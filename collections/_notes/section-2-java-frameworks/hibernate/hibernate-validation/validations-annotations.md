---
layout: post
title: Validation annotations
permalink: /:collection/hibernate/validations/annotations
---

# Bean validation annotations

|ANNOTATION|	DESCRIPTION|
|---|---|	
|@Digits(integer=, fraction=)|	Checks whether the annotated value is a number having up to integer digits and fraction fractional digits.|
|@Email|	Checks whether the specified character sequence is a valid email address.|
|@Max(value=)|	Checks whether the annotated value is less than or equal to the specified maximum.|
|@Min(value=)|	Checks whether the annotated value is higher than or equal to the specified minimum|
|@NotBlank|	Checks that the annotated character sequence is not null and the trimmed length is greater than 0.|
|@NotEmpty|	Checks whether the annotated element is not null nor empty.|
|@Null|	Checks that the annotated value is null|
|@NotNull|	Checks that the annotated value is not null|
|@Pattern(regex=, flags=)|	Checks if the annotated string matches the regular expression regex considering the given flagmatch|
|@Size(min=, max=)|	Checks if the annotated element’s size is between min and max (inclusive)|
|@Negative|	Checks if the element is strictly negative. Zero values are considered invalid.|
|@NegativeOrZero|	Checks if the element is negative or zero.|
|@Future|	Checks whether the annotated date is in the future.|
|@FutureOrPresent|	Checks whether the annotated date is in the present or in the future.|
|@PastOrPresent|	Checks whether the annotated date is in the past or in the present.|

# Hibernate validator specific annotations

|ANNOTATION|	DESCRIPTION|
|---|---|	
|@CreditCardNumber( ignoreNonDigitCharacters=)|	Checks that the annotated character sequence passes the Luhn checksum test. Note, this validation aims to check for user mistakes, not credit card validity!|
|@Currency(value=)|	Checks that the currency unit of the annotated javax.money.MonetaryAmount is part of the specified currency units.|
|@EAN|	Checks that the annotated character sequence is a valid EAN barcode. The default is EAN-13.|
|@ISBN|	Checks that the annotated character sequence is a valid ISBN.|

|@Length(min=, max=)|	Validates that the annotated character sequence is between min and max included.|
|@Range(min=, max=)|	Checks whether the annotated value lies between (inclusive) the specified minimum and maximum.|
|@UniqueElements|	Checks that the annotated collection only contains unique elements.|
|@URL|	Checks if the annotated character sequence is a valid URL according to RFC2396.|

```java
public class User {
 
    @NotNull(message = "Please enter id")
    private Long id;
 
    @Size(max = 20, min = 3, message = "{user.name.invalid}")
    @NotEmpty(message = "Please enter name")
    private String name;
 
    @Email(message = "{user.email.invalid}")
    @NotEmpty(message = "Please enter email")
    private String email;
 
    public User(Long id, String name, String email) {
        super();
        this.id = id;
        this.name = name;
        this.email = email;
    }
 
    //Getters and Setters
 
    @Override
    public String toString() {
        return "User [id=" + id + ", name=" + name + ", email=" + email + "]";
    }
}
```
```java
public class TestHibernateValidator{
    @Inject
    @HibernateValidator
    private static ValidatorFactory validatorFactory;
    @Inject
    @HibernateValidator
    private static Validator validator;
     
    public static void main(String[] args)    {
        //Create ValidatorFactory which returns validator
        validatorFactory = Validation.buildDefaultValidatorFactory();
         
        //It validates bean instances
        validator = validatorFactory.getValidator();
 
        User user = new User(null, "1", "abcgmail.com");
 
        //Validate bean
        Set<ConstraintViolation<User>> constraintViolations = validator.validate(user);
 
        //Show errors
        if (constraintViolations.size() > 0) {
            for (ConstraintViolation<User> violation : constraintViolations) {
                System.out.println(violation.getMessage());
            }
        } else {
            System.out.println("Valid Object");
        }
    }
}

//Output: 
'1' is an invalid name. It must be minimum 3 chars and maximum 20 chars.
Invalid Email
```
```java
// ValidationMessages.properties
user.name.invalid='${validatedValue}' is an invalid name. It must be minimum {min} chars and maximum {max} chars.
user.email.invalid=Invalid Email
```
