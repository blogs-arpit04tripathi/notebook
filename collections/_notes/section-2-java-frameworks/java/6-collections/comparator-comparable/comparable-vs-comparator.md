---
layout: post
title: Comparable vs Comparator
permalink: /:collection/java/collections/comparable-vs-comparator
---


|Comparable|Comparator|
|---|---|
|natural ordering|Custom ordering|
|Only one sort sequence|Many sort sequences can be created on attribute. (Collections.sort())|
|compareTo(Object o)|compare (Object o1, Object o2)|
|	|public boolean equals(Object obj)|
|	|sgn(comp1.compare(o1, o2))==sgn(comp2.compare(o1, o2))|
|java.lang|java.util package|
|Need to Modify Classes – Must have source Code|No need to Modify Classes – Third Party cases|

```java
//If this.id < country.id: return -1
//If this.id > country.id: return 1
//If this.id ==country.id: return 0
public class Country implements Comparable<Country>{
    int id;
    String countryName;
    @Override
    public int compareTo(Country country) {
        return (this.id < country.id) ? -1 : (this.id > country.id ? 1 : 0) ;
    }
}
Collections.sort(listOfCountries);
```
```java
//If country1.id < country2.id: return -1
//If country1.id > country2.id: return 1
//If country1.id ==country2.id: return 0
public class CountryIdComparator implements Comparator<Country>{
   @Override
   public int compare(Country c1, Country c2) {
     return (c1.getCountryId() < c2.getCountryId()) ? -1 : (c1.getCountryId() > c2.getCountryId() ? 1 : 0) ;
    }
}
Collections.sort(listOfCountries , comparatorById);
Collections.sort(listOfCountries , comparatorByName);
```
