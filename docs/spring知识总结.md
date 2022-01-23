<center><h1>spring知识总结</h1></center>

## 1，认识Spring（了解）

### 1，Spring的简单概述
Spring在英文里面本来的含义是春天的意思。Spring框架用Spring命名也是非常非常贴切的。它为我们软件开发也带来了春天。

在老师看来Spring是Java领域最成功的的框架。在企业实际应用中。基本上所有的项目都会使用到Spring。Spring之所以成功，来自原它的理念，它最核心的概念就是Ioc(控制翻转)和Aop(面向切面编程)，其中Ioc是Spring的基础，而Aop是最重要的功能。并且Spring还能整合开源社区几乎所有的第三方框架和类库。所以，我们一定要学习它。

老师工作这么多年，我看到的框架也是很多了，比如之前的strtus2，hibernate等等一些框架，肯能会火一段时间，然后就慢慢的消亡了。但是我们的Spring从推出开始，一直到今天，越来越好。所以说它真的是非常重要。面试的时候，大篇幅的问题你。
### 2，Spring的发展历史
1997年IBM提出了EJB的思想
1998年SUN制定开发标准规范EJB1.0
1999年，EJB1.1 发布
2001年，EJB2.0 发布
2003年，EJB2.1 发布
2006年，EJB3.0 发布
Rod Johnson（spring作者）
Expert One-to-One J2EE Design and Development(2002)
阐述了 J2EE 使用 EJB 开发设计的优点及解决方案
Expert One-to-One J2EE Development without EJB(2004)
阐述了 J2EE 开发不使用 EJB 的解决方式（Spring 雏形）
目前Spring的版本的5.x

### 3，学习和使用Spring的好处
学习Spring的好处那简直是太多了。老师给大家归纳了几点如下：

#### 方便解耦，简化开发

通过Spring提供的IoC容器，可以将对象间的依赖关系交由Spring进行控制，避免硬编码所造成的过度程序耦合。用户也不必再为单例模式类、属性文件解析等这些很底层的需求编写代码，可以更专注于上层的应用。

#### AOP 编程的支持

通过Spring的AOP功能，方便进行面向切面的编程，许多不容易用传统OOP（面向对象）实现的功能可以通过AOP轻松应付。

#### 声明式事务的支持

可以将我们从单调烦闷的事务管理代码中解脱出来，通过声明式方式灵活的进行事务的管理，提高开发效率和质量。

#### 方便程序的测试

可以用非容器依赖的编程方式进行几乎所有的测试工作，测试不再是昂贵的操作，而是随手可做的事情。

#### 方便集成各种优秀框架

Spring可以降低各种框架的使用难度，提供了对各种优秀框架（Struts、Hibernate、Hessian、Quartz、mybatis等）的直接支持。

#### 降低 JavaEE API 的使用难度

Spring对JavaEE API（如JDBC、JavaMail、远程调用等）进行了封装，使这些 API 的使用难度大为降低。

#### Java 源码是经典学习范例

Spring 的源代码设计精妙、结构清晰、匠心独用，处处体现着大师对Java设计模式灵活运用以及对 Java 技术的高深造诣。它的源代码无意是 Java 技术的最佳实践的范例。以后高级课程，我们会专门有节课就是分析Spring源码。

## 2，Spring IOC的概念

### 1，IOC思想：
我们Java是一个面向对象的语言。我们在开发的时候肯定要使用到大量的对象。我们使用的怎么对象是怎么来的？按照我们以前的知识，我们可能会通过调用构造器来创建一个。也有可能是我们通过写一个单例方法然后来获取到的。还有可能是我们自己反射出来的。但是Spring就提供了另外一种获取对象的更好的方案，就是IOC（控制反转）

#### 原始方式创建对象类比：

老师用吃饭来举例。同学们肚子饿了，想要吃饭。像老师小时候是和我的外婆外公在农村生活。当时村里也没有什么饭店之类的。老师肚子饿了，外婆要给我做饭会怎么做？首先，家里面得有锅，碗，瓢，铲子等基本的工具。然后还要有盐，有肉，有蔬菜，有米饭等食材。然后还要有柴火用来生活。然后外婆还需要控制好炒菜的时候放多少油，放多少盐，放多少菜，放多少肉，放多少水。然后最终加工出一桌饭菜出来。这个过程我们可以看如下流程图：

![img](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210529180926375.png)

我们可以看出来，整个流程，我们要吃饭，我们是主动去做饭。这个和我们以前编写代码的时候要使用某个类一样的。我们需要使用某个类了，我们会主动去创建一个类。如果这个类的构造方法需要各种参数，那么我们还需要提前准备好各种参数。对于我们来说就无形的增加了很多工作量。

#### IOC创建对象方式类比

IOC的思想，我们还是用吃饭来举例。到了后来，老师参加工作了，来到了城市。老师就比较懒了。不喜欢自己做饭。这个时候在饿了吗，美团上面有大量的外卖店，老师要吃饭只需要做这样一个事情，我只需要在手机上选择我想要吃哪些饭菜就行了。至于哪些餐饮商店到底是怎么做的，每道菜用了多少的油，多少的盐，用多大的火，我一概不用关心，我只需要告诉餐饮店我需要什么菜就行。这个方式的流程图如下：

![img](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210529181059999.png)

#### 总结：
通过上面的两个例子的讲解。同学们应该IOC有一个初步的认识。我们在Spring中就是通过IOC容器来帮助我们实现控制反转的。而实现IOC的方式用的就是依赖注入（Dependency Injection）DI。这个就好比前面的例子，我们下单之后，食材去哪里采购，制作的时候需要如何控制调味，放多少油，用什么打包盒，一切的一切我们都不需要去操心，这些事情就是别人给我们已经做好了，我们只需要下单就可以吃饭。

### 2，引出Spring IOC容器：
我们通过上面的介绍已经对控制翻转有了一个初步的认识。但是接下来我们再深入的讨论一下其中的问题。

就比如，我们点外卖，商家为我们做饭菜。做饭菜的时候需要米，肉，菜，做好了之后还需要包装盒。对于这些食材和包装盒，商家也不需要太过于关心肉是怎么来，米是谁种出来等等。商家只需要有钱向猪肉采购商和大米采购商等采购就行了。

那么我们可以看出，我么要吃这顿饭，老师是依赖于外卖平台，外卖平台依赖于餐饮店，餐饮店有依赖于各种采购商，各种采购商可能又会依赖于农民。我们在软件开发的时候也会有同样的问题，我们 要创建一个对象，这个对象依赖于其他对象，其他对象又依赖其他对象。

Spring里面就可以解决这种以来链的问题。Spring给我们提供一个东西叫做IOC容器，IOC容器就管理着各种资源。我们要以来的对象让Spring给我们创建好，然后存放在IOC容器中，我们需要使用的时候，直接去Spring容器中获取就好了。至于IOC原理是怎么回事，我们之后会讲。

## 3，spring IOC入门

### 1，导入Jar包：
Spring是Spring社区为我们提供的第三方的开源框架。我们首先来介绍一下Spring的三大核心组件：

Spring core: Spring核心中的核心，为context在管理Spring中bean(就是我们的对象)与bean之间关系时为其服务的。其实直白一点就是为Spring管理bean提交工具的一个工具类。
Spring beans: 主要负责Bean的创建，Bean的定义，Bean的解析。该组件依赖于Spring core
Spring context:在Spring中的context包下，为Spring提供运行环境，用以保存各个对象状态。该组件依赖于spring beans。
通过上面我们可以看出，我们开发的时候只要引入了spring-context就好了。

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.3.5</version>
</dependency>
```

### 2，什么是注入

在spring中这个注入，老师自己总结了一下用大白话来理解，就是其实就是创建对象，并且提交给Spring容器，让Spring容器管理器来。

### 3，依赖注入快速入门案例

#### 1，定义一个类：

```java
package com.vgxit.spring.ktdm.vgioc.beans;
public class Person {
    public void sayHello(String name) {
        System.out.println("Hello " + name);
    }
}
```

#### 2，创建Spring的配置文件，名字可以随便去，我们定义为spring-ioc-cfg.xml:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!--存放bean的容器-->
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
    <!--
    bean标签用来定义一个需要Spring创建并且注入到IOC容器的对象
    id表示这个对象的名字
    class表示类型
    -->
    <bean id="person" class="com.vgxit.spring.ktdm.vgioc.beans.Person"></bean>
</beans>
```

#### 3，通过Spring容器来获取对应的对象，然后执行方法。

```java
package com.vgxit.spring.ktdm.vgioc.test;
 
import com.vgxit.spring.ktdm.vgioc.beans.Person;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
 
public class Ioc001Test {
    public static void main(String[] args) {
        //1,首先通过配置文件获取到Spring的上下文
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-ioc-cfg.xml");
        //2,获取对应的对象,通知Spring的Ioc容器，我需要一个名字叫做Person的bean
        Person person = (Person) ctx.getBean("person");
        //调用方法
        person.sayHello("李一桐");
    }
}
```

## 4，spring 构造方法注入和set注入

### 1，概述
我们上节课讲了一下IOC入门，然后我们注入了一个对象到Spring容器，并且通过Spring容器获取到了这个对象。但是，我们思考一下，我们说道了注入就是我们创建一个对象然后把这个对象提交到Spring容器。那么我们思考一下他是如何创建这个对象的呢？

### 2，无参构造方法注入
所谓无参构造方法注入就是Spring会自动调用我们无参构造方法来创建一个对象，然后再把这个对象提交到Spring容器。像我们上节课讲的入门案例。我们创建Person对象不需要提交任何的参数。

### 3，有参构造方法注入
对于有一些对象，他有一些属性，这些属性的初始化是通过构造方法传递进去的。这个时候，我们创建对象的时候必须要指定对应的参数。Spring也给我们提供了通过构造器传入参数注入对象的方法。

#### 1，改造一下Person:

```java
package com.vgxit.spring.ktdm.vgioc.beans;
 
import lombok.AllArgsConstructor;
 
@AllArgsConstructor
public class Person {
    private Integer id;
    private String name;
    public void sayHello(String name) {
        System.out.println(this.id + ":" + this.name + " say hello to " + name);
    }
}
```

#### 2，修改注入配置：

```xml
<!--
    bean标签用来定义一个需要Spring创建并且注入到IOC容器的对象
    id表示这个对象的名字
    class表示类型
    -->
<bean id="person" class="com.vgxit.spring.ktdm.vgioc.beans.Person">
    <!--
        <constructor-arg/>标签就表示对应的构造方法的参数
        index表示参数的位置，从0开始的
        value表示参数的值
        -->
    <constructor-arg index="0" value="1"/>
    <constructor-arg index="1" value="V哥"/>
</bean>
```

#### 3，测试：

```java
package com.vgxit.spring.ktdm.vgioc.test;
 
import com.vgxit.spring.ktdm.vgioc.beans.Person;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
 
public class Ioc001Test {
    public static void main(String[] args) {
        //1,首先通过配置文件获取到Spring的上下文
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-ioc-cfg.xml");
        //2,获取对应的对象,通知Spring的Ioc容器，我需要一个名字叫做Person的bean
        Person person = (Person) ctx.getBean("person");
        //调用方法
        person.sayHello("李一桐");
    }
}
```

### 4，有参构造方法注入缺陷

我们上面讲了有参构造方法实现注入。但是我们在实际的开发中，基本上没人使用有参构造方法来实现注入。因为有参构造方法的注入是有非常大的缺陷的。下面我们演示一下这个缺陷。

#### 1，改造Person:

```java
package com.vgxit.spring.ktdm.vgioc.beans;
 
public class Person {
    private Integer id;
    private String name;
    private String nickName;
 
    public Person(String name, String nickName) {
        this.name = name;
        this.nickName = nickName;
    }
 
    public Person(Integer id, String name) {
        this.id = id;
        this.name = name;
    }
 
    public void sayHello(String name) {
        System.out.println(this.id + ":" + this.name + "[" + this.nickName + "]" + " say hello to " + name);
    }
}
```

这个时候，我们传入如下参数：

```xml
<bean id="person" class="com.vgxit.spring.ktdm.vgioc.beans.Person">
    <!--
        <constructor-arg/>标签就表示对应的构造方法的参数
        index表示参数的位置，从0开始的
        value表示参数的值
        -->
    <constructor-arg index="0" value="V哥"/>
    <constructor-arg index="1" value="V哥学IT"/>
</bean>
```

这个时候我们可以发现Spring调用了Person的Person(String name, String nickName)方法。但是，如果我们改成下面的参数传入：

```xml
<bean id="person" class="com.vgxit.spring.ktdm.vgioc.beans.Person">
    <!--
        <constructor-arg/>标签就表示对应的构造方法的参数
        index表示参数的位置，从0开始的
        value表示参数的值
        -->
    <constructor-arg index="0" value="1"/>
    <constructor-arg index="1" value="V哥学IT"/>
</bean>
```

这个时候，还是调用的Person(String name, String nickName)。但是我们实际上是想调用Person(Integer id, String name)。但是我们发现Spring永远没有办法帮我们调用到。因为Spring调用有参构造方法的逻辑按照构造方法定义的顺序，从上往下找到第一个满足参数个数匹配的方法来调用。

### 5，基于Setter的注入

setter注入是Spring中最流行的注入方式，它的原理是先调用无参构造方法来创建对象，然后调用对应的set方法来为属性赋值。用setter的方式可以解决有参构造方法注入的问题。并且可以提高可读性。

#### 1，改造Person:

```java
package com.vgxit.spring.ktdm.vgioc.beans;
 
import lombok.Setter;
 
@Setter
public class Person {
    private Integer id;
    private String name;
    private String nickName;
 
    public void sayHello(String name) {
        System.out.println(this.id + ":" + this.name + "[" + this.nickName + "]" + " say hello to " + name);
    }
}
```

#### 2，通过property标签来注入对应的属性：

```xml
<bean id="person" class="com.vgxit.spring.ktdm.vgioc.beans.Person">
    <property name="id" value="1"/>
    <property name="name" value="V哥"/>
    <property name="nickName" value="V哥学IT"/>
</bean>
```

## 5，Spring Xml装配Bean

### 1，概述
通过之前的学习，大家已经熟练的掌握了SpringIOC和理念，并且对Spring依赖注入的使用有一个初步的了解。这里我们再来深入的学习一下Bean的装配。在Spring中提供了三种方式来对Bean进行配置：

在XML文件中配置
在Java的接口和实现类中配置
隐式Bean的发现机制和自动装配原则
在现实的工作中，这三种方式都会被用到，并且在学习和工作中常常混合使用。所以我们这三种方式都要学习。本节课我们先学习XML装配Bean。

### 2，分析bean标签

```xml
<bean id="person" class="com.vgxit.spring.ktdm.vgioc.beans.Person">
    <property name="id" value="1"/>
    <property name="name" value="V哥"/>
    <property name="nickName" value="V哥学IT"/>
</bean>
```

1，bean标签有一个id属性，这个id属性就是为bean取一个全局唯一的名字。这个属性不是一个必须的属性，如果没有申明它，那么Spring会采用"全限定名#{number}"的方式来自动为我们生成一个编号，number从0开始计数。比如我们申明了两个Person对象，如下：

```xml
<bean class="com.vgxit.spring.ktdm.vgioc.beans.Person">
    <property name="id" value="1"/>
    <property name="name" value="V哥"/>
    <property name="nickName" value="V哥学IT"/>
</bean>
<bean class="com.vgxit.spring.ktdm.vgioc.beans.Person">
    <property name="id" value="2"/>
    <property name="name" value="李一桐"/>
    <property name="nickName" value="桐桐"/>
</bean>
```

这个时候，如果我们再用原来的方式获取Person对象就获取不到了，因为我们的id是Spring自动生成的，我们并没有指定。

```java
package com.vgxit.spring.ktdm.vgioc.test;
 
import com.vgxit.spring.ktdm.vgioc.beans.Person;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
 
public class Ioc001Test {
    public static void main(String[] args) {
        //1,首先通过配置文件获取到Spring的上下文
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-ioc-cfg.xml");
        //2,获取对应的对象
        Person person = (Person) ctx.getBean(Person.class.getName() + "#0");
        //调用方法
        person.sayHello("周杰伦");
    }
}
```

2，class就是我们要注入的对象的类型，这里填写一个类的全限定名

3，property元素定义类的属性，其中name表示属性名，value表示属性值

### 3，装配集合

我们之前讲了通过property标签的方式来实现注入。但是这个对于一些基本数据类型和String类型的注入还是比较方便的。但是如果我们的类型是集合类型（List, Set, Map, Properties）怎么办?

#### 1，接下来我们就定义一个新的类来做：

```java
package com.vgxit.spring.ktdm.vgioc.beans;
 
import lombok.Data;
 
import java.util.List;
import java.util.Map;
import java.util.Properties;
import java.util.Set;
 
@Data
public class Coder {
    private String name;
    private List<String> languages;
    private Set<String> friends;
    private Map<String, Integer> houses;
    private Properties properties;
}
```

#### 2，在spring的xml文件中，注入Coder:

```xml
<bean id="coder" class="com.vgxit.spring.ktdm.vgioc.beans.Coder">
    <property name="name" value="V哥"/>
    <property name="languages">
        <!--配置list集合-->
        <list>
            <value>java</value>
            <value>php</value>
            <value>sql</value>
            <value>shell</value>
            <value>javascript</value>
        </list>
    </property>
    <property name="friends">
        <!--配置set集合-->
        <set>
            <value>李一桐</value>
            <value>鞠婧祎</value>
            <value>郑爽</value>
            <value>迪丽热巴</value>
        </set>
    </property>
    <property name="houses">
        <!--配置map集合-->
        <map>
            <entry key="汤臣一品" value="30000000"/>
            <entry key="中国铁建" value="24000000"/>
        </map>
    </property>
    <property name="properties">
        <!--配置properties集合-->
        <props>
            <prop key="height">178</prop>
            <prop key="weight">140</prop>
            <prop key="age">18</prop>
        </props>
    </property>
</bean>
```

#### 3，调用测试：

```java
private static void testCoder() {
    //1,首先通过配置文件获取到Spring的上下文
    ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-ioc-cfg.xml");
    Coder coder = (Coder) ctx.getBean("coder");
    System.out.println(coder);
}
```

### 4，复杂Bean装配
上面我们讲了一下使用XML的方式如何装配集合。但是，我们想想如果我们的属性是一个复杂集合对象怎么办呢？比如，我们的属性是List或者Set，而这个List的泛型是一个对象。比如我们的Map，key和value都是一个对象怎么办？

解决思路，我们先把对应的bean注入好，然后在我们注入属性的时候引入过来就行。

#### 1，我们定义三个类，分别是用户，角色，还有一个是用户角色关联。

```java
@Data
public class User {
    private Integer id;
    private String name;
}
 
 
@Data
public class Role {
    private Integer id;
    private String name;
}
 
 
@Data
public class UserRole {
    private Integer id;
    private List<User> users;
    private Map<Role, User> map;
}
```

#### 2，注入的思路，首先我们先把依赖的对象给注入了，然后再来注入自己。

```xml
<bean id="user1" class="com.vgxit.spring.ktdm.vgioc.beans.User">
    <property name="id" value="1"/>
    <property name="name" value="V哥"/>
</bean>
<bean id="user2" class="com.vgxit.spring.ktdm.vgioc.beans.User">
    <property name="id" value="2"/>
    <property name="name" value="李一桐"/>
</bean>
<bean id="role1" class="com.vgxit.spring.ktdm.vgioc.beans.Role">
    <property name="id" value="1"/>
    <property name="name" value="超级管理员"/>
</bean>
<bean id="role2" class="com.vgxit.spring.ktdm.vgioc.beans.Role">
    <property name="id" value="2"/>
    <property name="name" value="普通用户"/>
</bean>
<bean id="userRole" class="com.vgxit.spring.ktdm.vgioc.beans.UserRole">
    <property name="id" value="1"/>
    <property name="users">
        <list>
            <ref bean="user1"/>
            <ref bean="user2"/>
        </list>
    </property>
    <property name="map">
        <map>
            <entry key-ref="role1" value-ref="user1"/>
            <entry key-ref="role2" value-ref="user2"/>
        </map>
    </property>
</bean>
```

#### 3，创建对象，打印效果：

```java
ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-ioc-cfg.xml");
Coder coder = (Coder) ctx.getBean("coder");
System.out.println(coder);
```

### 5，命名空间装配（了解）
命名空间装配在写法上比我们上面的控制器装配和setter装配要简单。但是这种写法可读性不好，基本上在工作中没人这么用。但是Spring的确是提供了这样的功能，这里老师也给大家介绍一下。

#### 1，使用构造方法装配
这里我们还是使用之前我们用过的Person类来做实验：

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class Person {
    private Integer id;
    private String name;
    private String nickName;
    public void sayHello(String name) {
        System.out.println(this.name + "[" + this.nickName + "] Hello " + name);
    }
}
```

然后，我们创建一个新的spring配置文件spring-namespace.xml引入通过构造方法以命名空间方式注入的XSD文件，然后注入：

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:c="http://www.springframework.org/schema/c"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean id="person" class="com.vgxit.learn.bean.bk.beans.Person" c:_0="1" c:_1="V哥" c:_2="V哥学IT"/>
</beans>
```

#### 2，使用setter方法装配

这里我们还是使用之前我们用过的Person类来做实验：

1，注入代码如下

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:c="http://www.springframework.org/schema/c"
       xmlns:p="http://www.springframework.org/schema/p"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean id="person2" class="com.vgxit.learn.bean.bk.beans.Person" p:id="1" p:name="李一桐" p:nickName="tongtong"/>
</beans>
```

#### 3，命名空间的方式注入复杂Bean

```java
package com.vgxit.learn.bean.bk.beans;
 
import lombok.Data;
import java.util.List;
import java.util.Map;
 
@Data
public class UserRole {
    private Integer id;
    //新加的
    private List<String> names;
    private List<User> users;
    private Map<Role, User> map;
}
```

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:c="http://www.springframework.org/schema/c"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:util="http://www.springframework.org/schema/util"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/util
       http://www.springframework.org/schema/util/spring-util.xsd">
<util:list id="names">
    <value>java</value>
    <value>php</value>
    <value>javascript</value>
    <value>golang</value>
</util:list>
<util:list id="users">
    <ref bean="user1"/>
    <ref bean="user2"/>
</util:list>
<util:map id="map">
    <entry key-ref="role1" value-ref="user1"/>
    <entry key-ref="role2" value-ref="user2"/>
</util:map>
<bean id="userRole" class="com.vgxit.learn.bean.bk.beans.UserRole" p:id="1" p:names-ref="names" p:users-ref="users" p:map-ref="map"/>
</beans>
```

## 6，Spring注解方式装配Bean

### 1，概述
通过之前的学习，我们己经知道如何使用XML的方式去装配Bean但是更多的时候我们已经不再推荐使用XML的方式去装配Bean(注意，XML装配Bean的知识你还是要会)，更多时候会考虑使用注解的方式去装配Bean。使用注解的方式可以减少XML的配置，并且注解功能更为强大，它既能实现XML的功能，也提供了自动装配的功能，采用了自动装配后，程序员所需要做的决断就少了，更加有利于对程序的开发，这就是“约定由于配置” 的开发原则。

在Spring中，提供了两种方式来发现Bean:

组件扫描：通过定义资源的方式，让Spring Ioc容器扫描对应的包，从而把Bean装配进来。
自动装配：通过定义注解，让一些依赖关系可以通过注解完成。
因为使用注解的方式来开发Spring应用已经是主流了，所以，我们后续的课程主要还是基于注解来讲解的。

### 2，使用@Component装配Bean:
#### 1，我们定义一个类，到时候使用这个类来装配bean:

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class Dog {
    @Value("1")
    private Integer id;
 
    @Value("丑丑")
    private String name;
 
    @Value("贵宾犬")
    private String breed;
}
```

#### 2，定义类之类：

```java
package com.vgxit.learn.spring.ktdm.vgannioc;
 
import org.springframework.context.annotation.ComponentScan;
 
@ComponentScan
public class VgAnnIocConfig {
}
```

#### 3，测试代码：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.test;
 
import com.vgxit.learn.spring.ktdm.vgannioc.VgAnnIocConfig;
import com.vgxit.learn.spring.ktdm.vgannioc.beans.Dog;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
 
public class VganniocTest01 {
    public static void main(String[] args) {
        //获取Spring的上下文
        ApplicationContext ctx = new AnnotationConfigApplicationContext(VgAnnIocConfig.class);
        Dog dog = (Dog) ctx.getBean("dog");
        System.out.println(dog);
    }
}
```

代码分析：

1，@Component注解代表Spring会把这个注解修饰的类扫描成bean。这个注解的value属性就相当于我们在XML中配置的bean的id。我们在开发的时候也可以不用指定value属性，在不指定的时候，spring会自动给我们生成一个id，这个id就是我们的类名首字母小写。

2，注解@Value代表的是值的注入，这里我们只是简单的注入了一些值。这个地方id是int类型。这个时候我们不用操心，Spring会自己知道帮我们转换的

3，我们定义了一个类VgAnnIocConfig。这个类就相当于我们之前用过得xml的配置文件，我们就可以理解成它就是Spring的一个配置类。这个类里面使用了一个注解@ComponentScan，这个注解代表的就是扫描当前包和子包。

4，使用了注解的方式注入bean之后，我们开发的时候的上下文用AnnotationConfigApplicationContext

### 3，自定义扫描包
按照之前讲的方式，我们定义的扫描配置只能扫描配置类对应的包和子包。但是在真实的开发中，我们更多的情况是需要自定义要扫描的包的路径，这个时候如何解决呢？

@ComponentScan有一个属性叫做basePackages，这个属性是一个数组，这个数组里面存放的就是我们要扫描的包的路劲。只要你配置了这个属性了，Spring会自动的扫描你配置的包和下面的子包。4

### 4，自定义扫描类

就是我们还可以通过指定对应的类的方式来进行扫描，如果我们指定了对应的类，那么Spring会扫描对应的类所在包下面的所有类。

```java
@ComponentScan(basePackageClasses = Cat.class)
public class VgAnnIocConfig {
}
```

### 5，按类型获取Bean

按照之前我们的学习，我们获取对应的bean是通过id来获取的。其实Spring还给我们提供了通过类型获取Bean的方式。

```java
public class VganniocTest01 {
    public static void main(String[] args) {
        //获取Spring的上下文
        ApplicationContext ctx = new AnnotationConfigApplicationContext(VgAnnIocConfig.class);
        //在ioc容器中找到对应的类型的bean，然后返回
        Dog dog = ctx.getBean(Dog.class);
        Cat cat = ctx.getBean(Cat.class);
        System.out.println(dog);
        System.out.println(cat);
    }
}
```

### 6，自动装配

我们上面给大家介绍的Dog，Cat这些类的属性，要不是int，要不就是String。反正都是一些简单数据类型，但是如果有一个类是复杂数据类型的怎么办？

#### 1，首先，我们给Cat（猫）定义一个主人类：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class Master {
    @Value("1")
    private Integer id;
 
    @Value("V哥")
    private String name;
}
```

#### 2，然后改造我们的Cat类：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class Cat {
    @Value("1")
    private Integer id;
 
    @Value("汤圆")
    private String name;
 
    @Value("美短")
    private String breed;
 
    @Autowired//这个注解回去Spring的ioc容器中寻找对应类型的bean，然后引用过来
    private Master master;
}
```

这里我们使用了AutoWried注解。这个注解的作用是，Spring把所有的Bean都生成好了之后，如果发现了有这个注解，Spring就会按照这个属性的类型去Spring容器里面找到对应的已经创建好的Bean，然后注入到这个属性中。

上面我们讲了自动装配，但是是有一些问题的。比如我们的Master没有注入到IOC容器中的时候，上面程序报错。但是有的时候，我们就希望如果容器中有对应类型的Bean就引用过来。如果没有对应类型的Bean那么就不要应用。这个时候，我们可以使用AutoWired的required属性。

```java
@Autowired(required = false)
private Master master;
```

这里我们说一下，我们除了配置属性之外，还可以配置属性方法。比如我们可以在属性对应的set方法上来配置这个注解完成。但是没有必要，因为对于PO，我们一般都是使用lombok来开发。然后对于Service，Controller我们根本就没有为属性提供get和set方法的必要。

### 7，自动装配的歧义

我们上面讲解了Autowried注解，使用它是非常简单的，并且可以完成自动装配的功能。它是按照类型来匹配。这个时候会产生一些问题。

比如我们定义一个接口叫做Cat：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
public interface Cat {
    void say();
}
```

他分别有两个实现类，一个是MeiduanCat，一个是LihuaCat:

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import org.springframework.stereotype.Component;
 
@Component
public class MeiduanCat implements Cat {
    @Override
    public void say() {
        System.out.println("喵喵");
    }
}
```

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import org.springframework.stereotype.Component;
 
@Component
public class LihuaCat implements Cat {
    @Override
    public void say() {
        System.out.println("哈哈");
    }
}
```

然后，我们把Cat类型引用到另外一个bean中。

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class Master {
    @Autowired
    private Cat cat;
 
    public void catSay() {
        cat.say();
    }
}
```

这个时候我们运行，直接报错，这个是因为Cat是借口，对应有两个实现类，一个是MeiduanCat一个是LihuaCat。我们使用Autowried注解来注入一个Cat的时候，Spring发现有两个不同类型的对象都是可以注入的。这个时候，Spring就不知道该注入哪一个了。这个时候程序直接报错。

### 8，注解Primary

注解Primary代表受邀的，当Spring IOC通过一个接口或者抽象类注入对象的时候，如果存在了多个实现类。spring就不知道该注入哪一个好了。这个我们可以使用Primary注解。这个注解的作用就是告诉Spring容器，优先使用我来注入。

```java
@Component
@Primary
public class LihuaCat implements Cat {
    @Override
    public void say() {
        System.out.println("哈哈");
    }
}
```

### 9，注解Qualifier
上面我们可以是用Primary注解来设置一个有限注入的对象。但是有的时候还是不能满足我们的需求，因为使用了这个注解之后，我们只要使用的AutoWired注解来注入对象的时候，都会注入加入了Primary注解的对象。而其他对象就无法注入进来了。这个时候，Spring给我们提供了一个按照名称来注入的方式。这个名称就是Bean的id。

#### 1，在注入的Component的时候，我们指定Bean的id

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import org.springframework.stereotype.Component;
 
@Component("lihuaCat")
public class LihuaCat implements Cat {
    @Override
    public void say() {
        System.out.println("哈哈");
    }
}
```

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import org.springframework.stereotype.Component;
 
@Component("meiduanCat")
public class MeiduanCat implements Cat {
    @Override
    public void say() {
        System.out.println("喵喵");
    }
}
```

#### 2，在引用的时候，我们通过Qualifier注解来引用对应的Bean

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class Master {
    @Autowired
    @Qualifier("meiduanCat")
    private Cat cat;
 
    public void catSay() {
        cat.say();
    }
}
```

### 10，注解+构造方法注入

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class Master {
    private Cat cat;
 
    public Master(@Autowired @Qualifier("lihuaCat") Cat cat) {
        this.cat = cat;
    }
 
    public void catSay() {
        cat.say();
    }
}
```

### 11，使用Bean注解：
上面我们都是通过Component来装配Bean。但是Component注解只能用在类上面，不能用在方法上面。但是，如果我们遇到我们要注入一个第三方包提供的类，我们应该怎么办呢？

比如，我们使用Druid来创建一个数据库连接池，但是我们希望这个连接池要让spring来管理。但是Druid阿里巴巴给我们提供的是第三方的开源包，我们不可能去修改源代码让其带上Component注解。这个时候我们又希望要注入，怎么办？

#### 1，导入druid和mysql驱动:

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.2.5</version>
</dependency>
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.21</version>
    <scope>runtime</scope>
</dependency>
```

#### 2,我们修改BeanConfig类，让其成为一个配置类。加上Configuration注解。

```java
package com.vgxit.learn.spring.ktdm.vgannioc.config;
 
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
 
@ComponentScan(basePackages = "com.vgxit.learn.spring.ktdm.vgannioc.beans")//定义扫描包的路劲
@Configuration//表明这个类是一个配置类
public class VgAnnIocConfig {
}
```

#### 3，定义druid数据库连接的属性，druid.properties：

```properties
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai
username=root
password=Abc@123456
# 初始化连接数量
initialSize=5
# 最大连接数
maxActive=10
# 最大等待时间
maxWait=3000
```

#### 4，提供获取数据库连接池的方法：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.config;
 
import com.alibaba.druid.pool.DruidDataSourceFactory;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import javax.sql.DataSource;
import java.io.InputStream;
import java.util.Properties;
 
@ComponentScan(basePackages = "com.vgxit.learn.spring.ktdm.vgannioc.beans")//定义扫描包的路劲
@Configuration//表明这个类是一个配置类
public class VgAnnIocConfig {
    /**
     * 定义一个获取数据源的方法
     * @return
     */
    @Bean(name = "dataSource")//我们把方法返回的数据源作为一个Bean注入到Spring容器中
    public DataSource getDataSource() throws Exception {
        Properties properties = new Properties();
        InputStream druidInputStram = VgAnnIocConfig.class.getClassLoader().getResourceAsStream("druid.properties");
        properties.load(druidInputStram);
        DataSource ds = DruidDataSourceFactory.createDataSource(properties);
        return ds;
    }
}
```

#### 5，编写数据库连接池的使用方法：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.test;
 
import com.vgxit.learn.spring.ktdm.vgannioc.config.VgAnnIocConfig;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import javax.sql.DataSource;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
 
public class VganniocTest002 {
    public static void main(String[] args) throws SQLException {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(VgAnnIocConfig.class);
        DataSource ds = ctx.getBean(DataSource.class);
        //新的语法来给大家写try resources
        Connection conn = ds.getConnection();
        PreparedStatement ps = conn.prepareStatement("select * from user");
        ResultSet rs = ps.executeQuery();
        try (conn; ps; rs){
            while (rs.next()) {
                System.out.println(rs.getInt("id") + "-------->" + rs.getString("name"));
            }
        }
    }
}
```

### 12，单例注入和多例注入
我们上面的所有的注入方式，在Spring中其实使用单例的方式的。也就是我们创建好了对应的Bean之后，放到Spring容器中，我们要用得时候，Spring自己去IOC容器里面拿出来给我们用就好了。但是，我们还可以进过配置让Spring用多例的方式给我们创建。多例注入的意思，就是我们要使用的时候，spring会给我们立马创建一个（new一个）出来，然后给我们使用。

比如，我们来看看原来的使用方式：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class Master {
    @Autowired @Qualifier("lihuaCat")
    private Cat cat;
 
    public Master() {
        System.out.println("创建了Master对象");
    }
 
    public void catSay() {
        cat.say();
    }
}
```

然后，我们通过spring容器两次获取了对应的Master对象：

```java
public static void main(String[] args) {
        //获取Spring的上下文
        ApplicationContext ctx = new AnnotationConfigApplicationContext(VgAnnIocConfig.class);
        //在ioc容器中找到对应的类型的bean，然后返回
        Master master1 = ctx.getBean(Master.class);
        master1.catSay();
        Master master2 = ctx.getBean(Master.class);
        master2.catSay();
    }
```

然后我们发现Master对应的构造方法被调用了两次。

但是如果我们使用多例的注入方式，那么对应的代码如下：

```java
package com.vgxit.learn.spring.ktdm.vgannioc.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;
 
@Component
@Data
@Scope("prototype")//这种方式就是多例的注入方式
public class Master {
    @Autowired @Qualifier("lihuaCat")
    private Cat cat;
 
    public Master() {
        System.out.println("创建了Master对象");
    }
 
    public void catSay() {
        cat.say();
    }
}
```

这个时候我们重新运行测试代码，可以发现Family的构造方法被调用了两次，这个可以证明，Spring每次都给我们创建了一个新对象。在默认情况下@Scope默认的方式就是单例的。如果我们要配置多列可以用@Scope("prototype")，当然我们要手动实现单例可以使用@Scope("singleton")

如果我们使用xml的方式来配置单例和多列，可以使用bean标签的scope属性。这里老师就不给大家演示了，大家自己下来手动实验一下。

## 7，Spring混合装配

### 1，概述
之前的课程介绍了最基本的装配Bean方法，我们对XML的方式和注解的方式都进行了讲解。在现实中，使用XML或者注解各有道理，V哥建议在自己的工程中所开发的类尽量使用注解方式，因为使用它并不困难，甚至可以说更为简单，而对于引入第三方包的类，尽量使用XML方式，这样的好处是可以尽量对三方包或者服务的细节减少理解，也更加清晰和明朗。

但是V哥给大家说一下，现在我们使用的是混合装配的方式。不过之后大家学习了Spring boot之后，XML的方式基本上是不会再使用了。都是注解的方式。

### 2，具体操作（基于注解的方式）
我们按照真实开发项目的一个流程，来给大家演示一下从数据库里面查询所有的用户数据的这么一个流程。

#### 1，首先，我们创建对应的PO:

```java
package com.vgxit.learn.spring.ktdm.blendioc.po;
 
import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;
 
@Data
@AllArgsConstructor
@NoArgsConstructor
@Builder
public class User {
    private Integer id;
    private String name;
    private Short gender;
    private Integer age;
    private String nickName;
}
```

#### 2, 我们定义好对应的IUserService和UserService:

```java
package com.vgxit.learn.spring.ktdm.blendioc.service;
 
import com.vgxit.learn.spring.ktdm.blendioc.po.User;
 
import java.sql.SQLException;
import java.util.List;
 
public interface IUserService {
    List<User> all() throws SQLException;
}
```

```java
package com.vgxit.learn.spring.ktdm.blendioc.service.impl;
 
import com.vgxit.learn.spring.ktdm.blendioc.po.User;
import com.vgxit.learn.spring.ktdm.blendioc.service.IUserService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
import javax.sql.DataSource;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;
 
@Component
public class UserService implements IUserService {
    @Autowired
    private DataSource dataSource;
    @Override
    public List<User> all() throws SQLException {
        Connection conn = dataSource.getConnection();
        PreparedStatement ps = conn.prepareStatement("select * from user");
        ResultSet rs = ps.executeQuery();
        List<User> users = new ArrayList<>();
        try (conn;ps;rs){
            while (rs.next()) {
                User user = User.builder()
                        .id(rs.getInt("id"))
                        .gender(rs.getShort("gender"))
                        .age(rs.getInt("age"))
                        .name(rs.getString("name"))
                        .nickName(rs.getString("nick_name"))
                        .build();
                users.add(user);
            }
        }
        return users;
    }
}
```

#### 3，定义一个Spring的配置文件，然后，其中配置druid对应的xml注入配置：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!--存放bean的容器-->
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
    <!--配置我们的数据源-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="com.mysql.cj.jdbc.Driver"/>
        <property name="url" value="jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai"/>
        <property name="username" value="root"/>
        <property name="password" value="Abc@123456"/>
        <property name="initialSize" value="1"/>
        <property name="minIdle" value="1"/>
        <property name="maxActive" value="20"/>
    </bean>
</beans>
```

#### 4，定义配置类，这里我们把扫描包调整到总包下面，还要在这个配置类下面引入对应的XML文件：

```java
package com.vgxit.learn.spring.ktdm.blendioc.config;
 
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.ImportResource;
 
@ComponentScan(basePackages = "com.vgxit.learn.spring.ktdm.blendioc")
@ImportResource("classpath:spring-cfg.xml")//引入对应的xml配置文件
public class BlendiocConfig {
}
```

#### 5，测试代码：

```java
package com.vgxit.learn.spring.ktdm.blendioc.test;
 
import com.vgxit.learn.spring.ktdm.blendioc.config.BlendiocConfig;
import com.vgxit.learn.spring.ktdm.blendioc.po.User;
import com.vgxit.learn.spring.ktdm.blendioc.service.IUserService;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import java.sql.SQLException;
import java.util.List;
 
public class BlendiocTest001 {
    public static void main(String[] args) throws SQLException {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(BlendiocConfig.class);
        IUserService userService = ctx.getBean(IUserService.class);
        List<User> users = userService.all();
        users.forEach(System.out::println);
    }
}
```

### 3，混合装配的第二种方式（基于xml的装配方式）：

#### 1，我们在xml中加上context的xsd文件，然后配置我们要扫描的包的路劲：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!--存放bean的容器-->
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd">
    <!--配置我们扫描包的路劲-->
    <context:component-scan base-package="com.vgxit.learn.spring.ktdm.blendioc"/>
    <!--配置我们的数据源-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="com.mysql.cj.jdbc.Driver"/>
        <property name="url" value="jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai"/>
        <property name="username" value="root"/>
        <property name="password" value="Abc@123456"/>
        <property name="initialSize" value="1"/>
        <property name="minIdle" value="1"/>
        <property name="maxActive" value="20"/>
    </bean>
</beans>
```

#### 2，加入我们的测试代码：

```java
package com.vgxit.learn.spring.ktdm.blendioc.test;
 
import com.vgxit.learn.spring.ktdm.blendioc.po.User;
import com.vgxit.learn.spring.ktdm.blendioc.service.IUserService;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
 
import java.sql.SQLException;
import java.util.List;
 
public class BlendiocTest001 {
    public static void main(String[] args) throws SQLException {
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
        IUserService userService = ctx.getBean(IUserService.class);
        List<User> users = userService.all();
        users.forEach(System.out::println);
    }
}
```

## 8，Spring 环境区分

### 1，概述
在软件开发的过程中，敏捷开发模式很常见，也就是每次都提交一个小阶段的测试，那么可能是开发人员使用一套环境（开发环境），而测试人员使用另一套环境（测试环境），而这两套系统的数据库是不一样的，毕竟测试人员也需要花费很多的时间去构建测试数据，可不想老是被开发人员修改那些测试数据，这样就有了在不同的环境中进行切换的需求了。

### 2，注解方式区分环境
比如，我们在开发的时候，开发人员连接的数据库和测试人员连接的数据库是分开的。这个时候，我们可以用如下的方式来做

#### 1，首先我们定义两个方法，来获取两个环境不同的数据源：

```java
package com.vgxit.learn.profile.config;
 
import com.alibaba.druid.pool.DruidDataSourceFactory;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import javax.sql.DataSource;
import java.io.InputStream;
import java.util.Properties;
 
@ComponentScan(basePackages = "com.vgxit.learn.profile.config")
@Configuration
public class ProfileConfig {
    /**
     * 获取开发环境的数据源
     * @return
     */
    @Bean(name = "devDataSource")
    public DataSource devDataSource() throws Exception {
        Properties properties = new Properties();
        InputStream druidInputStram = ProfileConfig.class.getClassLoader().getResourceAsStream("dev.druid.properties");
        properties.load(druidInputStram);
        DataSource ds = DruidDataSourceFactory.createDataSource(properties);
        return ds;
    }
 
    /**
     * 获取测试环境的数据源
     * @return
     */
    @Bean(name = "qaDataSource")
    public DataSource qaDataSource() throws Exception {
        Properties properties = new Properties();
        InputStream druidInputStram = ProfileConfig.class.getClassLoader().getResourceAsStream("qa.druid.properties");
        properties.load(druidInputStram);
        DataSource ds = DruidDataSourceFactory.createDataSource(properties);
        return ds;
    }
}
```

#### 2，我们直接测试运行：

```java
package com.vgxit.learn.profile.test;
 
import com.vgxit.learn.profile.config.ProfileConfig;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import javax.sql.DataSource;
 
public class ProfileTest {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(ProfileConfig.class);
        DataSource dataSource = ctx.getBean(DataSource.class);
        System.out.println(dataSource);
    }
}
```

直接运行，立马报错，这个是因为我们在Spring里面注入了两个DataSource类型的Bean，我们在获取的时候，就不知道应该用哪一个了。这个时候，如果我们是测试环境，我们用devDataSource，如果是qa环境，俺么我们使用qaDataSource。

如果要达到这个效果，首先我们应该给不同的数据源指定不同的环境。

```java
package com.vgxit.learn.profile.config;
 
import com.alibaba.druid.pool.DruidDataSourceFactory;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Profile;
 
import javax.sql.DataSource;
import java.io.InputStream;
import java.util.Properties;
 
@ComponentScan(basePackages = "com.vgxit.learn.profile.config")
@Configuration
public class ProfileConfig {
    /**
     * 获取开发环境的数据源
     * @return
     */
    @Bean(name = "devDataSource")
    @Profile("dev")
    public DataSource devDataSource() throws Exception {
        Properties properties = new Properties();
        InputStream druidInputStram = ProfileConfig.class.getClassLoader().getResourceAsStream("dev.druid.properties");
        properties.load(druidInputStram);
        DataSource ds = DruidDataSourceFactory.createDataSource(properties);
        return ds;
    }
 
    /**
     * 获取测试环境的数据源
     * @return
     */
    @Bean(name = "qaDataSource")
    @Profile("qa")
    public DataSource qaDataSource() throws Exception {
        Properties properties = new Properties();
        InputStream druidInputStram = ProfileConfig.class.getClassLoader().getResourceAsStream("qa.druid.properties");
        properties.load(druidInputStram);
        DataSource ds = DruidDataSourceFactory.createDataSource(properties);
        return ds;
    }
}
```

但是我们继续测试，还是发现报错。这个是因为我们还没有指定我们当前是什么环境。那么我们接下来就要指定环境。

![img](https://raw.githubusercontent.com/Chalice555/Picgo/master/2021060516165822.png)

![img](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210605161742796.png)

接下来再运行，不报错了。

### 3，xml的方式来区分环境

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
    <beans profile="dev">
        <bean id="devDataSource" class="com.alibaba.druid.pool.DruidDataSource">
            <property name="driverClassName" value="com.mysql.cj.jdbc.Driver"/>
            <property name="url" value="jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai"/>
            <property name="username" value="root"/>
            <property name="password" value="Abc@123456"/>
            <property name="initialSize" value="1"/>
            <property name="minIdle" value="1"/>
            <property name="maxActive" value="20"/>
        </bean>
    </beans>
    <beans profile="qa">
        <bean id="qaDataSource" class="com.alibaba.druid.pool.DruidDataSource">
            <property name="driverClassName" value="com.mysql.cj.jdbc.Driver"/>
            <property name="url" value="jdbc:mysql://localhost:3306/mybatis?serverTimezone=Asia/Shanghai"/>
            <property name="username" value="root"/>
            <property name="password" value="Abc@123456"/>
            <property name="initialSize" value="1"/>
            <property name="minIdle" value="1"/>
            <property name="maxActive" value="20"/>
        </bean>
    </beans>
</beans>
```

## 9，Spring 加载属性配置文件

### 1，概述
在实际的开发中往往有很多配置是写在properties类型的配置文件中的。我们使用Spring的时候，也需要能够加载并读取到配置文件。解决的思路是，spring应用在启动的时候，找到对应的配置文件，然后读取到内存中，要使用的时候，我们调用Spring为我们提供的Api进行读取。

### 2，使用直接加载的方式加载读取properties文件：
首先，我们在resources下面创建一个properties配置文件。这里我们就用之前用过的druid.properties文件就好了：

```properties
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai
username=root
password=Abc@123456
# 初始化连接数量
initialSize=5
# 最大连接数
maxActive=10
# 最大等待时间
maxWait=3000
```

我们定义一个Spring框架加载配置的类：

```java
package com.vgxit.learn.spring.ktdm.properties.config;
 
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.PropertySource;
 
@ComponentScan(basePackages = "com.vgxit.learn.spring.ktdm.properties")
@Configuration
@PropertySource(value = "classpath:druid.properties", ignoreResourceNotFound = true)//spring启动的时候，会自动的读取druid.properties文件的配置放在内存中
public class PropConfig {
}
```

这里，我们使用了一个注解@PropertySource来定义我们的properties配置文件的路劲。这个注解有几个配置项，我们这里说一下：

name:字符串，表示这次属性配置的名称，一般情况下，我们不用填写
value:对应的配置文件的数组
ignoreResourceNotFound:如果找不到配置文件，是否忽略。默认情况是下false，如果是true表示如果找不到对应的配置文件直接忽略。如果是false的话，找不到对应的配置文件会直接抛出异常
对应的测试代码如下：

```java
package com.vgxit.learn.spring.ktdm.properties.test;
 
import com.vgxit.learn.spring.ktdm.properties.config.PropConfig;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
 
public class PropertyTest {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(PropConfig.class);
        String url = ctx.getEnvironment().getProperty("url");
        System.out.println(url);
    }
}
```

### 3，通过属性占位符加载：

通过属性占位符的方式加载配置文件，意思就是我们把对应的配置文件加载进来之后，赋值给一个我们已经定义好的对象的各个属性。

#### 1，首先我们定义好一个项目配置类，配置类里面我们注入一个可以实现属性加载的配置工具

```java
package com.vgxit.learn.spring.ktdm.properties.config;
 
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.PropertySource;
import org.springframework.context.support.PropertySourcesPlaceholderConfigurer;
 
@ComponentScan("com.vgxit.learn.spring.ktdm.properties")
@Configuration
@PropertySource("classpath:druid.properties")
public class PropSeatConfig {
    /**
     * 注入舒心占位工具类
     * @return
     */
    @Bean
    public PropertySourcesPlaceholderConfigurer propertySourcesPlaceholderConfigurer() {
        return new PropertySourcesPlaceholderConfigurer();
    }
}
```

这个地方我们注入了一个Bean，名字叫做PropertySourcesPlaceholderConfigurer。它的作用就是让Spring能够解析属性占位符。这里只要创建了这个Bean，Spring会自动的给我们属性占位符赋值。

#### 2，定义配置文件：

```properties
datasource.driverClassName=com.mysql.cj.jdbc.Driver
datasource.url=jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai
datasource.username=root
datasource.password=Abc@123456
# 初始化连接数量
datasource.initialSize=5
# 最大连接数
datasource.maxActive=10
# 最大等待时间
datasource.maxWait=3000
```

#### 3，编写一个JavaBean来接收这些配置：

```java
package com.vgxit.learn.spring.ktdm.properties.propconfig;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class DataSourceConfig {
    @Value("${driverClassName}")
    private String driverClassName;
 
    @Value("${url}")
    private String url;
 
    @Value("${username}")
    private String username;
 
    @Value("${password}")
    private String password;
 
    @Value("${initialSize}")
    private Integer initialSize;
 
    @Value("${maxActive}")
    private Integer maxActive;
 
    @Value("${maxWait}")
    private Integer maxWait;
}
```

#### 4，测试代码：

```java
package com.vgxit.learn.spring.ktdm.properties.test;
 
import com.vgxit.learn.spring.ktdm.properties.config.PropSeatConfig;
import com.vgxit.learn.spring.ktdm.properties.propconfig.DataSourceConfig;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
 
public class PropSetTest {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(PropSeatConfig.class);
        DataSourceConfig dataSourceConfig = ctx.getBean(DataSourceConfig.class);
        System.out.println(dataSourceConfig);
    }
}
```

这个时候我们发现除了username之外的其他属性都是OK的。username属性编程Administrator。这个是因为我们使用windows操作系统，当前登陆的用户就是Administrator，而spring启动的时候，读取配置会优先读取系统配置。所以我们为了解决这个问题，可以再配置上加上前缀：

```properties
datasource.driverClassName=com.mysql.cj.jdbc.Driver
datasource.url=jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai
datasource.username=root
datasource.password=Abc@123456
# 初始化连接数量
datasource.initialSize=5
# 最大连接数
datasource.maxActive=10
# 最大等待时间
datasource.maxWait=3000
```

```java
package com.vgxit.learn.spring.ktdm.properties.propconfig;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class DataSourceConfig {
    @Value("${datasource.driverClassName}")
    private String driverClassName;
 
    @Value("${datasource.url}")
    private String url;
 
    @Value("${datasource.username}")
    private String username;
 
    @Value("${datasource.password}")
    private String password;
 
    @Value("${datasource.initialSize}")
    private Integer initialSize;
 
    @Value("${datasource.maxActive}")
    private Integer maxActive;
 
    @Value("${datasource.maxWait}")
    private Integer maxWait;
}
```

现在再来查看打印配置类，一切正常。

### 4，通过XML的方式加载配置文件

#### 1，首先我们定义好接收properties配置文件的类。

```java
package com.vgxit.learn.spring.ktdm.properties.propconfig;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class DataSourceConfig {
    @Value("${datasource.driverClassName}")
    private String driverClassName;
 
    @Value("${datasource.url}")
    private String url;
 
    @Value("${datasource.username}")
    private String username;
 
    @Value("${datasource.password}")
    private String password;
 
    @Value("${datasource.initialSize}")
    private Integer initialSize;
 
    @Value("${datasource.maxActive}")
    private Integer maxActive;
 
    @Value("${datasource.maxWait}")
    private Integer maxWait;
}
```

#### 2，创建对应的xml，加上对应xsd和对应的配置：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd">
    <!--定义对应的扫描包-->
    <context:component-scan base-package="com.vgxit.learn.spring.ktdm.properties"/>
    <!--引入一个配置文件，如果有多个配置文件，我们用逗号隔开-->
    <context:property-placeholder ignore-resource-not-found="false" location="druid.properties"/>
</beans>
```

## 10，Spring 条件化装配Bean

### 1，概述
有的时候我们在开发的时候需要按照条件来装配不同Bean。比如，我们开发一套人力资源管理系统。我们把这个系统分别提供给了公司A和公司B。但是公司A和公司B在导入用户数据的时候需求不同。公司A是导出了一个大的Json的文件给我们，让我们上传这个文件导入。而公司B是导出了一个Excel文件给我们，让我们导入这个文件。这个时候怎么办呢？

### 2，具体实现
思维导图：

![img](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210605214223272.png)

#### 1，定义一个员工数据操作的业务逻辑层，IEmployeeService接口

```java
package com.vgxit.learn.spring.ktdm.condition.service;
public interface IEmployeeService {
    void implodeEmployees();
}
```

#### 2，定义两个接口的实现类，分别代表A公司的业务，和B公司的业务

```java
package com.vgxit.learn.spring.ktdm.condition.service.impl;
 
import com.vgxit.learn.spring.ktdm.condition.service.IEmployeeService;
import org.springframework.stereotype.Component;
 
@Component
public class AEmployeeService implements IEmployeeService {
    @Override
    public void implodeEmployees() {
        System.out.println("A公司导入员工");
    }
}
```

```java
package com.vgxit.learn.spring.ktdm.condition.service.impl;
 
import com.vgxit.learn.spring.ktdm.condition.service.IEmployeeService;
import org.springframework.stereotype.Component;
 
@Component
public class BEmployeeService implements IEmployeeService {
    @Override
    public void implodeEmployees() {
        System.out.println("B公司导入员工");
    }
}
```

#### 3，写一个配置文件来定义当前运行的业务环境，application.properties:

```properties
business.env=ENVA
```

#### 4，编写对应的配置类：

```java
package com.vgxit.learn.spring.ktdm.condition.config;
 
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.PropertySource;
 
@ComponentScan("com.vgxit.learn.spring.ktdm.condition")
@PropertySource("classpath:appliction.properties")
public class ConditionConfig {
}
```

#### 5，定义对应的加载条件类：

```java
package com.vgxit.learn.spring.ktdm.condition.conditionbean;
 
import org.springframework.context.annotation.Condition;
import org.springframework.context.annotation.ConditionContext;
import org.springframework.core.type.AnnotatedTypeMetadata;
import org.springframework.stereotype.Component;
 
/**
 * 定义加载条件类
 */
public class ACondition implements Condition {
    /**
     * 条件生成的方法，如果这个方法的结果为true就表示要注入对应的Bean
     * @param conditionContext
     * @param annotatedTypeMetadata
     * @return
     */
    @Override
    public boolean matches(ConditionContext conditionContext, AnnotatedTypeMetadata annotatedTypeMetadata) {
        String envStr = conditionContext.getEnvironment().getProperty("business.env");
        return "ENVA".equals(envStr);
    }
}
```

```java
package com.vgxit.learn.spring.ktdm.condition.conditionbean;
 
import org.springframework.context.annotation.Condition;
import org.springframework.context.annotation.ConditionContext;
import org.springframework.core.type.AnnotatedTypeMetadata;
 
public class BCondition implements Condition {
    @Override
    public boolean matches(ConditionContext conditionContext, AnnotatedTypeMetadata annotatedTypeMetadata) {
        String envStr = conditionContext.getEnvironment().getProperty("business.env");
        return "ENVB".equals(envStr);
    }
}
```

#### 6，测试代码：

```java
package com.vgxit.learn.spring.ktdm.condition.test;
 
import com.vgxit.learn.spring.ktdm.condition.config.ConditionConfig;
import com.vgxit.learn.spring.ktdm.condition.service.IEmployeeService;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
 
public class ConditionTest001 {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(ConditionConfig.class);
        IEmployeeService employeeService = ctx.getBean(IEmployeeService.class);
        employeeService.implodeEmployees();
    }
}
```

## 11，Spring表达式（了解）

### 1，概述

Spring还提供了更加灵活的注入方式。那就是Spring表达式，也叫做Spring EL。Spring EL非常强大。我们本节课会好好的学习。

### 2，Bean属性设置默认值

```java
package com.vgxit.learn.spring.ktdm.el.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class User {
    @Value("#{1}")
    private Integer id;
 
    @Value("#{'liyitong'}")
    private String username;
 
    @Value("#{'tongtong'}")
    private String nickname;
}
```

### 3，引用其他对象和其他对象的属性

#### 1，定义一个Role对象

```java
package com.vgxit.learn.spring.ktdm.el.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component("role")
@Data
public class Role {
    @Value("#{1}")
    private Integer id;
 
    @Value("#{'超级管理员'}")
    private String name;
}
```

#### 2，我们在User对象中，引用一个Role对象和这个对象的名称

```java
package com.vgxit.learn.spring.ktdm.el.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class User {
    @Value("#{1}")
    private Integer id;
 
    @Value("#{'liyitong'}")
    private String username;
 
    @Value("#{'tongtong'}")
    private String nickname;
 
    @Value("#{role}")
    private Role role;
 
    @Value("#{role.getName()}")
    private String roleName;
}
```

### 4，引用静态方法和常量

有的时候，我们希望使用一些静态方法和常量，比如我们要用到圆周率。这个圆周率其实在Java的Math对象中就定义了一个PI的常量。

```java
package com.vgxit.learn.spring.ktdm.el.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class User {
    @Value("#{1}")
    private Integer id;
 
    @Value("#{'liyitong'}")
    private String username;
 
    @Value("#{'tongtong'}")
    private String nickname;
 
    @Value("#{role}")
    private Role role;
 
    @Value("#{role.getName()}")
    private String roleName;
 
    @Value("#{T(Math).PI}")
    private Double pi;
 
    @Value("#{T(Math).random()}")
    private Double rand;
 
    @Value("#{T(com.vgxit.learn.spring.ktdm.el.changliang.Changliang).NUM}")//引用定义在非java.lang包西面的类，需要写全路径名
    private Integer num;
}
```

### 5，EL表达式运算

```java
package com.vgxit.learn.spring.ktdm.el.beans;
 
import lombok.Data;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
 
@Component
@Data
public class User {
    @Value("#{1}")
    private Integer id;
 
    @Value("#{'liyitong'}")
    private String username;
 
    @Value("#{'tongtong'}")
    private String nickname;
 
    @Value("#{role}")
    private Role role;
 
    @Value("#{role.getName()}")
    private String roleName;
 
    @Value("#{T(Math).PI > 4 ? '大于4' : '小于等于4'}")
    private String pi;
 
    @Value("#{T(Math).random()}")
    private Double rand;
 
    @Value("#{T(com.vgxit.learn.spring.ktdm.el.changliang.Changliang).NUM}")//引用定义在非java.lang包西面的类，需要写全路径名
    private Integer num;
 
    @Value("#{T(Math).PI < 4}")
    private Boolean flag;
}
```

## 12，Spring 面向切面，问题引入

### 1，概述
如果说IOC是Spring的核心，那么面向切面就是Spring最重要的功能之一了，面向切面的专业术语叫做AOP。在数据库事物中切面编程是广泛应用的。

### 2，AOP的概念和使用原因
我们就用我们的数据库编程来举例。比如，我们做了一个电商系统，我们要做一块使用账户余额支付的功能。这个功能一般情况下需要四个操作来支撑，分别是：1，商品库存减一。2，生成一个订单。3，账户余额扣款。4，生成一条交易记录。

按照没用Spring之前的操作我们可能会写如下伪代码：

```java
商品扣库存;
if(商品库存扣成功) {
    生成订单;
    if(订单生成成功){
        账户余额扣款;
        if(账户余额扣款成功) {
            生成一条交易记录;
            if (交易记录生成成功) {
                提交事物;
            } else {
                事物回滚;
            }
        } else {
            事物回滚;
        }
    } else {
        事物回滚;
    }
} else {
    事物回滚;
}
```

对应的流程图如下：

![img](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210606000241946.png)

从上面的情况，我们可以看出来我们代码编写得真的是非常非常的复杂。如果我们采用Spring Aop来管理事物，我们可以用如下流程图来代替。

![img](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210606001611268.png)

我们通过上图可以看到，如果我们使用了Spring Aop来管理事物之后，我们的流程就会变得非常的简单。我们只需要做到如果数据库操作失败就直接抛出异常就行了。其他的，我们完全不用关心。那么我们思考一下我们如何才能做到这样的逻辑呢？

AOP是通过动态代理模式来管控哥哥对象操作的切换环境。包括日志，数据库事物等操作。让我们可以在反射原有对象方法正常返回，异常之前和返回后插入自己的逻辑代码的能力。在一些常用的流程中，比如数据库事物，AOP会提供默认的实现逻辑，也会提供一些简单的配置，程序员就能方便的修改默认的实现，从而达到符合真实引用要求的效果。提升代码的可读性，将开发集中在也业务逻辑上。

### 3，自己手写Aop:

自己实现AOP需要用到动态代理的知识，我们在这里就不会给大家再来介绍动态代理的知识了。如果大家没有这方面的知识，你需要去学习一下，看看老师之前讲的《简单设计模式入门》这门课程。我们这里手写AOP我们使用添加用户这样的逻辑来实现。

#### 1，定义一个PO:

```java
package com.vgxit.learn.spring.ktdm.myaop.po;
 
import lombok.Data;
 
@Data
public class User {
    private Integer id;
    private String name;
    private Short gender;
}
```

#### 2，创建对应的业务逻辑层的接口

```java
package com.vgxit.learn.spring.ktdm.myaop.service;
 
import com.vgxit.learn.spring.ktdm.myaop.po.User;
 
public interface IUserService {
    void add(User user);
}
```

#### 3，编写对应的业务逻辑层的实现类

```java
package com.vgxit.learn.spring.ktdm.myaop.service.impl;
 
import com.vgxit.learn.spring.ktdm.myaop.po.User;
import com.vgxit.learn.spring.ktdm.myaop.service.IUserService;
 
public class UserService implements IUserService {
    @Override
    public void add(User user) {
        System.out.println("添加用户[" + user + "]到数据库");
    }
}
```

#### 4，提供一个Interceptor拦截器接口，这个接口里面定义了再具体的业务方法之前，之后，正常返回，异常返回的时候我们要插入的代码：

```java
package com.vgxit.learn.spring.ktdm.myaop.aop;
 
public interface Interceptor {
    //业务方法开始之前调用的代码
    void before(Object obj);
    //业务方法开始之后调用的代码
    void after(Object obj);
    //业务方法正常返回之后调用的代码
    void afterReturning(Object obj);
    //业务方法异常返回之后调用的代码
    void afterThrowing(Object obj);
}
```

#### 5，编写Interceptor的具体实现类：

```java
package com.vgxit.learn.spring.ktdm.myaop.aop;
public class TranInterceptor implements Interceptor {
    @Override
    public void before(Object obj) {
        System.out.println("获取数据库连接");
        System.out.println("开启事务");
    }
 
    @Override
    public void after(Object obj) {
        System.out.println("对应逻辑执行完成");
    }
 
    @Override
    public void afterReturning(Object obj) {
        System.out.println("提交事物");
    }
 
    @Override
    public void afterThrowing(Object obj) {
        System.out.println("事物回滚");
    }
}
```

#### 6，实现动态代理工具类：

```java
package com.vgxit.learn.spring.ktdm.myaop.proxy;
 
import com.vgxit.learn.spring.ktdm.myaop.aop.Interceptor;
 
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;
 
public class ProxyUtil implements InvocationHandler {
    //被代理的对象
    private Object target;
    //对应的拦截器
    private Interceptor interceptor;
 
    //获取对应的代理对象
    public static <T> T getBean(T target, Interceptor interceptor) {
        ProxyUtil proxyUtil = new ProxyUtil();
        proxyUtil.target = target;
        proxyUtil.interceptor = interceptor;
        return (T) Proxy.newProxyInstance(ProxyUtil.class.getClassLoader(), target.getClass().getInterfaces(), proxyUtil);
    }
 
    @Override
    public Object invoke(Object o, Method method, Object[] objects) throws Throwable {
        //到时候要返回的数据
        Object result = null;
        boolean hasException = false;
        interceptor.before(target);
        try {
            //调用真实方法
            result = method.invoke(target, objects);
        } catch (Throwable e) {
            hasException = true;
        } finally {
            interceptor.after(target);
        }
        if (hasException) {
            interceptor.afterThrowing(target);
        } else {
            interceptor.afterReturning(target);
        }
        return result;
    }
}
```

#### 7，测试代码：

```java
package com.vgxit.learn.spring.ktdm.myaop.test;
 
import com.vgxit.learn.spring.ktdm.myaop.aop.Interceptor;
import com.vgxit.learn.spring.ktdm.myaop.aop.TranInterceptor;
import com.vgxit.learn.spring.ktdm.myaop.po.User;
import com.vgxit.learn.spring.ktdm.myaop.proxy.ProxyUtil;
import com.vgxit.learn.spring.ktdm.myaop.service.IUserService;
import com.vgxit.learn.spring.ktdm.myaop.service.impl.UserService;
 
public class MyAopTest001 {
    public static void main(String[] args) {
        IUserService target = new UserService();
        Interceptor interceptor = new TranInterceptor();
        IUserService userService = ProxyUtil.getBean(target, interceptor);
        User user = new User();
        user.setId(1);
        user.setName("李一桐");
        user.setGender((short) 2);
        userService.add(user);
    }
}
```

## 13，Spring Aop基于AspectJ开发

### 1，选择切点
Spring是一个方法级别的AOP框架。也就是我们可以再调用某个方法之前，之后，正常返回之后，异常返回之后来切入我们的代码。我们需要被拦截的方法就叫做一个切点。那么我们应该创建对应的切点。这里我们就直接把上节课讲的添加用户复制过来作为我们的切点。

#### 1，创建对应的PO:

```java
package com.vgxit.learn.spring.ktdm.springaop.po;
 
import lombok.Data;
 
@Data
public class User {
    private Integer id;
    private String name;
    private Short gender;
}
```

#### 2，创建对应的切点：

```java
package com.vgxit.learn.spring.ktdm.springaop.service;
 
import com.vgxit.learn.spring.ktdm.springaop.po.User;
 
public interface IUserService {
    void add(User user);
}
```

```java
package com.vgxit.learn.spring.ktdm.springaop.service.impl;
 
import com.vgxit.learn.spring.ktdm.springaop.po.User;
import com.vgxit.learn.spring.ktdm.springaop.service.IUserService;
 
public class UserService implements IUserService {
    @Override
    public void add(User user) {
        System.out.println("添加用户[" + user + "]到数据库");
        throw new RuntimeException("添加错误");
    }
}
```

### 2，创建切面

选择好了切点之后，我们就可以创建切面了。切面就如同我们上节课写的拦截器。在spring中，我们只需要提供一个AspectJ注解，就可以让一个类成一个切面。但是如果我们想要使用这个注解，必须引入对应的依赖包：

```xml
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.9.6</version>
</dependency>
```

接下来我们创建对应的切面：

```java
package com.vgxit.learn.spring.ktdm.springaop.aspect;
 
import org.aspectj.lang.annotation.*;
 
@Aspect//使用了这个注解就表明该类为一个切面类
public class TranAspect {
    @Before("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..))")
    public void before() {
        System.out.println("获取数据库连接");
        System.out.println("开启事务");
    }
 
    @After("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..))")
    public void after() {
        System.out.println("对应逻辑执行完成");
    }
 
    @AfterReturning("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..))")
    public void afterReturning() {
        System.out.println("提交事物");
    }
 
    @AfterThrowing("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..))")
    public void afterThrowing() {
        System.out.println("事物回滚");
    }
}
```

上面我们使用了Aspect来定义对应的类是一个切面。然后我们使用了4个注解来定义对应的方法。这四个注解的含义如下：

1.@Before：在切点调用之前前置通知执行的方法。
2.@After:在切点调用之后后置通知执行的方法。
3.@AfterReturning：在被代理对象的方法正常返回之后调用
4.@AfterThrowing：在被代理对象的方法抛出异常之后调用

### 3，连接点
连接点在AOP中的作用其实就是用来判断是否要拦截对应的方法。比如我们上面的4个注解我们就可以理解成为连接点。

比如我们的@After("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..))")：
 	execution：代表执行方法的时候触发
 	*：代表方法可以是任意返回类型
 	com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService表示对应的方法提供者的全限定名 
 	add:表示被拦截的方法的名称
 	(..)：表示是任意类型的参数

### 4，测试运行

#### 1，首先应该创建一个配置类

```java
package com.vgxit.learn.spring.ktdm.springaop.config;
 
import com.vgxit.learn.spring.ktdm.springaop.aspect.TranAspect;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.EnableAspectJAutoProxy;
 
@ComponentScan("com.vgxit.learn.spring.ktdm.springaop")
@EnableAspectJAutoProxy//表示spring启动AspectJ框架自动代理
@Configuration
public class SpringAopConfig {
    //注入切面
    @Bean
    public TranAspect tranAspect() {
        return new TranAspect();
    }
}
```

#### 2，测试：

```java
package com.vgxit.learn.spring.ktdm.springaop.test;
 
import com.vgxit.learn.spring.ktdm.springaop.config.SpringAopConfig;
import com.vgxit.learn.spring.ktdm.springaop.po.User;
import com.vgxit.learn.spring.ktdm.springaop.service.IUserService;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
 
public class SpringaopTest001 {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(SpringAopConfig.class);
        IUserService userService = ctx.getBean(IUserService.class);
        User user = User.builder().id(1).name("李一桐").gender((short) 2).build();
        userService.add(user);
    }
}
```

### 5，简化连接点操作

我们上面写的这个切面是比较复杂的，每一个连接点我们都把自己的配置重复写了一遍，其实这个完全没有，我们可以简化。

```java
package com.vgxit.learn.spring.ktdm.springaop.aspect;
 
import org.aspectj.lang.annotation.*;
 
@Aspect//使用了这个注解就表明该类为一个切面类
public class TranAspect {
    @Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..))")
    public void tranPointer(){}
 
    @Before("tranPointer()")
    public void before() {
        System.out.println("获取数据库连接");
        System.out.println("开启事务");
    }
 
    @After("tranPointer()")
    public void after() {
        System.out.println("对应逻辑执行完成");
    }
 
    @AfterReturning("tranPointer()")
    public void afterReturning() {
        System.out.println("提交事物");
    }
 
    @AfterThrowing("tranPointer()")
    public void afterThrowing() {
        System.out.println("事物回滚");
    }
}
```

## 14，spring AOP 连接点指示器

### 1，概述
上节课我们讲了一下连接点，相信大家已经能够熟练的使用，并且老师告诉大家，在实际的开发中，我们基本上使用上面讲的连接点相关的知识就够了。但是AspectJ注解还给我们提供了更多的功能。

### 2，args()指示器：
限制连接点匹配参数为指定类型的方法。

比如我们把上节课的切面类改一下：

```java
@Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..)) && args(String)")
public void tranPointer(){}
```

这个改了之后aop不起作用了。这个是因为我们限定了必须切点方法的参数是String类型的。但是我们的切点方法的参数是User，所以我们的切面代码失效了。如果我们想要切面代码生效，我们可以用如下代码：

```java
@Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..)) && args(com.vgxit.learn.spring.ktdm.springaop.po.User)")
public void tranPointer(){}
```

### 3，@args()指示器：

限制连接点匹配参数对应的类型应该有对应的注解。

比如我们自定义一个注解。

```java
package com.vgxit.learn.spring.ktdm.springaop.anno;
 
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;
 
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
public @interface VgTest {
}
```

然后接下来我们定义连接点：

```java
@Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.UserService.add(..)) && @args(com.vgxit.learn.spring.ktdm.springaop.anno.VgTest)")
public void tranPointer(){}
```

接下来再来运行测试，我们发现切面代码又失效了。这个是因为我们的参数的类型必须要被VgTest注解修饰。但是现在没有任何修饰，所以说会失效。

```java
package com.vgxit.learn.spring.ktdm.springaop.po;
 
import com.vgxit.learn.spring.ktdm.springaop.anno.VgTest;
import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;
 
@Data
@Builder
@AllArgsConstructor
@NoArgsConstructor
@VgTest
public class User {
    private Integer id;
    private String name;
    private Short gender;
}
```

我们再重新加上VgTest的注解修饰，再来运行测试，发现切面代码又成功了。

### 4，this指示器

this指示器就是限定切入点所在类的类型是否和指定的类型相同。

首先，我们创建一个Role的PO:

```java
package com.vgxit.learn.spring.ktdm.springaop.po;
 
import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;
 
@Data
@Builder
@AllArgsConstructor
@NoArgsConstructor
public class Role {
    private Integer id;
    private String name;
    private Short gender;
}
```

接下来我们创建IRoleService和RoleService:

```java
package com.vgxit.learn.spring.ktdm.springaop.service;
 
import com.vgxit.learn.spring.ktdm.springaop.po.Role;
 
public interface IRoleService {
    void add(Role role);
}
```

```java
package com.vgxit.learn.spring.ktdm.springaop.service.impl;
 
import com.vgxit.learn.spring.ktdm.springaop.po.Role;
import com.vgxit.learn.spring.ktdm.springaop.service.IRoleService;
import org.springframework.stereotype.Component;
 
@Component
public class RoleService implements IRoleService {
    @Override
    public void add(Role role) {
        System.out.println("添加角色[" + role + "]到数据库");
    }
}
```

然后我们接下来运行测试代码，我们发现UserService和RoleService中的代码都被拦截了。而我们现在想要的方案是只有UserService被拦截，RoleService不被拦截，怎么办？这个时候我们直接修改切点：

```java
@Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.*.*(..)) && this(com.vgxit.learn.spring.ktdm.springaop.service.IUserService)")
public void tranPointer(){}
```

然后再运行，我们发现只有UserService被拦截，RoleService没有被拦截。

### 5，target指示器

target指示器的作用，就是限定切点所在类的类型是否和指定的相同。从字面以上来看，它和this()指示器似乎没有任何区别。那么我们实验一下看看：

```java
@Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.*.*(..)) && target(com.vgxit.learn.spring.ktdm.springaop.service.IUserService)")
public void tranPointer(){}
```

然后，我们再次运行程序。发现效果和this()一样。

### 6，@target指示器

限制连接点对应的类是否被某个注解修饰过。

1，首先，我们修改一下连接点：

```java
@Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.*.*(..)) && @target(com.vgxit.learn.spring.ktdm.springaop.anno.VgTest)")
public void tranPointer(){}
```

2，然后运行测试代码，我们发现只有被VgTest修饰过的类才会被拦截，其他的都不会。

### 7，within()指示器

within是指限制连接点对应的类是否属于某个包下面。我们修改一下连接点：

```java
@Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.*.*(..)) && within(com.vgxit.learn.spring.ktdm.springaop.service.impl.*)")
public void tranPointer(){}
```

### 8，@within()指示器

@within和@target的作用一样，都是限定匹配连接点所在类必须被某个注解修饰。

### 9，@annotation()指示器

@annotation()指示器用来限定连接点方法是否被某个注解修饰过。

## 15，Spring Aop环绕通知

### 1，概述
环绕通知是SpringAOP中最强大的通知，它可以实现前置通知和后置通知。它保留了调度被代理对象原有方法的功能，所以它强大又灵活。但是由于强大，它的可控制性不那么强，如果不需要大量改变业务逻辑 而言并不需要使用它。

环绕通知说白了，就是把我们之前的，前置通知，后置通知，正常返回通知，异常返回通知合并到一起。

### 2，具体实现

```java
package com.vgxit.learn.spring.ktdm.springaop.aspect;
 
import org.aspectj.lang.ProceedingJoinPoint;
import org.aspectj.lang.annotation.Around;
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Pointcut;
 
@Aspect
public class AroundAspect {
    @Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.*.*(..))")
    public void aroundPointer() {}
 
    @Around("aroundPointer()")
    public void around(ProceedingJoinPoint jp) {
        boolean hasException = false;
        System.out.println("环绕通知-获取数据库连接");
        System.out.println("环绕通知-开启事物");
        try {
            jp.proceed();//这段代码的意思，就是运行真正的切点方法
        } catch (Throwable throwable) {
            hasException = true;
        } finally {
            System.out.println("环绕通知-程序运行完成");
        }
        if (hasException) {
            System.out.println("环绕通知-程序异常");
        } else {
            System.out.println("环绕通知-程序正常");
        }
    }
}
```

我们再来把这个切面注入到ioc容器中，然后测试运行。

## 16，Spring 通知传递参数

### 1，概述

我们上面在执行切点方法的时候，我们可能会传入一些参数给对应的切点方法，比如我们UserService的add方法：

```java
package com.vgxit.learn.spring.ktdm.springaop.service.impl;
 
import com.vgxit.learn.spring.ktdm.springaop.po.User;
import com.vgxit.learn.spring.ktdm.springaop.service.IUserService;
import org.springframework.stereotype.Component;
 
@Component
public class UserService implements IUserService {
    @Override
    public void add(User user) {
        System.out.println("添加用户[" + user + "]到数据库");
    }
}
```

这个方法传入了一个User类型的参数。那么问一下同学们，如果我想要在对应的前置通知，后置通知....我们想要获取到这个User类型的参数怎么办？

### 2，具体操作

我们在前置，后置，正常返回，异常返回四个通知方法中，我们获取传入的参数。

1，我们修改一下我们的切面类

```java
package com.vgxit.learn.spring.ktdm.springaop.aspect;
 
import org.aspectj.lang.annotation.*;
 
@Aspect//使用了这个注解就表明该类为一个切面类
public class TranAspect {
    @Pointcut("execution(* com.vgxit.learn.spring.ktdm.springaop.service.impl.*.*(..)) && args(o)")
    public void tranPointer(Object o){}
 
    @Before("tranPointer(o)")
    public void before(Object o) {
        System.out.println("before:" + o);
        System.out.println("获取数据库连接");
        System.out.println("开启事务");
    }
 
    @After("tranPointer(o)")
    public void after(Object o) {
        System.out.println("after:" + o);
        System.out.println("对应逻辑执行完成");
    }
 
    @AfterReturning("tranPointer(o)")
    public void afterReturning(Object o) {
        System.out.println("afterReturning:" + o);
        System.out.println("提交事物");
    }
 
    @AfterThrowing("tranPointer(o)")
    public void afterThrowing(Object o) {
        System.out.println("afterThrowing:" + o);
        System.out.println("事物回滚");
    }
}
```

2，调用测试代码看效果

## 17，spring Aop XML方式实现

### 1，概述
之前我们使用了注解的方式来开发AOP，以后我们在工作中，更多的也是使用注解的方式来开发AOP，但是Spring也给我们提供了XML开发AOP的方式。我们接下来用我们之前做过的例子给大家举例。

### 2，前置，后置，正常返回和异常返回通知
#### 1，编写切点
创建切点，我们可以直接使用我们之前讲的IUserService和UserService

```java
package com.vgxit.learn.spring.ktdm.springxmlaop.serivce;

import com.vgxit.learn.spring.ktdm.springxmlaop.po.User;

public interface IUserService {
    void add(User user);
}
```

```java
package com.vgxit.learn.spring.ktdm.springxmlaop.serivce.impl;

import com.vgxit.learn.spring.ktdm.springxmlaop.po.User;
import com.vgxit.learn.spring.ktdm.springxmlaop.serivce.IUserService;

public class UserService implements IUserService {
    @Override
    public void add(User user) {
        System.out.println("添加用户[" + user + "]到数据库");
    }
}
```

#### 2，编写切面

```java
package com.vgxit.learn.spring.ktdm.springxmlaop.aspect;

public class TranAspect {
    public void before() {
        System.out.println("获取数据库连接");
        System.out.println("开启事务");
    }

    public void after() {
        System.out.println("对应逻辑执行完成");
    }

    public void afterReturning() {
        System.out.println("提交事物");
    }

    public void afterThrowing() {
        System.out.println("事物回滚");
    }
}
```

#### 3，编写spring的xml配置文件

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd
                           http://www.springframework.org/schema/aop
                           http://www.springframework.org/schema/aop/spring-aop.xsd">
    <!--这个配置也就和我们@EnableAspectJAutoProxy相同，都是开启自动动态代理-->
    <aop:aspectj-autoproxy/>
    <!--注入对应的切面和Service-->
    <bean id="tranAspect" class="com.vgxit.learn.spring.ktdm.springxmlaop.aspect.TranAspect"/>
    <bean id="userService" class="com.vgxit.learn.spring.ktdm.springxmlaop.serivce.impl.UserService"/>
    <!--aop配置-->
    <aop:config>
        <!--定义切面-->
        <aop:aspect ref="tranAspect">
            <!--定义切点-->
            <aop:pointcut id="action" expression="execution(* com.vgxit.learn.spring.ktdm.springxmlaop.serivce.impl.*.*(..))"/>
            <!--定义连接点-->
            <aop:before method="before" pointcut-ref="action"/>
            <aop:after method="after" pointcut-ref="action"/>
            <aop:after-returning method="afterReturning" pointcut-ref="action"/>
            <aop:after-throwing method="afterThrowing" pointcut-ref="action"/>
        </aop:aspect>
    </aop:config>
</beans>
```

#### 4，编写测试代码

```java
package com.vgxit.learn.spring.ktdm.springxmlaop.test;

import com.vgxit.learn.spring.ktdm.springxmlaop.po.User;
import com.vgxit.learn.spring.ktdm.springxmlaop.serivce.IUserService;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class SpringXmlAopTest001 {
    public static void main(String[] args) {
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
        IUserService userService = ctx.getBean(IUserService.class);
        User user = User.builder().id(1).name("李一桐").gender((short) 2).build();
        userService.add(user);
    }
}
```

### 3，环绕通知

#### 1，定义对应的切面

```java
package com.vgxit.learn.spring.ktdm.springxmlaop.aspect;

import org.aspectj.lang.ProceedingJoinPoint;

public class TranAspect {
    public void arround(ProceedingJoinPoint jp) {
        System.out.println("获取数据库连接");
        System.out.println("开启事务");
        boolean hasException = false;
        try {
            jp.proceed();//调用真实的切点方法
        } catch (Throwable throwable) {
            hasException = true;
        } finally {
            System.out.println("切点运行完成");
        }
        if (hasException) {
            System.out.println("异常返回");
        } else {
            System.out.println("正常返回");
        }
    }
}
```

#### 2，配置

```xml
<!--aop配置-->
    <aop:config>
        <!--定义切面-->
        <aop:aspect ref="tranAspect">
            <!--定义切点-->
            <aop:pointcut id="action" expression="execution(* com.vgxit.learn.spring.ktdm.springxmlaop.serivce.impl.*.*(..))"/>
            <!--定义连接点-->
            <aop:around method="arround" pointcut-ref="action"/>
        </aop:aspect>
    </aop:config>
```

### 4，通知传递参数

#### 1，编写对应的切面

```java
package com.vgxit.learn.spring.ktdm.springxmlaop.aspect;

import org.aspectj.lang.ProceedingJoinPoint;

public class TranAspect {
    public void before(Object o) {
        System.out.println(o);
        System.out.println("开始。。。。。");
    }
}
```

#### 2，编写对应的配置

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd
                           http://www.springframework.org/schema/aop
                           http://www.springframework.org/schema/aop/spring-aop.xsd">
    <!--这个配置也就和我们@EnableAspectJAutoProxy相同，都是开启自动动态代理-->
    <aop:aspectj-autoproxy/>
    <!--注入对应的切面和Service-->
    <bean id="tranAspect" class="com.vgxit.learn.spring.ktdm.springxmlaop.aspect.TranAspect"/>
    <bean id="userService" class="com.vgxit.learn.spring.ktdm.springxmlaop.serivce.impl.UserService"/>
    <!--aop配置-->
    <aop:config>
        <!--定义切面-->
        <aop:aspect ref="tranAspect">
            <!--定义切点-->
            <aop:pointcut id="action" expression="execution(* com.vgxit.learn.spring.ktdm.springxmlaop.serivce.impl.*.*(..)) and args(o)"/>
            <!--定义连接点-->
            <aop:before method="before" pointcut-ref="action"/>
        </aop:aspect>
    </aop:config>
</beans>
```

## 18，Spring 数据库编程

### 1，概述：
Spring最重要的功能毫无疑问就是操作数据。在Java互联网项目中，数据大部分存储在数据库和NoSQL工具中，我们接下来就要接触到基于Spring的数据库编程。数据库的编程是互联网编程的基础，Spring为开发者提供了JDBC模板模式，那就是它自身的jdbcTemplate，它可以简化许多代码的编程，但是在实际的工作中jdbcTemplate并不常用。Spring还提供了基于TransactionTemplate的支持事务的模板。只不过这些都不是常用技术。对于持久层，我们在开发的时候更多的是使用Mybatis或者Hibernate这样的技术。对于Hibernate的话，Spring提供了HibernateTemplate给与支持，它可以简化对于Hibernate的编程。对于Mybatis框架，由于版本原因，Spring并没有支持Mybatis，好在Mybatis社区开发了介入Spring的开发包，该包也提供了SqlSessionTemplate给开发者使用。更让人欣喜的是该包还屏蔽了SqlSessionTemplate这种功能性的代码。让开发者在开发的时候可以擦除SqlSessionTemplate让开发者直接使用Mapper接口编程，大大提高了编码的可读性。

### 2，传统的JDBC代码的弊端：

传统的jdbc代码，是非常有弊端的。比如如下代码：

```java
public class ConnMysqlTest {
    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //1,加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2，获取数据库连接,通过DriverManager
        //连接的地址，书写格式 jdbc:数据库驱动类型://ip:端口/数据库名?serverTimezone=时区[&useUnicode=true&characterEncoding=utf8]
        //如果使用utf8编码用如下方式
        String connUrl = "jdbc:mysql://localhost:3306/vgxit_test?serverTimezone=Asia/Shanghai";
        //4,编写查询语句
        String selectSql = "select id, name, gender, age, phone from user;";
        try (
                Connection connection = DriverManager.getConnection(connUrl, "root", "Abc@123456");
                //3,使用Connection来创建一个Statement对象
                Statement statement = connection.createStatement();
                //5,执行对应的sql，获取到一个ResultSet
                ResultSet rs = statement.executeQuery(selectSql);
                ) {
            //遍历查询出来的数据
            while (rs.next()) {
                System.out.println(rs.getInt(1) + ":" + rs.getString(2) + "," + rs.getShort(3) + "," + rs.getInt(4) + "," + rs.getString(5));
            }
        }
    }
}
```

这段代码是老师第一次给同学们讲Jdbc的时候给大家写的代码，我是原样的复制过来的。同学们可以看到使用jdbc编程，就算是一条sql，其实也不是太简单。因为我们要考虑打开数据库连接，然后执行sql，然后遍历结果集，然后封装数据，然后关闭Statement，ResultSet，Connection。其实我们就是想要简单的写一条sql来查询数据而已。上面的代码对于我们来说真的是太复杂了。
当然如果我们使用原生的Jdbc编程，效率肯定是最好的。但是我们有太多的逻辑和异常处理等需要我们编码，这个时候其实我们再这么使用在大项目中肯定是不行的。而Spring就可以为我们大大的简化数据库的开发。

## 19，Spring整合JdbcTemplate

### 1，概述
我们之前之前也开发过做过很多JDBC查询数据库相关代码。我们可以看到。使用JDBC开发程序，我们是非常痛苦的。因为我们要经历创建连接，获取PreparedStatement，获取ResultSet，组装数据等各种一系列的问题。非常的麻烦。而Spring为我们提供的JdbcTemplate就为我们很好的提供了这一方式。但是V哥给大家说一下，这种JdbcTemplate的数据库编程的方式，在真的线上开发的时候，很少使用。大家还是喜欢使用mybatis，hibernate（jpa）这样的一些框架。

### 2，配置整合
#### 1，引入对应的jar包：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>spring.ktdm</artifactId>
        <groupId>com.vgxit.learn</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.vgxit.learn.spring.ktdm</groupId>
    <artifactId>jdbctemplate</artifactId>
    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>
        <!--mysq驱动包-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
        <!--引入jdbc驱动包-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
        </dependency>
        <!--引入对应的数据库连接池-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
        </dependency>
    </dependencies>
</project>
```

#### 2，配置对应的数据源，datasource.properties:

```properties
datasource.class=com.alibaba.druid.pool.DruidDataSource
datasource.url=jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai
datasource.username=root
datasource.password=Abc@123456
datasource.initalSize=5
datasource.minIdel=5
maxActive=20
maxWait=3000
```

#### 3，定义spring的配置文件，spring-cfg.xml，然后我们配置数据源和JdbcTemplate:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd">
    <!--加载数据源配置文件-->
    <context:property-placeholder location="classpath:datasource.properties"/>
    <!--注入数据源-->
    <bean id="datasource" class="${datasource.class}">
        <property name="driverClassName" value="${datasource.driver}"/>
        <property name="url" value="${datasource.url}"/>
        <property name="username" value="${datasource.username}"/>
        <property name="password" value="${datasource.password}"/>
        <property name="initialSize" value="${datasource.initalSize}"/>
        <property name="minIdle" value="${datasource.minIdel}"/>
        <property name="maxActive" value="${datasource.maxActive}"/>
        <property name="maxWait" value="${datasource.maxWait}"/>
    </bean>
    <!--注入JdbcTemplate-->
    <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
        <property name="dataSource" ref="datasource"/>
    </bean>
</beans>
```

#### 4，测试运行：

```java
package com.vgxit.learn.spring.ktdm.jdbctemplate.test;

import com.vgxit.learn.spring.ktdm.jdbctemplate.po.User;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.jdbc.core.RowMapper;
import java.sql.ResultSet;
import java.sql.SQLException;

public class JdbcTemplate001 {
    /**
     * 测试用JdbcTemplate查询数据
     */
    private static void testSelect() {
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
        String sql = "select * from user where id=1";
        JdbcTemplate jdbcTemplate = ctx.getBean(JdbcTemplate.class);
        //查询用户
        User user = jdbcTemplate.queryForObject(sql, new RowMapper<User>() {
            /**
             * 该方法会在数据库返回了查询结果之后调用，其作用就是返回数据库查询之后组装的数据
             * @param resultSet 结果集
             * @param i
             * @return 封装的结果集
             * @throws SQLException
             */
            @Override
            public User mapRow(ResultSet resultSet, int i) throws SQLException {
                User user = User.builder()
                        .id(resultSet.getInt("id"))
                        .name(resultSet.getString("name"))
                        .gender(resultSet.getShort("gender"))
                        .age(resultSet.getInt("age"))
                        .nickName(resultSet.getString("nick_name"))
                        .build();
                return user;
            }
        });
        System.out.println(user);
    }

    private static void testUpdate() {
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
        String sql = "update user set name=? where id=?";
        JdbcTemplate jdbcTemplate = ctx.getBean(JdbcTemplate.class);
        //添加和删除的时候也是调用update方法
        jdbcTemplate.update(sql, "李一桐", 1);
    }

    public static void main(String[] args) {
//        testUpdate();
        testSelect();
    }
}
```

## 20，Spring整合Mybatis

### 1，概述
现在大部分的Java互联网项目，都是使用SpringMvc + Spring + Mybatis来搭建的。但是Spring官方并没有为我们提供整合Mybatis相关的方案。不过还好的是Mybatis社区为我们开发了Mybatis-Spring项目，可以用来实现Mybatis和Spring的整合。
那么我们要整合Mybatis，首先我们需要引入对应的Jar包：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>spring.ktdm</artifactId>
        <groupId>com.vgxit.learn</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.vgxit.learn.spring.ktdm</groupId>
    <artifactId>ms</artifactId>
    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>
        <!--mysq驱动包-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
        <!--引入jdbc驱动包-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
        </dependency>
        <!--引入对应的数据库连接池-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
        </dependency>
        <!--引入logback需要的jar包-->
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-api</artifactId>
        </dependency>
        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-classic</artifactId>
        </dependency>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
        </dependency>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
        </dependency>
    </dependencies>
    <build>
        <finalName>${artifactId}.jar</finalName>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*</include>
                </includes>
            </resource>
        </resources>
    </build>
</project>
```

### 2，SqlSessionFactoryBean
从Mybatis的介绍中，可以知道SqlSessionFactory是产生SqlSession的基础，因此配置SqlSessionFactory十分关键。在Mybatis-Spring项目中提供了SqlSessionFactoryBean去支持SqlSessionFactory的配置。我们先看看对应的源码：

```java
public class SqlSessionFactoryBean
    implements FactoryBean<SqlSessionFactory>, InitializingBean, ApplicationListener<ApplicationEvent> {

  private static final Logger LOGGER = LoggerFactory.getLogger(SqlSessionFactoryBean.class);

  private static final ResourcePatternResolver RESOURCE_PATTERN_RESOLVER = new PathMatchingResourcePatternResolver();
  private static final MetadataReaderFactory METADATA_READER_FACTORY = new CachingMetadataReaderFactory();

  private Resource configLocation;

  private Configuration configuration;

  private Resource[] mapperLocations;

  private DataSource dataSource;

  private TransactionFactory transactionFactory;

  private Properties configurationProperties;

  private SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();

  private SqlSessionFactory sqlSessionFactory;

  // EnvironmentAware requires spring 3.1
  private String environment = SqlSessionFactoryBean.class.getSimpleName();

  private boolean failFast;

  private Interceptor[] plugins;

  private TypeHandler<?>[] typeHandlers;

  private String typeHandlersPackage;

  @SuppressWarnings("rawtypes")
  private Class<? extends TypeHandler> defaultEnumTypeHandler;

  private Class<?>[] typeAliases;

  private String typeAliasesPackage;

  private Class<?> typeAliasesSuperType;

  private LanguageDriver[] scriptingLanguageDrivers;

  private Class<? extends LanguageDriver> defaultScriptingLanguageDriver;

  // issue #19. No default provider.
  private DatabaseIdProvider databaseIdProvider;

  private Class<? extends VFS> vfs;

  private Cache cache;

  private ObjectFactory objectFactory;

  private ObjectWrapperFactory objectWrapperFactory;
  }
```

从上面的源码中，我们可以看到这个类几乎可以配置Mybatis所有的组件，并且提供了setter方法让我spring来设置。所以我们完全可以通过spring ioc容器来配置。

### 3，基于SqlSessionTemplate组件的配置方式：

#### 1，首先应该配置mybatis的配置文件, mybatis-config.xml：

```java
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <settings>
        <!--配置运行的sql在控制台打印输出-->
        <setting name="logImpl" value="STDOUT_LOGGING"/>
        <!--开启驼峰映射-->
        <setting name="mapUnderscoreToCamelCase" value="true"/>
        <!--全局设置主键自动回填-->
        <setting name="useGeneratedKeys" value="true"/>
        <!--配置默认的执行器，SIMPLE会直接执行sql没有什么特别的。REUSE会重用预处理器，也就是会重用同一个Sql的Statement。BATCH 通过批量操作来优化性能-->
        <setting name="defaultExecutorType" value="REUSE"/>
        <!--开启延迟加载-->
        <setting name="lazyLoadingEnabled" value="true"/>
        <!--设置超时时间，就是sql执行的超时时间，单位秒-->
        <setting name="defaultStatementTimeout" value="120"/>
    </settings>
    <!--配置别名-->
    <typeAliases>
        <package name="com.vgxit.learn.spring.ktdm.ms.po"/>
    </typeAliases>
    <!--配置映射器-->
    <mappers>
        <package name="com.vgxit.learn.spring.ktdm.ms.mapper"/>
    </mappers>
</configuration>
```

#### 2，编写对应的PO:

```java
package com.vgxit.learn.spring.ktdm.ms.po;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;

@Data
@Builder
@AllArgsConstructor
@NoArgsConstructor
public class User {
    private Integer id;
    private String name;
    private Integer age;
    private Short gender;
    private String nickName;
}
```

#### 3，创建Mapper:

```java
package com.vgxit.learn.spring.ktdm.ms.mapper;

import com.vgxit.learn.spring.ktdm.ms.po.User;
import org.apache.ibatis.annotations.Param;

public interface UserMapper {
    User getById(@Param("id") int id);
}
```

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <settings>
        <!--配置运行的sql在控制台打印输出-->
        <setting name="logImpl" value="STDOUT_LOGGING"/>
        <!--开启驼峰映射-->
        <setting name="mapUnderscoreToCamelCase" value="true"/>
        <!--全局设置主键自动回填-->
        <setting name="useGeneratedKeys" value="true"/>
        <!--配置默认的执行器，SIMPLE会直接执行sql没有什么特别的。REUSE会重用预处理器，也就是会重用同一个Sql的Statement。BATCH 通过批量操作来优化性能-->
        <setting name="defaultExecutorType" value="REUSE"/>
        <!--开启延迟加载-->
        <setting name="lazyLoadingEnabled" value="true"/>
        <!--设置超时时间，就是sql执行的超时时间，单位秒-->
        <setting name="defaultStatementTimeout" value="120"/>
    </settings>
    <!--配置别名-->
    <typeAliases>
        <package name="com.vgxit.learn.spring.ktdm.ms.po"/>
    </typeAliases>
    <!--配置映射器-->
    <mappers>
        <package name="com.vgxit.learn.spring.ktdm.ms.mapper"/>
    </mappers>
</configuration>
```

#### 4，对应一下logback日志输出，便于我们之后看效果：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="logback.xsd"
        scan="true"
        scanPeriod="60 seconds"
        debug="false">
    <property name="log.pattern" value="%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{100} %msg%n"/>
    <appender name="consoleAppender" class="ch.qos.logback.core.ConsoleAppender">
        <!--appender其实是负责统一调度日志的输出工作，而具体的日志的格式化工作和输出的工作会交给encoder-->
        <encoder>
            <!--定义日志输出的格式-->
            <pattern>${log.pattern}</pattern>
        </encoder>
    </appender>
    <root level="DEBUG">
        <appender-ref ref="consoleAppender"/>
    </root>
</configuration>
```

#### 5，配置数据源：

```properties
datasource.class=com.alibaba.druid.pool.DruidDataSource
datasource.driver=com.mysql.cj.jdbc.Driver
datasource.url=jdbc:mysql://localhost:3306/mybatis.ktdm?serverTimezone=Asia/Shanghai
datasource.username=root
datasource.password=Abc@123456
datasource.initalSize=5
datasource.minIdel=5
datasource.maxActive=20
datasource.maxWait=3000
```

#### 6，定义spring的配置文件：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd">
    <!--加载数据源配置文件-->
    <context:property-placeholder location="classpath:datasource.properties"/>
    <!--注入数据源-->
    <bean id="datasource" class="${datasource.class}">
        <property name="driverClassName" value="${datasource.driver}"/>
        <property name="url" value="${datasource.url}"/>
        <property name="username" value="${datasource.username}"/>
        <property name="password" value="${datasource.password}"/>
        <property name="initialSize" value="${datasource.initalSize}"/>
        <property name="minIdle" value="${datasource.minIdel}"/>
        <property name="maxActive" value="${datasource.maxActive}"/>
        <property name="maxWait" value="${datasource.maxWait}"/>
    </bean>
    <!--配置SqlSessionFactoryBean-->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <property name="dataSource" ref="datasource"/>
        <!--指定mybatis的配置文件-->
        <property name="configLocation" value="classpath:mybatis-config.xml"/>
    </bean>
    <!--注入SqlSessionTemplate-->
    <bean id="sqlSessionTemplate" class="org.mybatis.spring.SqlSessionTemplate">
        <constructor-arg ref="sqlSessionFactory"/>
    </bean>
</beans>
```

#### 7，测试代码：

```java
package com.vgxit.learn.spring.ktdm.ms.test;

import com.vgxit.learn.spring.ktdm.ms.po.User;
import org.mybatis.spring.SqlSessionTemplate;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class MybatisSpringTest001 {
    private static void testSelect() {
        ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
        SqlSessionTemplate sqlSessionTemplate = ctx.getBean(SqlSessionTemplate.class);
        User user = sqlSessionTemplate.selectOne("com.vgxit.learn.spring.ktdm.ms.mapper.UserMapper.getById", 1);
        System.out.println(user);
    }


    public static void main(String[] args) {
        testSelect();
    }
}
```

### 4，基于MapperFactoryBean的整合：
我们使用上面的SqlSessionTemplate的方式整合，还是非常的不方便。我们之前学习Mybatis我们知道，要运行对应的sql我们只需要拿到对应的Mapper就好了。
我们通过Mybatis的学习，我们知道，Mybatis创建Mapper是通过动态代理来创建了一个Mapper的代理对象。但是Spring肯定是么有办法为我们创建这个代理对象。但是Mybatis-spring项目为我们一同了一个MypperFactoryBean类作为中介，我们可以通过配置这个类来实现我们想要的Mapper的代理对象。

```xml
<!--配置对应的Mapper-->
<bean id="userMapper" class="org.mybatis.spring.mapper.MapperFactoryBean">
    <property name="mapperInterface" value="com.vgxit.learn.spring.ktdm.ms.mapper.UserMapper"/>
    <property name="sqlSessionFactory" ref="sqlSessionFactory"/>
    <!--我们配置和SqlSession相关的我们只需要配置SqlSessionFacotry或者sqlSessionTemplate，但是如果我们两个都配置上了，那么只有sqlSessionTemplate生效-->
    <!--        <property name="sqlSessionTemplate" ref="sqlSessionTemplate"/>-->
</bean>
```

对应的测试代码如下：

```java
ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
UserMapper userMapper = ctx.getBean(UserMapper.class);
User user = userMapper.getById(1);
System.out.println(user);
```

### 5，基于注解的整合（推荐1）：
上面我们通过MapperFacotryBean的方式来整合Mybatis，我们还是觉得比较麻烦，以为我们每次写一个Mapper，就需要在Xml中配置一下。那么接下来V哥给大家介绍一种更方便的方式。就是基于注解的方式。我们的思路，就是配置一个扫描器，它能够自动的扫描这些Mapper然后注入到SpringIoc容器中。

#### 1，首先我们注入一个MapperScannerConfigurer:

```xml
<!--配置了Mapper的扫描器-->
<bean id="mapperScannerConfigurer" class="org.mybatis.spring.mapper.MapperScannerConfigurer">
    <!--定义Mapper所在包-->
    <property name="basePackage" value="com.vgxit.learn.spring.ktdm.ms.mapper"/>
    <!--定义SqlSessionFacotry的名字-->
    <property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/>
    <!--指定对标注了某个注解的Mapper我们要注入-->
    <property name="annotationClass" value="org.springframework.stereotype.Repository"/>
</bean>
```

#### 2，然后给对应的Mapper加上注解：

```java
package com.vgxit.learn.spring.ktdm.ms.mapper;

import com.vgxit.learn.spring.ktdm.ms.po.User;
import org.apache.ibatis.annotations.Param;
import org.springframework.stereotype.Repository;

@Repository
public interface UserMapper {
    User getById(@Param("id") int id);
}
```

#### 3，测试运行：

```java
ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
UserMapper userMapper = ctx.getBean(UserMapper.class);
User user = userMapper.getById(1);
System.out.println(user);
```

### 6，基于标注的整合（推荐2）：

这种方法的思想和我们上面注解的思想相同，只不过这种方式定义了一个父接口，然后让所有的Mapper继承这个接口，然后扫描的时候，如果这个Mapper是这个接口的子接口，那么SpringIoc会注入其代理对象。

#### 1，首先创建一个BaseMapper:

```java
package com.vgxit.learn.spring.ktdm.ms.base;

public interface BaseMapper {
}
```

#### 2，然后让对应的Mapper来继承这个Mapper，并且干掉@Repository注解：

```java
package com.vgxit.learn.spring.ktdm.ms.mapper;

import com.vgxit.learn.spring.ktdm.ms.base.BaseMapper;
import com.vgxit.learn.spring.ktdm.ms.po.User;
import org.apache.ibatis.annotations.Param;

public interface UserMapper extends BaseMapper {
    User getById(@Param("id") int id);
}
```

#### 3，配置对应的mapperScannerConfigurer:

```xml
<!--配置了Mapper的扫描器-->
<bean id="mapperScannerConfigurer" class="org.mybatis.spring.mapper.MapperScannerConfigurer">
    <!--定义Mapper所在包-->
    <property name="basePackage" value="com.vgxit.learn.spring.ktdm.ms.mapper"/>
    <!--定义SqlSessionFacotry的名字-->
    <property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/>
    <property name="markerInterface" value="com.vgxit.learn.spring.ktdm.ms.base.BaseMapper"/>
</bean>
```

## 21，Spring整合Mybatis纯注解方式

### 1，定义Spring配置类：

```java
package com.vgxit.learn.spring.mybatis.bk.config;

import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan("com.vgxit.learn.spring.mybatis.bk")
public class ApplicationConfig {
}
```

### 2，定义Mybatis配置类：

```java
package com.vgxit.learn.spring.mybatis.bk.config;

import com.alibaba.druid.pool.DruidDataSourceFactory;
import com.vgxit.learn.spring.mybatis.bk.mapper.BaseMapper;
import org.mybatis.spring.SqlSessionFactoryBean;
import org.mybatis.spring.mapper.MapperScannerConfigurer;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.io.ClassPathResource;
import org.springframework.core.io.Resource;
import javax.sql.DataSource;
import java.io.InputStream;
import java.util.Properties;

@Configuration
public class MybatisConfig {
    @Bean
    public DataSource dataSource() throws Exception {
        Properties properties = new Properties();
        InputStream druidInputStream = MybatisConfig.class.getClassLoader().getResourceAsStream("datasource.properties");
        properties.load(druidInputStream);
        DataSource ds = DruidDataSourceFactory.createDataSource(properties);
        return ds;
    }

    @Bean("sqlSessionFactory")
    public SqlSessionFactoryBean sqlSessionFactoryBean() throws Exception {
        SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
        sqlSessionFactoryBean.setDataSource(dataSource());
        Resource resource = new ClassPathResource("mybatis-config.xml");
        sqlSessionFactoryBean.setConfigLocation(resource);
        return sqlSessionFactoryBean;
    }

    @Bean
    public MapperScannerConfigurer mapperScannerConfigurer() {
        MapperScannerConfigurer mapperScannerConfigurer = new MapperScannerConfigurer();
        mapperScannerConfigurer.setBasePackage("com.vgxit.learn.spring.mybatis.bk.mapper");
        mapperScannerConfigurer.setSqlSessionFactoryBeanName("sqlSessionFactory");
        mapperScannerConfigurer.setMarkerInterface(BaseMapper.class);
        return mapperScannerConfigurer;
    }
}
```

### 3，具体测试代码：

```java
private static void testAnnoSelect() {
    ApplicationContext ctx = new AnnotationConfigApplicationContext(ApplicationConfig.class);
    UserMapper userMapper = ctx.getBean(UserMapper.class);
    User user = userMapper.getById(1);
    System.out.println(user);
}

public static void main(String[] args) {
    testAnnoSelect();
}
```

## 22，Spring编程式事物

### 1，概述
之前我们已经使用了Spring来整合JdbcTemplate和Mybatis。但是我们并没有配置事务，我们知道在互联网开发项目中，数据库事务的配置是非常重要的。那么接下来我们就要来学习Spring的事物管理。

### 2，Spring数据库事务管理器设计思路
在Spring中，数据库事务通过PlatformTransactionManager进行管理。然后，Spring再给我们提供了一个支持事务的模板TransactionTemplate。我们可以看看TransactionTemplate的源码，其中核心的就是execute方法：

```java
private PlatformTransactionManager transactionManager;

public <T> T execute(TransactionCallback<T> action) throws TransactionException {
   Assert.state(this.transactionManager != null, "No PlatformTransactionManager set");

   if (this.transactionManager instanceof CallbackPreferringPlatformTransactionManager) {
      return ((CallbackPreferringPlatformTransactionManager) this.transactionManager).execute(this, action);
   }
   else {
      TransactionStatus status = this.transactionManager.getTransaction(this);
      T result;
      try {
         result = action.doInTransaction(status);
      }
      catch (RuntimeException | Error ex) {
         // Transactional code threw application exception -> rollback
         rollbackOnException(status, ex);
         throw ex;
      }
      catch (Throwable ex) {
         // Transactional code threw unexpected exception -> rollback
         rollbackOnException(status, ex);
         throw new UndeclaredThrowableException(ex, "TransactionCallback threw undeclared checked exception");
      }
      this.transactionManager.commit(status);
      return result;
   }
}
```

从上面源码中，我们可以看到，对应的流程如下：

- 事务的创建，提交和回滚是通过PlatformTransactionManager接口完成的
- 当事务产生异常时会回滚事务，在默认的实现中所有的异常都会回滚。我们可以通过配置去修改在某些异常发生时不会滚事务
- 当没有异常的时候提交事务

### 3，事物配置：

```xml
<!--注入事务管理器-->
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
    <property name="dataSource" ref="datasource"/>
</bean>
```

### 4，编程式事物

编程式事务以代码的方式管理事物，换句话说，事物将由开发者通过自己的代码实现。这里需要使用一个事物定义接口：TransactionDefinition。

```java
private static void testInsert() {
    ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
    UserMapper userMapper = ctx.getBean(UserMapper.class);
    //创建一个事物定义类
    TransactionDefinition transactionDefinition = new DefaultTransactionDefinition();
    //获取事物的秒数对象,也就是我们的事物管理器
    PlatformTransactionManager transactionManager = ctx.getBean(PlatformTransactionManager.class);
    //获取事物的状态
    TransactionStatus transactionStatus = transactionManager.getTransaction(transactionDefinition);
    try {
        User user = User.builder().name("猪八戒").gender((short) 1).age(500).nickName("八戒").build();
        userMapper.add(user);
        //            int a = 1 / 0;
        //手动提交事物
        transactionManager.commit(transactionStatus);
    } catch (Throwable throwable) {
        throwable.printStackTrace();
        //手动回滚事务
        transactionManager.rollback(transactionStatus);
    }
}
```

## 23，Spring 声明式事物

### 1，概述
声明式式事物是一种约定性的事物，在大部分情况下，当数据库使用事物的时候。一般我们都是发生了异常就需要事物回滚，如果没有繁盛异常，那么久提交事物。从这一点出发，Spring给了我们一个约定，就是没有异常提交事物，有异常回滚事务。通过这种思想，为我们提供了声明式事物。

### 2，具体实现：
我们这里要实现必须通过一个注解@Transactional。被这个注解修饰的方法就自动的会按照Spring给我们的约定管理起了事务。

#### 1，我们首先在xml中开启申明式事务：

```xml
<tx:annotation-driven transaction-manager="transactionManager"/>
```

#### 2，编写对应的业务逻辑代码：

```java
package com.vgxit.learn.springtransaction.bk;

import lombok.Getter;
import lombok.Setter;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.transaction.annotation.Transactional;

@Getter
@Setter
@Transactional
public class User1Service {
    private JdbcTemplate jdbcTemplate;

    public void updateUser() {
        jdbcTemplate.update("update user set name=? where id=?", "111111", 31);
        throw new RuntimeException();
    }
}
```

#### 3，编写对应的测试代码：

```java
private static void testShenmingTransaction() {
    ApplicationContext ctx = new ClassPathXmlApplicationContext("spring-cfg.xml");
    User1Service user1Service = ctx.getBean(User1Service.class);
    user1Service.updateUser();
}
```

4，我们的Transactional注解，可以配置在类上，也可以配置在方法上，配置在类上，所有的类的public方法都会起作用，如果作用在方法上，对应的方法起作用

### 3，纯注解的方式实现申明式事物

#### 1，定义配置类：

```java
package com.vgxit.learn.spring.ktdm.trananno.config;

import com.alibaba.druid.pool.DruidDataSourceFactory;
import com.vgxit.learn.spring.ktdm.trananno.base.BaseMapper;
import org.mybatis.spring.SqlSessionFactoryBean;
import org.mybatis.spring.mapper.MapperScannerConfigurer;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.io.ClassPathResource;
import org.springframework.core.io.Resource;
import org.springframework.jdbc.datasource.DataSourceTransactionManager;
import org.springframework.transaction.TransactionManager;
import org.springframework.transaction.annotation.EnableTransactionManagement;

import javax.sql.DataSource;
import java.io.InputStream;
import java.util.Properties;

@Configuration
@ComponentScan("com.vgxit.learn.spring.ktdm.trananno")
@EnableTransactionManagement//启用申明式事物
public class TranannoConfig {
    @Bean
    public DataSource dataSource() throws Exception {
        Properties properties = new Properties();
        InputStream druidInputStream = TranannoConfig.class.getClassLoader().getResourceAsStream("datasource.properties");
        properties.load(druidInputStream);
        DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);
        return dataSource;
    }

    @Bean("sqlSessionFactoryBean")
    public SqlSessionFactoryBean sqlSessionFactoryBean(@Autowired DataSource dataSource) throws Exception {
        SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
        sqlSessionFactoryBean.setDataSource(dataSource);
        Resource resource = new ClassPathResource("mybatis-config.xml");
        sqlSessionFactoryBean.setConfigLocation(resource);
        return sqlSessionFactoryBean;
    }

    @Bean
    public MapperScannerConfigurer mapperScannerConfigurer() {
        MapperScannerConfigurer mapperScannerConfigurer = new MapperScannerConfigurer();
        mapperScannerConfigurer.setBasePackage("com.vgxit.learn.spring.ktdm.trananno.mapper");
        mapperScannerConfigurer.setSqlSessionFactoryBeanName("sqlSessionFactoryBean");
        mapperScannerConfigurer.setMarkerInterface(BaseMapper.class);
        return mapperScannerConfigurer;
    }

    @Bean
    public TransactionManager transactionManager(@Autowired DataSource dataSource) throws Exception {
        DataSourceTransactionManager transactionManager = new DataSourceTransactionManager();
        transactionManager.setDataSource(dataSource);
        return transactionManager;
    }
}
```

#### 2，定义对应的UserService:

```java
package com.vgxit.learn.spring.ktdm.trananno.service;

import com.vgxit.learn.spring.ktdm.trananno.mapper.UserMapper;
import com.vgxit.learn.spring.ktdm.trananno.po.User;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
import org.springframework.transaction.annotation.Transactional;

@Component
public class UserService {
    @Autowired
    private UserMapper userMapper;

    @Transactional
    public void add(User user) {
        userMapper.add(user);
//        int x = 1 / 0;
    }
}
```

#### 3，具体的注入方法：

```java
package com.vgxit.learn.spring.ktdm.trananno.test;

import com.vgxit.learn.spring.ktdm.trananno.config.TranannoConfig;
import com.vgxit.learn.spring.ktdm.trananno.po.User;
import com.vgxit.learn.spring.ktdm.trananno.service.UserService;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class TranannoTest001 {
    public static void main(String[] args) {
        ApplicationContext ctx = new AnnotationConfigApplicationContext(TranannoConfig.class);
        UserService userService = ctx.getBean(UserService.class);
        User user = User.builder().name("沙悟净").age(550).gender((short) 1).nickName("卷帘大将").build();
        userService.add(user);
    }
}
```

## 24，Spring Transactionl注解详解

### 1，概述

在我们真正的编程开发中，大部分情况下，我们都是使用的Transactionl注解来进行声明式事务开发的。所以，这个注解非常的重要，这里我们单独拿出来讲一讲。

### 2，事务超时时间

#### 1,我们在定义@Transactionl注解的时候，加上超时时间的属性：

```java
@Transactional(timeout = 5)
```

#### 2,对应的业务代码：

```java
public void updateUser() {
    try {
        Thread.sleep(6000);
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
    jdbcTemplate.update("update user set name=? where id=?", "55555", 31);
}
```

### 3，只读事务
从字面上的意思来看，只读事物就是只能进行读操作的事务。那有的同学就很奇怪了。我们事务不是保证数据库操作的一致性吗？按理说，这个应该是写操作的事情，现在，为什么读操作也要加事物呢？这里用如下场景举例：
如果你一次执行单条查询语句，则没有必要启用事务支持，数据库默认支持SQL执行期间的读一致性；
如果你一次执行多条查询语句，例如统计查询，报表查询，在这种场景下，多条查询SQL必须保证整体的读一致性，否则，在前条SQL查询之后，后面再发送一条SQL查询之前，数据被其他用户改变，则该次整体的统计查询将会出现读数据不一致的状态，此时，应该启用事务支持。
那么为什么启用了事物支持之后，就能够保证在一次事务里面多次查询读出来的数据是一样的呢？这里我们复习一下我们之前学习Mysql讲的知识。下面我们引入了mysql入门课程中的课堂笔记：

> 多个事务之间是相互独立的。但是如果多个事务操作同一批数据，则会引发一些问题。设置不同的隔离级别，就可以解决这些问题了。 存在的问题：
> 1，脏读：一个事务读取到另外一个事务中没有提交的数据。
> 2，不可重复读：在同一个事务中，两次读取到的数据不一样。
> 3，幻读：一个事务去操作数据表中所有的记录，另一个事务添加了一条数据，则第一个事务查询不到自己的修改。这个问题mysql不存在，无法演示。
> Mysql中的隔离级别：
> 1，read uncommitted: 读取未提交的数据，会产生脏读，不可重复度和幻读都会发生
> 2，read committed: 读取已提交的内容，会产生不可重复读和幻读
> 3，repeatable read:可重复读，会产生幻读
> 4，serializable: 串行化，可以解决所有的问题。
> 有的同学就会问老师，既然serializable可以解决所有的问题，那我们为什么不直接把隔离级别设置成serializable，为什么我们还要学习这个隔离级别呢？
> 隔离级别从小到大，安全性是越来越高，但是效率是越来越低。Mysql中默认的隔离级别是：repeatable read。

从上面的笔记中我们可以看到在mysql中默认的事物隔离级别是repeatable read。这个可以防止出现不可重复读。如果我们开启了事物，就可以保证的多次读取数据的一致性。
最佳实践：我们如果项目并发不大，对性能要求不高的情况下，我们可以直接在对应的业务Service的方法上直接写上一个@Transactional注解。但是如果我们项目是大项目并发很大，大家为了优化性能，老师建议大家吧@Transactionl注解写到方法上，并且在只有读操作的方法上注解加上readOnly属性为true。

```java
@Transactional(readOnly = true)
public void getUserById(int id) {
}
```

**具体操作**

#### 1，首先我们在UserMapper中再加一个方法，代码和getById一样：

```java
public interface UserMapper extends BaseMapper {
    User getById(@Param("id") int id);

    int add(@Param("user") User user);


    User selectById(@Param("id") int id);
}
```

#### 2，我们在service中编写代码：

```java
@Transactional(readOnly = true)
public void getById(int id) throws InterruptedException {
    User user = userMapper.getById(id);
    System.out.println(user);
    Thread.sleep(20000);
    User user1 = userMapper.selectById(id);
    System.out.println(user1);
}
```

我们分别测试加上注解和不加注解的区别。

### 4，事务隔离级别

事物的隔离级别的设置可以用如下属性：

```java
@Transactional(isolation = Isolation.REPEATABLE_READ)
```

该属性可取值为一个枚举：

```java
public enum Isolation {
    DEFAULT(-1),
    READ_UNCOMMITTED(1),
    READ_COMMITTED(2),
    REPEATABLE_READ(4),
    SERIALIZABLE(8);

    private final int value;

    private Isolation(int value) {
        this.value = value;
    }

    public int value() {
        return this.value;
    }
}
```

### 5，事务传播行为

![在这里插入图片描述](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210612224750454.png)

我们在开发的时候首先最常用的是REQUIRED，也是默认的事物传播行为。它的意思是如果已经存在了一个事物了，就沿用之前的，否则新开启一个事物。然后我们还需要关注的有REQUIRES_NEW和NESTED。
REQUIRED：如果已经存在了一个事物了，就沿用之前的，否则新开启一个事物
REQUIRES_NEW：内部方法和外部方法不是同一个事物，内部方法抛出异常，外部不回滚，外部抛出异常，内部回滚。此处注意内部抛出异常，外部不处理，相当于外部直接往外抛。
NESTED：内外方法嵌套事物，内部抛出异常，外部不回滚，外部抛出异常，内部回滚。
注意：我们在开发的时候，一般我们使用默认的就行了，因为默认的是最安全的，只要有一个地方有异常，全部回滚。

### 6，指定异常回滚

我们首先，先来看一个例子。

#### 1，首先我们自定义一个异常：

```java
package com.vgxit.learn.spring.ktdm.trananno.exception;

public class VgException extends Exception {
    public VgException() {
    }

    public VgException(String message) {
        super(message);
    }

    public VgException(String message, Throwable cause) {
        super(message, cause);
    }

    public VgException(Throwable cause) {
        super(cause);
    }

    public VgException(String message, Throwable cause, boolean enableSuppression, boolean writableStackTrace) {
        super(message, cause, enableSuppression, writableStackTrace);
    }
}
```

#### 2，编写批量添加用户的方法：

```java
@Transactional
public void batchAdd(List<User> users) throws VgException {
    for (User user : users) {
        userMapper.add(user);
        if (user.getName().equals("name3")) {
            throw new VgException();
        }
    }
}
```

接下来，我们调用，发现，根本就没有回滚事务，还是插入了三条数据。这个是因为，我们的Transactionl注解，默认的情况下是如果发现抛出了RuntimeException就会回滚。否则不会。我们这里说一下，我们现在是只有发生了RuntimeException的时候才会回滚事务，否则不会。这种情况不是我们想要的，因为异常之后的代码不会执行，如果是抛出了其他的异常，可能就会造成数据不一致的问题。这一个，我们可以指定异常。最佳实践是所有的异常我们都需要回滚。

```java
@Transactional(rollbackFor = Throwable.class)
public void batchAdd(List<User> users) throws VgException {
    for (User user : users) {
        userMapper.add(user);
        if (user.getName().equals("name3")) {
            throw new VgException();
        }
    }
}
```

## 25，Transactionl注解失效问题

### 1、@Transactional 应用在非 public 修饰的方法上

如果Transactional注解应用在非public 修饰的方法上，Transactional将会失效。

![在这里插入图片描述](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210613002056515.png)

之所以会失效是因为在Spring AOP 代理时，如上图所示 TransactionInterceptor （事务拦截器）在目标方法执行前后进行拦截，DynamicAdvisedInterceptor（CglibAopProxy 的内部类）的 intercept 方法或 JdkDynamicAopProxy 的 invoke 方法会间接调用 AbstractFallbackTransactionAttributeSource的 computeTransactionAttribute 方法，获取Transactional 注解的事务配置信息。

```java
protected TransactionAttribute computeTransactionAttribute(Method method,
    Class<?> targetClass) {
        // Don't allow no-public methods as required.
        if (allowPublicMethodsOnly() && !Modifier.isPublic(method.getModifiers())) {
        return null;
}
```

此方法会检查目标方法的修饰符是否为 public，不是 public则不会获取@Transactional 的属性配置信息。
注意：protected、private 修饰的方法上使用 @Transactional 注解，虽然事务无效，但不会有任何报错，这是我们很容犯错的一点。

### 2、@Transactional 注解属性 propagation 设置错误

这种失效是由于配置错误，若是错误的配置以下三种 propagation，事务将不会发生回滚。

- TransactionDefinition.PROPAGATION_SUPPORTS：如果当前存在事务，则加入该事务；如果当前没有事务，则以非事务的方式继续运行。
  TransactionDefinition.PROPAGATION_NOT_SUPPORTED：以非事务方式运行，如果当前存在事务，则把当前事务挂起。
  TransactionDefinition.PROPAGATION_NEVER：以非事务方式运行，如果当前存在事务，则抛出异常。

### 3、@Transactional 注解属性 rollbackFor 设置错误

rollbackFor可以指定能够触发事务回滚的异常类型。Spring默认抛出了未检查unchecked异常（继承自RuntimeException的异常）或者Error才回滚事务；其他异常不会触发回滚事务。如果在事务中抛出其他类型的异常，但却期望 Spring 能够回滚事务，就需要指定 rollbackFor属性。

![在这里插入图片描述](https://raw.githubusercontent.com/Chalice555/Picgo/master/20210613002326129.png)

### 4、同一个类中方法调用，导致@Transactional失效

开发中避免不了会对同一个类里面的方法调用，比如有一个类Test，它的一个方法A，A再调用本类的方法B（不论方法B是用public还是private修饰），但方法A没有声明注解事务，而B方法有。则外部调用方法A之后，方法B的事务是不会起作用的。这也是经常犯错误的一个地方。
　　那为啥会出现这种情况？其实这还是由于使用Spring AOP代理造成的，因为只有当事务方法被当前类以外的代码调用时，才会由Spring生成的代理对象来管理。

### 5、异常被你的 catch“吃了”导致@Transactional失效

Exception直接被catch处理了。异常就没有跑出去，直接就在方法内部被消化了，那么spring会不会收到Exception，收不到。

### 6、数据库引擎不支持事务

