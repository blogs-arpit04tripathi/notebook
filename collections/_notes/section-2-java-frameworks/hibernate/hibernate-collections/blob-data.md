---
layout: post
title: Blob
permalink: /:collection/hibernate/blob-data
---

```java
@Entity
@Table(name = "TBL_IMAGES")
public class ImageWrapper implements Serializable {
     
    private static final long serialVersionUID = 1L;
 
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "ID", unique = true, nullable = false)
    private Integer id;
     
    @Column(name = "IMAGE_NAME", unique = false, nullable = false, length = 100)
    private String imageName;
     
    @Column(name = "DATA", unique = false, nullable = false, length = 100000)
    private byte[] data;
     
    //Getters and Setters
}
```

**Inserting blob data into database**
```java
Session session = HibernateUtil.getSessionFactory().openSession();
session.beginTransaction();
File file = new File("C:\test.png");
byte[] imageData = new byte[(int) file.length()];
try {
    FileInputStream fileInputStream = new FileInputStream(file);
    fileInputStream.read(imageData);
    fileInputStream.close();
} catch (Exception e) {
    e.printStackTrace();
}
ImageWrapper image = new ImageWrapper();
image.setImageName("test.jpeg");
image.setData(imageData);
session.save(image);    //Save the data
session.getTransaction().commit();
HibernateUtil.shutdown();
```

**Reading the blob data from database**
```java
Session session = HibernateUtil.getSessionFactory().openSession();
session.beginTransaction();
ImageWrapper imgNew = (ImageWrapper)session.get(ImageWrapper.class, 1);
byte[] bAvatar = imgNew.getData();
try{
    FileOutputStream fos = new FileOutputStream("C:\temp\test.png");
    fos.write(bAvatar);
    fos.close();
}catch(Exception e){
    e.printStackTrace();
}
session.getTransaction().commit();
HibernateUtil.shutdown();
```
