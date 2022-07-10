---
layout: post
title: Convert list to map
categories: [content, java]
---

Hello, sometimes you nedd to parse some list to map. In java you can use stream api for this:



{% highlight c %}
package pl.marczak;

import com.github.javafaker.Faker;
import java.util.ArrayList;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

public class Main {

public static void main(String[] args) {
var faker = new Faker();
var users = new ArrayList<User>();

    for (int i = 0; i < 100; i++) {
      users.add(
          new User(
              faker.name().firstName(),
              faker.name().lastName(),
              faker.number().numberBetween(1, 100)));
    }

    Map<Integer, List<User>> result = users.stream().collect(Collectors.groupingBy(User::age));
}

record User(String name, String lastName, Integer age) {}
}

{% endhighlight %}

