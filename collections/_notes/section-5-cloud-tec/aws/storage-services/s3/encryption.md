---
layout: post
title: S3 Encryption
permalink: /:collection/aws/s3/encryption
---

- TOC
{:toc}

<hr><br>

# Types of Encryption
- Encryption In Transit
    - SSL/TLS ie. https
    - For data you are transferring to and from your bucket
- Encryption At Rest - Server Side Encryption
    - S3 Managed Keys - ***SSE-S3***
        - AES-256, Advanced encryption standard 256 bits
        - Each object encrypted with its own key using strong multifactor encryption
        - Additional Step - Also encrypt the key with master key, AWS manages and rotates the keys for you.
    - AWS Key Management Service, Managed Keys, ***SSE-KMS***
        - AWS managed keys with additional benefits.
        - You get a Separate permission for use of an additional key called **Envelope Key**.
        - Envelope Key encrypts yours data's encryption key.
        - You also get an audit trail for the use  of your encryption keys, so you can see who used it and why.
    - Server Side Encryption with customer provided keys - ***SSE-C***
        - AWS manages encryption and decryption but you manage your own keys.
        - You are incharge of rotating those keys and lifecycle of those keys.
- Client Side Encryption
    - You encrypt the files yourself before uploading to S3.

# Enforcing Encryption on S3 Buckets

- Everytime a file is uploaded to S3, a PUT request is initiated.

![encrypt-s3]({{site.cdn}}/aws/s3/encrypt-s3.png)

- PUT /filename HTTP/1.1
- HOst bucket dns
- Authorization
- x-amz-meta-author: Faye
- Expect: 100-continue 
    - Tells S3 not to send your RequestBody until recieves an acknowledgement.
    - S3 can reject your request based on the contents of your header.
- If file is to be encrypted at upload time, header will have x-amz-server-side-encryption parameter.
    - x-amz-server-side-encryption: AES256 (SSE-S3 - S3 managed keys)
    - x-amz-server-side-encryption: ams:kms (SSE-KMS - KMS managed keys)
    - Can enforce use of SSE by using bucket policy which denies any s3 PUT request which doesn't include header param `x-amz-server-side-encryption`

# HTTP 100 Continue
> Read more about [100 Continue](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/100)
- Informational status response code indicates that everything so far is OK and that the client should continue with the request or ignore it if it is already finished.
- To have a server check the request's headers, a client must send Expect: 100-continue as a header in its initial request and receive a 100 Continue status code in response before sending the body.

![encrypt-s3-policy]({{site.cdn}}/aws/s3/encrypt-s3-policy.png)

![encrypt-s3-policy-json]({{site.cdn}}/aws/s3/encrypt-s3-policy-json.png)

* Here add "/*" for Resource if error shows up "Action does not apply to any resource in statement"
