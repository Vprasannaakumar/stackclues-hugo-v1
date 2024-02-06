+++
title = 'My Fifth Post My Fifth Post My Fifth Post '
date = 2023-11-22T16:55:24+01:00
draft = false
description = "This is a description"
image = "/images/5s.webp"
imageBig = "/images/5b.webp"
categories = ["general", "life", "coding"]
authors = ["Lama Dev"]
avatar = "/images/avatar.webp"
+++

Test Content
# JPA

### What is mapped by in JPA?

The `comments` `@OneToMany` association is marked with the `mappedBy` attribute which indicates that the `@ManyToOne` side is responsible for handling this bidirectional association.

owner --&gt; blogs [ one-to-many ]

Blog Entity

```java
@ManyToOne(cascade = CascadeType.ALL)
    @JoinColumn(name = "owner_id")
    private Owner owner;
```

Owner Entity

```java
@OneToMany(fetch = FetchType.LAZY, mappedBy = "owner", cascade = CascadeType.ALL)
    private List<Blog> blogList;
```
![](images/RzLktMO0Momp6IX438GN_md1gF7_cBKbHOOVmXpZgkM=.png)

![](images/v7c4CfANNa1XSAJMajreu_Qf7LkNpvRXPG0FQJpm70g=.png)

#### Bidirectional relationship  one-to-many

```java
@Entity
public class Department {
    @OneToMany(mappedBy = "department")
    private List<Employee> employees;
}
 
@Entity
public class Employee {
    @ManyToOne
    @JoinColumn(name = "department_id")
    private Department department;
}

```



#### UniDirectional relationship  one-to-many

```java
@Entity
public class Department {
    @Id
    private Long id;
 
    @OneToMany
    @JoinColumn(name = "department_id")
    private List<Employee> employees;
}

@Entity
public class Employee {
    @Id
    private Long id;
}

```