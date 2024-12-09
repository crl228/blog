---
title: 'Java 中 Optional 的使用'
description: 'Java 中 Optional 的使用'
pubDate: 2018-03-30 16:51:49
---

> 升级 SpringBoot2 之后 SpringData 也一并升级到了 2.0.5，之前的 CrudRepository 提供的默认实现很多都采用了 Optional 的方式，致使之前业务代码中的 null 处理显得很尴尬，在迁移过程中记录整理下 Optional 的一些使用。

NPE 作为 Java 中最著名的梗已无需多言，Java8 之后提供了 Optional 的方式来对其进行处理，毕竟 Java 作为一个大龄语言，没有 Elvis 之类的特殊语法或运算符来处理 null 这种类型（结果），加入 Optional 这种语法糖也算是一点点进步。

以实际中 SpringData 的一些操作为例

```java
//传统方式
User user = userRepository.findById(1L);
if (user == null) {
    throw new Exception("user not exists");
}
//伪优化
Optional<User> optional = userRepository.findById(1L);
if (!optional.isPresent()) {
    throw new Exception("user not exists");
}
//优雅一点的方式（已抛出业务异常为例）
User user = userRepository.findById(1L).orElseThrow(() -> new Exception("User not exists"));
```

在获取对象内容时减少形如`if(user != null)`这样的判断

```java
private String getName(User user) {
    return Optional.ofNullable(user).map(u -> u.getNickname()).orElse("默认昵称");
}
```
