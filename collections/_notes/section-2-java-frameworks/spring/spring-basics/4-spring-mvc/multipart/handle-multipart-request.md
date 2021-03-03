---
layout: post
title: Handle multipart request
permalink: /:collection/spring/mvc/multipart/handle-request
---

- TOC
{:toc}

<hr><br>

# Handling multipart requests

Annotate a controller method parameter with @RequestPart.

You’ve added a new `<input>` field whose type is file. This lets the user select an image file to upload. The accept attribute is set to limit file types to JPEG, PNG, and GIF images. And according to its name attribute, the image data will be sent in the multipart request in the profile Picture part. Now you just need to change the processRegistration() method to accept the uploaded image. One way to do that is to add a byte array parameter that’s annotated with @RequestPart.

```java
@RequestMapping(value="/register", method=POST)
public String processRegistration(
    @RequestPart("profilePicture") byte[] profilePicture,
    @Valid Spitter spitter,
    Errors errors
  ) {
      ...
}
```
When the registration form is submitted, the profilePicture attribute is given an array of byte containing the data from the request part (as specified by @RequestPart). If the user submits the form without selecting a file, then the array will be empty (but not null). With the image data in hand, all that’s left is for processRegistration() to save the file somewhere.

## Receiving a MultipartFile

```java
public interface MultipartFile {
    String getName();
    String getOriginalFilename();
    String getContentType();
    boolean isEmpty();
    long getSize();
    byte[] getBytes() throws IOException;
    InputStream getInputStream() throws IOException;
    void transferTo(File dest) throws IOException;
}
```
MultipartFile offers a convenient transferTo() method to help you write the uploaded file to the filesystem. For example, you could add the following lines to processRegistration() to write the uploaded image file to the filesystem:
```java
profilePicture.transferTo(new File("/data/spittr/" + profilePicture.getOriginalFilename()));
```
Saving a file to the local filesystem like this is simple enough, but it leaves the management of the file up to you. You’re responsible for ensuring that there’s plenty of space. It’s up to you to make sure the file is backed up in case of a hardware failure. And it’s your job to deal with synchronizing the image files across multiple servers in a cluster.

## Saving Files To Amazon S3
```java
private void saveImage(MultipartFile image) throws ImageUploadException {
  try {
    AWSCredentials awsCredentials = new AWSCredentials(s3AccessKey, s2SecretKey);
    S3Service s3 = new RestS3Service(awsCredentials);
    S3Bucket bucket = s3.getBucket("spittrImages");
    S3Object imageObject = new S3Object(image.getOriginalFilename());
    imageObject.setDataInputStream(image.getInputStream());
    imageObject.setContentLength(image.getSize());
    imageObject.setContentType(image.getContentType());
    AccessControlList acl = new AccessControlList();
    acl.setOwner(bucket.getOwner());
    acl.grantPermission(GroupGrantee.ALL_USERS, Permission.PERMISSION_READ);
    imageObject.setAcl(acl);
    s3.putObject(bucket, imageObject);
  } catch (Exception e) {
    throw new ImageUploadException("Unable to save image", e);
  }
}
```
The first thing that saveImage() does is set up Amazon Web Service (AWS) credentials. For this, you’ll need an S3 access key and an S3 secret access key. These will be given to you by Amazon when you sign up for S3 service. They’re provided to SpitterController via value injection. With the AWS credentials in hand, saveImage() creates an instance of JetS3t’s RestS3Service, through which it operates on the S3 filesystem. It gets a reference to the spitterImages bucket, creates an S3Object to contain the image, and then fills that S3Object with image data.

Just before calling the putObject() method to write the image data to S3, saveImage() sets the permissions on the S3Object to allow all users to view it. This is important—without it, the images wouldn’t be visible to your application’s users. Finally, if anything goes wrong, an ImageUploadException will be thrown.

## Receiving the Uploaded File as a Part

If you’re deploying your application to a Servlet 3.0 container, you have an alternative to MultipartFile. Spring MVC will also accept a javax.servlet.http.Part as a controller method parameter. Using Part instead of MultipartFile leaves the processRegistration() method signature looking like this:
```java
@RequestMapping(value="/register", method=POST)
public String processRegistration(
@RequestPart("profilePicture") Part profilePicture, @Valid Spitter spitter, Errors errors) {
  ...
}
```
```java

public interface Part {
  public InputStream getInputStream() throws IOException;
  public String getContentType();
  public String getName();
  public String getSubmittedFileName();
  public long getSize();
  public void write(String fileName) throws IOException;
  public void delete() throws IOException;
  public String getHeader(String name);
  public Collection<String> getHeaders(String name);
  public Collection<String> getHeaderNames();
}

profilePicture.write("/data/spittr/" + profilePicture.getOriginalFilename());
```
It’s worth noting that if you write your controller handler methods to accept file uploads via a Part parameter, then you don’t need to configure the StandardServletMultipartResolver bean. StandardServletMultipartResolver is required only when you’re working with MultipartFile.
