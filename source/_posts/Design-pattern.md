---
title: Design_pattern
date: 2021-08-17 22:21:56
tags: [C++,Linux,Design_Pattern]
categories: Design_Pattern
---


<!-- more -->

### 面向对象设计原则：

1. 单一职责原则
2. 开闭原则
3. 里氏转换原则
4. 依赖倒转原则
5. 接口隔离原则
6. 合成复用原则
7. 迪米特法则

#### 单一职责原则：

- 一个对象应该只包含单一的职责，并且该职责被完整的封装在一个类中
- 就一个类而言，应该仅有一个引起它变化的原因

#### 开闭原则：

- 软件实体应对扩展开放，对修改关闭

#### 里氏转换原则：

- 所有引用基类的地方必须能透明的使用其子类的对象

#### 依赖倒转原则：

- 高层模块不应该依赖低层模块，它们都应该依赖抽象。抽象不应该依赖于细节，细节应该依赖于抽象。

#### 接口隔离原则：

- 客户端不应该依赖于那些它不需要的接口

#### 合成复用原则：

- 优先使用对象组合，而不是通过继承来达到复用的目的

#### 迪米特法则：

- 每一个软件单位对其他单位都只有最少的知识，而且局限于那些与本单位密切相关的软件单位



## 创建型模式

- 创建型模式关注对象的创建过程，描述如何将对象的创建和使用分离，让用户在使用过程中无需关心对象的创建细节，从而降低系统耦合度，让系统易于修改和扩展

### 简单工厂模式

#### 定义：

定义一个简单工厂类，它可以根据参数的不同返回不同类的实例，被创建的实例通常都具有共同的父类


