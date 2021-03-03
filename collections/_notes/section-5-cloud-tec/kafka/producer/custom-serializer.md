---
layout: post
title: Custom Serializers
permalink: /:collection/kafka/serializer/custom
---

-	props.put("value.serializer", "SupplierSerializer");
-	**Generic serializers**: avro or protocol-buffer

```java
import org.apache.kafka.common.serialization.Serializer;
import org.apache.kafka.common.errors.SerializationException;
import java.io.UnsupportedEncodingException;
import java.util.Map;
import java.nio.ByteBuffer;

public class SupplierSerializer implements Serializer < Supplier > {
    private String encoding = "UTF8";

    @Override
    public void configure(Map < String, ? > configs, boolean isKey) {
        // nothing to configure
    }

    @Override
    public byte[] serialize(String topic, Supplier data) {

        int sizeOfName;
        int sizeOfDate;
        byte[] serializedName;
        byte[] serializedDate;
        try {
            if (data == null)
                return null;
            serializedName = data.getName().getBytes(encoding);
            sizeOfName = serializedName.length;
            serializedDate = data.getStartDate().toString().getBytes(encoding);
            sizeOfDate = serializedDate.length;

            ByteBuffer buf = ByteBuffer.allocate(4 + 4 + sizeOfName + 4 + sizeOfDate);
            buf.putInt(data.getID());
            buf.putInt(sizeOfName);
            buf.put(serializedName);
            buf.putInt(sizeOfDate);
            buf.put(serializedDate);
            return buf.array();
        } catch (Exception e) {
            throw new SerializationException("Error when serializing Supplier to byte[]");
        }
    }

    @Override
    public void close() {
        // nothing to do
    }
}
```

```java
import java.nio.ByteBuffer;
import java.util.Date;
import java.text.DateFormat;
import java.text.SimpleDateFormat;
import org.apache.kafka.common.errors.SerializationException;
import org.apache.kafka.common.serialization.Deserializer;
import java.io.UnsupportedEncodingException;
import java.util.Map;

public class SupplierDeserializer implements Deserializer < Supplier > {
    private String encoding = "UTF8";

    @Override
    public void configure(Map < String, ? > configs, boolean isKey) {
        //Nothing to configure
    }

    @Override
    public Supplier deserialize(String topic, byte[] data) {
        try {
            if (data == null) {
                System.out.println("Null recieved at deserialize");
                return null;
            }
            ByteBuffer buf = ByteBuffer.wrap(data);
            int id = buf.getInt();
            int sizeOfName = buf.getInt();
            byte[] nameBytes = new byte[sizeOfName];
            buf.get(nameBytes);
            String deserializedName = new String(nameBytes, encoding);
            int sizeOfDate = buf.getInt();
            byte[] dateBytes = new byte[sizeOfDate];
            buf.get(dateBytes);
            String dateString = new String(dateBytes, encoding);
            DateFormat df = new SimpleDateFormat("EEE MMM dd HH:mm:ss Z yyyy");
            return new Supplier(id, deserializedName, df.parse(dateString));
        } catch (Exception e) {
            throw new SerializationException("Error when deserializing byte[] to Supplier");
        }
    }

    @Override
    public void close() {
        // nothing to do
    }
}
```
