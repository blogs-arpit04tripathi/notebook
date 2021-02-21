---
layout: post
title: Comparator
permalink: /:collection/java/collections/comparator
---


* TreeSet, TreeMap store elements in sorted order.
* Custom definition of “sorted order” when natural-sorting is not desirable.
* interface Comparator<T>

## List of Methods : Comparator

|Methods||
|---|---|
|int compare(T obj1, T obj2) | obj1 - obj2|
|boolean equals(object obj)||
|default Comparator<T> reversed( )||
|default Comparator<T> thenComparing(Comparator<? super T> thenByComp) | cascade compare by X then by Y sequence.|
|static <T extends Comparable <? super T>> Comparator<T> reverseOrder( )||
|static <T extends Comparable <? super T>> Comparator<T> naturalOrder( )||
|static <T> Comparator <T> nullsFirst(Comparator<? super T> comp)||
|static <T> Comparator<T> nullsLast(Comparator<? super T> comp)||

```java
class MyComp implements Comparator<String> {
  public int compare(String aStr, String bStr){
    return bStr.compareTo(aStr);                            // Reverse the comparison.
  }
}
MyComp mc = new MyComp();
TreeSet<String> ts = new TreeSet<String>(mc.reversed());    // reverse order of MyComp

// Comparator by Lambda
Comparator<String> mc = (aStr, bStr) -> bStr.compareTo(aStr);
Comparator<Person> c = Comparator.comparingInt(Person::getAge);

// Cascaded Comparator
Comparator<Person> multiComparator = Comparator.comparing(Person::getFirstName);
multiComparator = multiComparator.thenComparing(Comparator.comparing(Person::getLastName));
Collections.sort(persons, multiComparator);

CompLastNames compLN = new CompLastNames();
Comparator<String> compLastThenFirst = compLN.thenComparing (new CompThenByFirstName());
TreeMap<String, Double> tm = new TreeMap<String, Double>(compLastThenFirst);

Collections.sort(reportList, Comparator.comparing(Report::getReportKey).thenComparing(Report::getStudentNumber).thenComparing(Report::getSchool));
```
