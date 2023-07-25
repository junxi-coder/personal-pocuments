# BUG

### **1.npm ERR! Cannot read properties of null (reading 'package')**

脚手架需要全局安裝 npm install gxblog -g

### **2.服务器宕机之后如何快速切换备用服务器  nginx**

### **3.Caused by: java.io.FileNotFoundException: class path resource [spring/] cannot be resolved to URL because it does not exist**

配置spring容器时候配置好classpath spring xml文件的路径

```xml
<context-param>
   <param-name>contextConfigLocation</param-name>
   <param-value>
      classpath:*/spring/applicationContext*.xml
   </param-value>
</context-param>
```



### **4.Invalid 'log4jConfigLocation' parameter: class path resource [*/resources/log4j.properties] cannot be resolved to absolute file path because it does not reside in the file system**

只有打上sources标签才会加载到classes下，通过classpath才能加载对应的资源，加载的资源不能前缀/ 否则会从项目根目录开始加载 导致加载失败



### **5.webservice常见问题**

JSR-224 (JAX-WS：Java API for XML-Based Web Services ) ，主要使用soap协议，使用wsdl来描述；

JSR-311 (JAX-RS：The Java API for RESTful Web Services)，使用wsdl描述；

soap协议（http+xml）

**（1）报错：服务器无法为请求提供服务，因为不支持该媒体类型。**

​			content-type不对，例如只支持 `text/xml; charset=UTF-8`

因为暴露的webservice实现规范是 **JAX-WS**  ，SOAP WS**仅允许使用XML数据格式。\**定义的操作通过\**POST请求发送**。而REST方式则允许多种数据格式，例如，XML、JSON、文本、HTML等等。

**（2）请求参数名错误**

​	 <s:element minOccurs="0" maxOccurs="1" **name="req"** type="s:string"/>

**（3）服务器未能识别 HTTP 头 SOAPAction 的值**

```java
postMethod.setRequestHeader("SOAPAction", nameSpace + methodName);
```

SOAPAction HTTP request [header](https://so.csdn.net/so/search?q=header&spm=1001.2101.3001.7020)被用来标识SOAP HTTP请求的目的地

SOAPAction header的内容可以被用在服务端，诸如：防火墙适当的过滤基于HTTP的[SOAP](https://so.csdn.net/so/search?q=SOAP&spm=1001.2101.3001.7020)请求消息等场景。

SOAPAction header的值为空串("")表示SOAP消息的目的地由HTTP请求的URI标识；无值则表示没有指定这条消息的目的地。

### **6.请求状态码220，解决方法：登录后再测试接口**

### **7.@RequestBody**

org.springframework.http.converter.HttpMessageNotReadableException: Required request body is missing

org.springframework.web.HttpMediaTypeNotSupportedException: Content type 'text/plain;charset=UTF-8' not supported

org.springframework.web.HttpMediaTypeNotSupportedException: Content type 'multipart/form-data;boundary=--------------------------687269989050921623532340;charset=UTF-8' not supported

后台只获取请求体 body中的参数，且只支持json字符串格式测试

### **8.java.sql.SQLException:Field'openid' doesn't hava a default value**

解决：后端需要加数据验证或者增加默认值，防止约束项不为NULL字段报此异常。

### **9.Post请求方式下后端参数接收失败**

原因1：在此方式下一般会把参数放在http Body体内，无法直接接收参数。

原因2：前端传递的参数为json格式，可以通过对象反序列化接收或者通过string数据类型接收。

解决：使用@requesbody注解,参数使用string或者JavaBean接收

### **10.创建SpringBoot项目时修改Server URL（下载路径）**

​	**将Server URL下载路径修改为阿里云镜像仓库：https://start.aliyun.com/**

#### 

### **11.localhost:8080 当查看本地端口未占用浏览器却显示页面时考虑浏览器缓存因素。**

#### 

```Java
nested exception is org.apache.ibatis.binding.BindingException: Parameter 'patientCode' not found. Available parameters are [0, 1, param1, param2]
解决；dao使用@param
@Param注解的作用，当我们的sql中需要多个参数的时候，Maybatis会将参数列表中的参数封装成一个Map进行传递，这个过程是通过@Param来实现的，@Param注解括号中的值会作为key,value就是参数实际的值
```

#### 

### **12.子查询中若进行排序则排序失效**

解决 使用limit强制执行排序功能

### **13.子查询会重新生成一张新表 注意查询条件会有所改变**

**14.nested exception is org.apache.ibatis.exceptions.TooManyResultsException: Expected one result (or null) to be returned by selectOne(), but found: 2]**

原因：返回应该是个集合
    

### **15.controller接收参数,会调用对象的无参构造创建对象，然后使用set方法赋值**



### **16.java.lang.IllegalStateException：已经调用getreader（）**

原因:

HttpServletRequest 的 getInputStream() 和 getReader() 都只能读取一次。
因为 我们使用@RequestBody 注解，读取body参数；而 又 写了拦截器，也需要将post请求，body数据拿出来。
由于@RequestBody 也是流的形式读取，流读了一次就没有了。
https://blog.csdn.net/qq_35387940/article/details/125423192



### **17.**ClassCastException

**java.lang.ClassCastException: org.apache.catalina.connector.RequestFacade cannot be cast to com.insight.core.config.**

无法向下强转，条件1：继承关系，条件二：父类不能实例化



### 18.BeanCreationException

org.springframework.beans.factory.**BeanCreationException**: Error creating bean with name 'jacksonObjectMapperBuilder' defined in class path resource [org/springframework/boot/autoconfigure/jackson/JacksonAutoConfiguration$JacksonObjectMapperBuilderConfiguration.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.http.converter.json.Jackson2ObjectMapperBuilder]: Factory method 'jacksonObjectMapperBuilder' threw exception; nested exception is java.lang.IllegalArgumentException: Illegal pattern character 'e'

**application.yml 中原来配置的 spring.jackson.date-format 与升级后的 jar 版本不兼容，删除此配置即可**

### 

### 19.postman

使用postman时报错如下 : Error: write EPROTO 93988952:error:100000f7:SSL routines:OPENSSL_internal:WRONG_VERSION_NUMBER:…/…/third_party/boringssl/src/ssl/tls_record.cc:242:

把https改成http，去掉s就能正常检测接口啦

### 20.编码排序问题

```

Caused by: java.sql.SQLException: Illegal mix of collations (utf8_general_ci,IMPLICIT) and (utf8_croatian_ci,IMPLICIT) for operation '='

编码排序问题
```

------

### 21.mq无法消费问题

   测试和线上使用了同一个队列

### 22.MySQL数据类型自动转换

mysql varchar类型字段=0取出数据不正确 mysql  在一个varchar列字段查询的时候传入条件为整型，这个时候会自动将数据库字段数据转换为整型再与传入的参数比较 所以这个时候 =  0比较就会出现查询的数据不准确的问题，所以varchar列查询最好传入的参数也是字符串类型



### 23.mysql 异常

#### 	1.Mybatis 报错Parameter index out of range (30 ＞ number of parameters, which is 29).

一、
 xml被注释掉的的SQL代码中含有获取值得表达式 ，例如：/*id=#{params.id}*/或者/*id=’${params.id}’*/都会抛出此异常，
 二、
 还有一个原因时因为手写[sql语句](https://so.csdn.net/so/search?q=sql语句&spm=1001.2101.3001.7020)错误。



# 知识点总结

Shift+Alt+F

### 1.字符串按，分割

```xml
<if test="approveStatus != null and approveStatus!=''">
      and i.approve_status IN
        <foreach item="status" collection="approveStatus.split(',')" open="(" separator="," close=")">
            #{status}
        </foreach>
</if>
```

### 2.对象转换为json

```java
String returnStr = JSON.toJSONString(r, SerializerFeature.WriteMapNullValue, SerializerFeature.DisableCircularReferenceDetect, SerializerFeature.WriteDateUseDateFormat);
```

### 3.字符串类型进行数值相加

```java
String str=new BigInteger("1").add(new BigInteger("2")).toString();
```

### 4.sql语句相同字段统计不同值的个数

```xml
SELECT
	sum(CASE assessment_result WHEN "1" THEN 1 ELSE 0 END) AS lowRisk,
	sum(CASE assessment_result WHEN "2" THEN 1 ELSE 0 END) AS middleRisk,
	sum(CASE assessment_result WHEN "3" THEN 1 ELSE 0 END) AS highRisk,
	sum(CASE assessment_result WHEN "6" THEN 1 ELSE 0 END) AS veryHighRisk
FROM tb_vte_assessment
WHERE 
	IFNULL(is_enable,'0') = 1 AND assessment_type = "1"
	<if test="patientCode != null and patientCode != ''">
		and patient_code = #{patientCode}
	</if>
```

### 5.java类序列号属性忽略注解

### 6.stream流用法

通过typeid分组-Map<Long, List<Shop>> map = list.stream().collect(Collectors.groupingBy(Shop::getTypeId)); 

#### 

### 7.hutool工具

```xml
 	<!--hutool-->
        <dependency>
            <groupId>cn.hutool</groupId>
            <artifactId>hutool-all</artifactId>
            <version>5.7.17</version>
        </dependency>
```

 	(1)JSONUtil.toBean(shopJson, Shop.class);

### 8.@ApiOperation swagger接口说明注解

### 9.String verifyCode = String.valueOf(new Random().nextInt(899999) + 100000); 生成6位验证码

### 10.通过 @PathVariable 可以将 URL 中占位符参数绑定到控制器处理方法的入参中:URL 中的 {xxx} 占位符可以通过

```java
	@RequestMapping("/getUserById/{name}")
    public User getUser(@PathVariable("name") String name){
        return userService.selectUser(name);
    }
```

### 11.布隆过滤器 

通过一个庞大的数组验证key是否存在，直接返回。 （缓存击穿解决方案）

### 12.SSH -专为[远程登录](https://baike.baidu.com/item/远程登录/1071998?fromModule=lemma_inlink)会话和其他网络服务提供安全性的协议。

从客户端来看，SSH提供两种级别的安全验证。

​	**第一种级别（基于口令的安全验证）**

只要你知道自己帐号和口令，就可以登录到远程主机。所有传输的数据都会被加密，但是不能保证你正在连接的服务器就是你想连接的[服务器](https://baike.baidu.com/item/服务器?fromModule=lemma_inlink)。可能会有别的服务器在冒充真正的服务器，也就是受到“中间人”这种方式的攻击。

​	**第二种级别（基于密匙的安全验证）**

需要依靠[密匙](https://baike.baidu.com/item/密匙?fromModule=lemma_inlink)，也就是你必须为自己创建一对密匙，并把公用密匙放在需要访问的服务器上。如果你要连接到SSH服务器上，客户端软件就会向服务器发出请求，请求用你的密匙进行安全验证。服务器收到请求之后，先在该服务器上你的主目录下寻找你的公用密匙，然后把它和你发送过来的公用密匙进行比较。如果两个密匙一致，服务器就用公用密匙加密“质询”（challenge）并把它发送给客户端软件。客户端软件收到“质询”之后就可以用你的私人密匙解密再把它发送给服务器。

用这种方式，你必须知道自己密匙的[口令](https://baike.baidu.com/item/口令?fromModule=lemma_inlink)。但是，与第一种级别相比，第二种级别不需要在网络上传送口令。

第二种级别不仅加密所有传送的数据，而且“中间人”这种攻击方式也是不可能的（因为他没有你的私人密匙）。但是整个登录的过程可能需要10秒



### 12.JAVA命名规范

**方法：**

（1）getXXX 获取数据

（2）getXXXs 获取数据集合

（3）isXXX 布尔判断

（4）toXXX 数据转换为XXX

（5）fromXXX 数据转换此XXX

（6）lostXXX 削弱能力



### 13.控制台如何打印日志？

```java
//1. 引入slf4j接口的Logger和LoggerFactory
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
 
public class UserService {
  //2. 声明一个Logger，这个是static的方式，我比较习惯这么写。
  private final static Logger logger = LoggerFactory.getLogger(UserService.class);
 
  public boolean verifyLoginInfo(String userName, String password) {
    //3. log it，输出的log信息将会是："Start to verify User [Justfly]
    logger.info("Start to verify User [{}]", userName);
    return false;
  }
}
```



### 14.动态sql

```XML
CASE WHEN tt.count IS NULL THEN 0 ELSE tt.count END

DATE_FORMAT( hi.patient_in_hospital, '%Y-%m-%d' ) patientInHospital,

 <choose>
                    <when test="reportResult == '1'.toString()">
                        AND hi.patient_number IN  (SELECT patient_number FROM tb_vte_report WHERE is_enable = 1)
                    </when>
                    <otherwise>
                        AND hi.patient_number IN  (SELECT patient_number FROM tb_vte_report WHERE is_enable = 1)
                    </otherwise>
                </choose>
```



### 15.空集合

```Java
//空集合
Collections.emptyList()
```

### 16.正则表达式

```Java
最简单的形式：

^\w+(,\w+)*$

I need to restrict only alphabets. How can I do that ?

使用正则表达式(包括示例unicode字符范围)：

^[\u0400-\u04FFa-zA-Z ]+(,[\u0400-\u04FFa-zA-Z ]+)*$

用法示例：

public static void main (String[] args) throws java.lang.Exception

{

String regex = "^[\u0400-\u04FFa-zA-Z ]+(,[\u0400-\u04FFa-zA-Z ]+)*$";

System.out.println("abc,xyz,pqr".matches(regex)); // true

System.out.println("text1,text2,".matches(regex)); // false

System.out.println("ЕЖЗ,ИЙК".matches(regex)); // true

}
```



### 17.压缩 打不开，找不到目标文件路径。

原因是：目录层级太深文件路径过长。

### 18.insert返回主键

```
useGeneratedKeys="true" keyProperty="id"
```



### 19.@ComponentScan注解作用：（扫描指定注解的类注册到IOC容器中）

    @ComponentScan用于类或接口上主要是指定扫描路径，spring会把指定路径下带有指定注解的类注册到IOC容器中。
    会被自动装配的注解包括@Controller、@Service、@Component、@Repository等等。
    其作用等同于<context:component-scan base-package="com.maple.learn" />配置。
常用属性如下：

    basePackages、value：指定扫描路径，如果为空则以@ComponentScan注解的类所在的包为基本的扫描路径
    basePackageClasses：指定具体扫描的类
    includeFilters：指定满足Filter条件的类
    excludeFilters：指定排除Filter条件的类
    includeFilters和excludeFilters 的FilterType可选：ANNOTATION=注解类型默认、ASSIGNABLE_TYPE(指定固定类)、ASPECTJ(ASPECTJ类型)、REGEX(正则表达式)、CUSTOM(自定义类型)，自定义的Filter需要实现TypeFilter接口



### 20.cmd命令过长？

使用 / 可以换行



### 21.@Deprecated 

标注该类或者方法已经过时



### 22.nacos问题（docker容器部署）

**1.配置文件拉取不到**

​	除了配置8848端口映射，还需要进行端口9849端口映射，springboot才能拉取nacos的配置文件

**2.nacos连接失败**





### 23.@Builder

Builder设计模式

# ====================================

### 1.SQL[字符串](https://so.csdn.net/so/search?q=字符串&spm=1001.2101.3001.7020)的分组聚合

我们在开发过程中有时需要对表中的数据进行分组，又需要查询出具体信息。
 本文中用到的是 **group_concat()** 函数
 **作用：**
 函数返回一个字符串结果，该结果由分组中的值连接组合而成。（多条数据，同样拼接在一个字符串中）
 **语法：**

```
group_concat( [distinct] 要连接的字段 [order by 排序字段 asc/desc ] [separator ‘分隔符’] )

select 
	account_id, age, 
	group_concat(name) as name, SUM(money) money 
from user 
	GROUP BY age
```

### 2.MySQL group_concat 长度限制

1、 查找当前数据库设置的长度

```
show variables like 'group_concat_max_len'
```

2、 设置当前session 的 group_concat 长度， 其他session 连接不受影响

```
SET SESSION group_concat_max_len = 10240;
```

3、设置 全局 group_concat 长度， 当前 session 不受影响，需要断开重连才生效

```
SET GLOBAL group_concat_max_len = 10240;
```

### 3.BeanCopyUtils  

1：首先在mapper层也就是dao层，我们记住我们一定是用domain实体类去接收查询出来的参数
2：然后我们在serviceImpl层接收到后，我们要将查询出来的数据赋值给vo层返回给前端，这里使用BeanCopyUtils将mapper层查询出来的数据赋给vo层
3：BeanCopyUtils

### 4.Comparable实现大小比较



        static class Person implements Comparable<Person>{
            private String name;
            private int age;
        public Person(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        @Override
        public int compareTo(Person o) {
            //this当前对象 与 o 比较
            //返回数据有三种类型：
            //整数 ： 代表this当前对象较大
            //0   :  代表一样大
            //负数 ： 代表this当前对象较小
            if(this.age > o.age){
                return 1;
            }else if(this.age == o.age){
                return 0;
            }
             return -1;
             //可以简写为return this.age - o.age;
        }
        }



### 5.maven依赖冲突

![image-20230221103203073](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230221103203073.png)

使用exclusions排除依赖包     



### 6.bootstrap.yml和application.yml

bootstrap.yml文件也是Spring Boot的默认配置文件，而且其加载的时间相比于application.yml更早。

application.yml和bootstrap.yml虽然都是Spring Boot的默认配置文件，但是定位却不相同。

bootstrap.yml可以理解成系统级别的一些参数配置，这些参数一般是不会变动的。

application.yml可以用来定义应用级别的参数，如果搭配 spring cloud config 使用，application.yml里面定义的文件可以实现动态替换。

### 7.LocalDateTime和Date的区别

##### 一、Date存在的缺陷

Date如果不格式化，打印出的日期可读性差,如下所示。

所以通常会使用SimpleDateFormate来实现格式化，但是[SDF](https://so.csdn.net/so/search?q=SDF&spm=1001.2101.3001.7020)最大的问题是线程不安全的。

![image-20230223110911710](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230223110911710.png)

SimpleDateFormat.format来进行日期格式化，format方法是父类dateformat抽象类，simpledateformat进行了实现format方法，其中使用了calendar这个共享变量，calendar.setDate()是线程不安全的。

![image-20230223111320815](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230223111320815.png)

##### 二、多线程并发如何保证线程安全

- 避免线程之间共享一个SimpleDateFormat对象，每个线程使用时都创建一次SimpleDateFormat对象 => 创建和销毁对象的开销大
- 对使用format和parse方法的地方进行加锁 => 线程阻塞性能差
- 使用ThreadLocal保证每个线程最多只创建一次SimpleDateFormat对象 => 较好的方法
   Date对时间处理比较麻烦，比如想获取某年、某月、某星期，以及n天以后的时间，如果用Date来处理的话真是太难了，你可能会说Date类不是有getYear、getMonth这些方法吗，获取年月日很Easy，但是这些方法都被弃用了。

## 

##### 三、LocalDateTime使用

JDK8带来了新的时间日期API也就是 java.time 包下面带来Local和Zone，他俩的区别一个是基于你本地时间的，一个是你自己指定时区的。

而Local都有这几个类：LocalDateTime（既包含时间也包含日期），LocalDate（只关注日期，一般来说你只关注日期不需要时间的话用这个），LocalTime（只关注时间，不关注日期）。

当然了，实际上LocalDate和LocalTime也支持日期+时间的形式，那他是怎么做到的呢，因为LocalDate里面包含一个atTime来存储时间，同理LocalTime也有一个atDate属性

所以说LocalDateTime取代Date是一个趋势，当然有人比较过二者的效率，**结果是Date要比LocalDateTIme快一些，这也没办法毕竟线程安全可能就要多点取舍**，未来的版本也许LocalDateTime也可以像Current集合那样线程又安全又快。



```html
Date.from( localDateTime.atZone( ZoneId.systemDefault()).toInstant());
```

### 8.ThreadLocal

使用 private static修饰

private static threadlocal<string> local = new threadlocal<string>();

常用方法

local.set() 

local.get()

local.remove() 

### 9.断言

assertions.assertNotNull()判断是否为空

### 10.slf4j和log4j的区别是什么

slf4j是通用的接口规范，log4j是具体实现的日志插件。*PS：代码中命名常用【4 代表 for】、【2 代表 to】*

slf4j:simple log facade for java

log4j:log for java



### 11.xml标记语言中有的字符有特殊含义需要进行转义处理

![image-20230224172447395](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230224172447395.png)

ps:其他语言中也有需要转义的部分

### 12.类的内部接口

1.接口标记

2.接口私有，接口的方法只会在本类中实现。

3灵活可变，这个和第一个就有所相反，他是在其他调用的地方实现

接口具体逻辑，通过回掉来执行逻辑

注意：类内部接口默认静态化

### 13.生成序列号

1、setting->Inspections->Serialization issues，将serialzable class without "serialVersionUID"打上勾；

### 14.swagger常见注解

Swaager的常用注解如下： 在Java类中添加Swagger的注解即可生成Swagger接口，常用Swagger注解如下：      

 @Api：修饰整个类，描述Controller的作用

 @ApiOperation：描述一个类的一个方法，或者说一个接口

 @ApiParam：单个参数描述

 @ApiModel：用对象来接收参数

 @ApiModelProperty：用对象接收参数时，描述对象的一个字段

 @ApiResponse：HTTP响应其中1个描述

 @ApiResponses：HTTP响应整体描述

 @ApiIgnore：使用该注解忽略这个API

 @ApiError ：发生错误返回的信息

 @ApiImplicitParam：一个请求参数

 @ApiImplicitParams：多个请求参数

### 15.mysql递归实现树形结构

with recursive t1 as (

select * from course_category p where id= '1' 

union all 

​	select t.* from course_category t inner join t1 on t1.id = t.parentid 

) 

select * from t1 order by t1.id, t1.orderby

**PS：mysql8.0以上才可以使用**

### 16.mybatis二级映射

```
<resultMap id="TreeResultMap" type="com.xuecheng.content.model.dto.CourseCategoryTreeDto">
    <id column="one_id" property="id" />
    <result column="one_name" property="name" />
    <result column="one_label" property="label" />
    <result column="one_parentid" property="parentid" />
    <result column="one_orderby" property="orderby" />
    <collection property="childrenTreeNodes" ofType="com.xuecheng.content.model.po.CourseCategory">
        <id column="two_id" property="id" />
        <result column="two_name" property="name" />
        <result column="two_label" property="label" />
        <result column="two_parentid" property="parentid" />
        <result column="two_orderby" property="orderby" />
    </collection>
</resultMap>
```



### 17.旧版idea调出微服务service窗口

.idea文件下的workspace.xml文件 调出微服务service窗口

```xml
 <component name="RunDashboard">
    <option name="configurationTypes">
      <set>
        <option value="SpringBootApplicationConfigurationType" />
      </set>
    </option>
    <option name="ruleStates">
      <list>
        <RuleState>
          <option name="name" value="ConfigurationTypeDashboardGroupingRule" />
        </RuleState>
        <RuleState>
          <option name="name" value="StatusDashboardGroupingRule" />
        </RuleState>
      </list>
    </option>
  </component>
```



### 18.spring事务声明式使用条件

​	1.通过代理对象调用

​	2.方法使用@transcational注解

### 19.mysql 日期格式化

```
DATE_FORMAT(a.patient_out_hospital,'%Y-%m-%d %H:%i:%s')
```

### 20.RandomAccessFile类

RandomAccessFile是独立于其他Java io流，具有读写能力，随机访问属性。

**1、RandomAccessFile(File file, String mode)**

**2、RandomAccessFile(String name, String mode)**

**两个构造方法的第一个参数不做介绍，**

**mode ：**第二个参数是指以什么模式创建读写流，此参数有固定的输入值，必须为"r"/"rw"/"rws"/"rwd"其中一个。

**r**：以只读方式打开指定文件。如果试图对该RandomAccessFile指定的文件执行写入方法则会抛出IOException
**rw**：以读取、写入方式打开指定文件。如果该文件不存在，则尝试创建文件
**rws**：以读取、写入方式打开指定文件。相对于rw模式，还要求对文件的内容或元数据的每个更新都同步写入到底层存储设备，默认情形下(rw模式下),是使用buffer的,只有cache满的或者使用RandomAccessFile.close()关闭流的时候儿才真正的写到文件
**rwd**：与rws类似，只是仅对文件的内容同步更新到磁盘，而不修改文件的元数据。

### 21.编程式事务

```java
@Autowired
private DataSourceTransactionManager transactionManager;

 TransactionDefinition def = new DefaultTransactionDefinition();
        TransactionStatus status = transactionManager.getTransaction(def);
        try {
          //TODO
            
            // 事务提交
            transactionManager.commit(status);
        }catch (Exception e){
            //事务回滚
            transactionManager.rollback(status);
            throw new RuntimeException(e);
        }
```

### 22.date_add函数

```
UPDATE sys_user SET create_time = DATE_ADD(create_time, INTERVAL 1 year) WHERE create_time < '2023-01-01 00:00:00'
```



### 23.rabbitMq 

解决无法连接AmqpConnectException: java.net.ConnectException: Connection timed out:

### 检查：

先检查端口，15672是控制端插件的端口，在SpringBoot的配置文件中，应该使用5672

- **在linux服务器注意开启这两个端口。**
- 登录用户，如果你使用的是guest默认的用户，那么默认情况下只能在localhost登录，解决：

1. 进入到etc的目录:
2. 再进入到rabbitmq的目录并且在此目录下编辑一个名为rabbitmq.config的文件(注意:名字一定要是这个)
3. 进入到文件编辑框,,加上如下的代码;
4. [{rabbit, [{loopback_users, []}]}].
5. 重启。

如果你使用的是自己创建的用户，那么检查你是否配置了权限

配置权限命令：rabbitmqctl set_permissions -p / 用户名 ".*" ".*" ".*"

### 3）停止服务

停止rabbitmq的所有服务(windows为例，在rabbitmq的安装目录bin目录下执行)：

```bash
rabbitmq-service stop
```

4）修改配置

A.配置文件： <安装目录>\RabbitMQ Server\rabbitmq_server_3.7.14\etc\rabbitmq.config.example

B.去掉注释符号%%，增加用户：

    %% ... 
    {tcp_listeners, [5672]},
    {loopback_users, ["admin"]},
    ...
### 5）启动rabbitmq的服务

```bash
rabbitmq-service start
```





### 24.防火墙

基本配置步骤

    查看暴露的端口号：iptables-save
    开放端口号：firewall-cmd --zone=public --add-port=80/tcp --permanent
    重新加载：firewall-cmd --reload

firewall防火墙

    查看firewall服务状态
    
    执行命令：systemctl status firewalld
        出现Active: active (running)切高亮显示则表示是启动状态
        出现Active: inactive (dead)灰色表示停止
    
    查看firewall的状态
    
    执行命令：firewall-cmd --state
    
    开启\重启\关闭firewalld.service服务
        开启：service firewalld start
        重启：service firewalld restart
        关闭 service firewalld stop
    
    查看防火墙规则
    
    执行命令：firewall-cmd --list-all
    
    查询、开放、关闭端口
        查询80端口是否开放：firewall-cmd --query-port=80/tcp
            no表示不开放
            yes表示开放
        开放80端口：firewall-cmd --permanent --add-port=80/tcp
        移除开放的80端口：firewall-cmd --permanent --remove-port=80/tcp
        重启防火墙(修改配置后要重启防火墙)：firewall-cmd --reload


### 25.aop落地

```
@Aspect
@Component
@Slf4j
public class VoteAop {

    @Autowired
    private IVoteDoctorService voteDoctorService;

    /**
    * TODO 用于答题系统saveUserAnswer接口增强
    *
    * @author: SuJunXi
    * @param:
    * @return:
    * @date: 2023/4/17 18:17
    */
    @After(value ="execution(public * com.insightin.modules.web.anser.service.ITrainUserAnserService.saveUserAnswer(..))")
    public void saveUserAnswerAop(JoinPoint joinPoint){
        Object[] args =joinPoint.getArgs();
        SaveUserAnswerDto saveUserAnswerDto = (SaveUserAnswerDto) args[0];
        TrainUserResult trainUserResult = saveUserAnswerDto.getTrainUserResult();
        Long userId = trainUserResult.getUserId();
        Integer score = trainUserResult.getScore();
        String cardNo = trainUserResult.getCardNo();
        if (!cardNo.contains("vote")){
            return;
        }
        VoteDoctor condition = new VoteDoctor();
        condition.setTrainUserId(userId);
        List<VoteDoctor> voteDoctors = voteDoctorService.selectVoteDoctorList(condition);
        if (CollectionUtils.isEmpty(voteDoctors)){
            log.info("【保存答题结果后置增强：注册医生未和答题id绑定】");
            return;
        }
        VoteDoctor voteDoctor = voteDoctors.get(0);
        voteDoctor.setIntegral(voteDoctor.getIntegral() + score);
        voteDoctor.setUpdateTime(DateUtils.getNowDate());
        voteDoctorService.updateVoteDoctor(voteDoctor);
        log.info("【保存答题结果后置增强成功】"+joinPoint.getTarget().getClass().getName()+"."+joinPoint.getSignature().getName());
    }
}
```

### 26.mysql字符串匹配

```xml
INSTR(TRIM(#{inspectItems}), a.title) > 0

instr(pram1,pram2)  pram1:长字符串，pram2:子字符串
trim(pram) 字符串首尾去空
```

### 27.mysql not in 踩坑

如果not in 中有null 则返回空集合

### 28.锁 踩坑

当只需要进行一次插入操作时，可以加同步锁，但被阻塞的线程依然会重新唤醒拿到锁并执行同步代码块，所以在进行修改前要再次查询确保数据库已经进行了插入防止重复插入

### 29.分布式锁 redis实现

**1.setnx** 实现分布式锁

​	1.1 set key value NX EX    EX:过期时间

​	1.2 redisTemplate.opsForValue().setIfAbsent()

**2.设置过期时间**

**3.Lua脚本原子性操作：**判断是自己的锁才删除

缺陷：过期时间设置不精确

### 30.redission 实现了java的重入锁LOCK接口

解决 过期时间设置不精确问题

### 31.redis 缓存持久化

**1.RDB内存快照**

​	**1.1 持久化**

​		1.1.1 通过save、bgsave主动备份RDB文件

​		1.1.2 通过redis.conf文件 save 900 1 配置自动备份 （通过bgsave）

​	**1.2 RDB执行原理**

​		1.2.1 bgsave开始时，会fork一个**子进程**,子进程会复制主进程的页表文件虚拟映射物理内存，读取**磁盘数据**，写新RDB替换旧RDB文件。

![image-20230504102051590](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230504102051590.png)

​		1.2.2  fork采用**copy-on-write**技术，防止产生脏数据

​			当主进程写操作访问共享内存时，会拷贝一份内存数据进行写操作同时页表的映射关系也会替换到新的内存空间

**2.AOF记录所有写操作**

​	**2.1** **刷盘策略**

​	![image-20230504102849655](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230504102849655.png)

​	**2.2 重写AOF**

​		2.2.1 通过bgrewriteaof命令主动重写

​		2.2.2 通过redis.conf配置自动重写

![image-20230504103154757](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230504103154757.png)

![image-20230504103256195](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230504103256195.png)

### 32.redis 过期策略

**1** **惰性删除** 当读取时判断key是否过期，过期则删除

**缺点：如果一个key一直没有进行访问则永远不会释放内存空间**

**2 定期删除** 每过一段时间则定期删除过期的key

​	2.1 SLOW模式是定时任务，每隔10hz删除一次，每次不超过25ms

​	2.2 FAST模式执行次数不固定，每次不超过1ms，间隔时间不低于2ms

**缺点：难以确定删除操作执行时长和频率**



### **33.redis 内存淘汰策略**

 ![image-20230504104856681](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230504104856681.png)

![image-20230504105303047](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230504105303047.png)

### 34、35、36 redis集群模式

### 34.redis 主从复制

​	1.实现高并发

   ![image-20230505102955785](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230505102955785.png)



### 35.redis 哨兵模式

​	1.实现redis的高可用

 ![image-20230505104917451](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230505104917451.png)

###  36.分片集群 

​	1.解决高并发写的问题

​	2.解决存储海量数据的问题

![image-20230505105701096](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230505105701096.png)



### 37.redis I/O多路复用，网络模型

![image-20230505112918798](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230505112918798.png)



**I/O多路复用有多种实现方案：**

select

poll

epoll

select、poll只会接收socket通知就绪，但不会记录socket，所以需要调用函数循环遍历

epoll，会记录已就绪的socket写入用户空间。性能大大提升



**redis的性能瓶颈在于网络I/O,提升性能的方案：**

1.实现I/O多路复用+事件派发

​	1.1 redis会监听多个socket请求，并且把请求分发到不同的处理器处理。

2.在网络请求和响应阶段在redis6.0引入了多线程

​	2.1 对请求命令接收并解析成redis指令

​	2.2 响应redis处理结果



### 38.mysql篇

### 38.1.mysql慢查询

 **如何定位慢查询？**

1.调试工具arthas

2.运维工具： skywalking

3.mysql慢日志 调试阶段

**sql的执行计划 desc/explain**

![image-20230506114402212](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230506114402212.png)

![image-20230506114528376](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230506114528376.png)

### 38.2 索引 

![image-20230512101515554](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230512101515554.png)



### 38.3 索引创建原则

![image-20230512104216816](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230512104216816.png)



### 38.4 索引失效

![image-20230512105311268](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230512105311268.png)



  

 



### 39.websocket实时通信

**1.坐标**

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-websocket</artifactId>
</dependency>
```



**2.添加websocket配置类**

```java
@Configuration
@EnableWebSocket
public class WebSocketConfig {
    @Bean
    public ServerEndpointExporter serverEndpointExporter() {
        return new ServerEndpointExporter();
    }

    @Bean
    public VoteWebSocket voteWebSocket() {
        return new VoteWebSocket();
    }
    @Bean
    public IVoteTeamService voteTeamService() {
        return new VoteTeamServiceImpl();
    }
}
```

​		2.1 首先要注入ServerEndpointExporter，这个bean会自动注册使用了@ServerEndpoint注解声明的Websocket endpoint。要注意，如果使用独立的																容器，而不是直接使用springboot的内置容器，就不要注入ServerEndpointExporter，因为它将由容器自己提供和管理。

​		2.2 当不由spring管理的bean可以通过调用set方法实现手动注入spring bean

​		2.3 在使用 `@ServerEndpoint` 注解标记 WebSocket 端点类时，我们通常需要使用 Java WebSocket API 提供的 `Endpoint` 类来手动注册 WebSocket 端点类。具体来说，我们可以在 Spring Boot 应用程序的配置类中创建一个 `ServerEndpointExporter` 对象，并调用其 `registerEndpoint()` 方法将 `@ServerEndpoint` 注解标记的 WebSocket 端点类注册为 Bean。

​		2.4 注意拦截器或者过滤器对路径的拦截

```java
  @Autowired
  public void setMyService(MyService myService) {
    this.myService = myService;
  }
```



3.websocket实时通讯

```java
@ServerEndpoint(value = "/mini/voteTeamRealTime")
public class VoteWebSocket {

    private static IVoteTeamService voteTeamService;
    //静态变量，用来记录当前在线连接数。应该把它设计成线程安全的。
    private static int onlineCount = 0;

    //concurrent包的线程安全Set，用来存放每个客户端对应的MyWebSocket对象。
    private static CopyOnWriteArraySet<VoteWebSocket> webSocketSet = new CopyOnWriteArraySet<VoteWebSocket>();

    //与某个客户端的连接会话，需要通过它来给客户端发送数据
    private Session session;
    
    //定时任务
    private static ScheduledExecutorService executor;
    
    public static synchronized int getOnlineCount() {
        return onlineCount;
    }

    public static synchronized void addOnlineCount() {
        VoteWebSocket.onlineCount++;
    }

    public static synchronized void subOnlineCount() {
        VoteWebSocket.onlineCount--;
    }

    public static synchronized Integer getSubOnlineCount() {
        VoteWebSocket.onlineCount--;
        return onlineCount;
    }
    public static synchronized Integer getAddOnlineCount() {
        VoteWebSocket.onlineCount++;
        return onlineCount;
    }

    @Autowired
    public void setVoteTeamService(IVoteTeamService voteTeamService) {
        if (VoteWebSocket.voteTeamService == null){
            VoteWebSocket.voteTeamService = voteTeamService;
        }
    }

    /**
     * 连接建立成功调用的方法*/
    @OnOpen
    public void onOpen(Session session) throws InterruptedException {
        this.session = session;
        List<TeamVo> teamListRealTime = voteTeamService.getTeamListRealTime();
        webSocketSet.add(this);     //加入set中
        Integer addOnlineCount = getAddOnlineCount();  //在线数加1
        System.out.println("有新连接加入！当前在线人数为" + addOnlineCount);
        try {
            if (addOnlineCount == 1){  //首次连接开启线程池
                System.out.println("开启任务");

                Runnable runnable = VoteWebSocket.getTeamListTask();
//                Runnable runnable = new Runnable() {
//                    @Override
//                    public void run() {
//                        List<TeamVo> list = voteTeamService.getTeamListRealTime();
//                        if (CollectionUtils.isEmpty(list)){
//                            list = Collections.EMPTY_LIST;
//                        }
//                        String json = new Gson().toJson(list);
//                        System.out.println(json);
//                        try {
//                            VoteWebSocket.sendInfo(json);
//                        } catch (IOException e) {
//                            e.printStackTrace();
//                        }
//                    }
//                };
                executor = Executors.newScheduledThreadPool(1);
                executor.scheduleAtFixedRate(runnable, 0, 2, TimeUnit.SECONDS);
            }

        } catch (Exception e) {
            System.out.println("IO异常");
        }
    }


    /**
     * 连接关闭调用的方法
     */
    @OnClose
    public void onClose() {
        webSocketSet.remove(this);  //从set中删除
        Integer subOnlineCount = getSubOnlineCount();//在线数减1
        if (subOnlineCount == 0){
            System.out.println("关闭任务");
            executor.shutdown();
        }
        System.out.println("有一连接关闭！当前在线人数为" + getOnlineCount());
    }

    /**
     * 收到客户端消息后调用的方法
     *
     * @param message 客户端发送过来的消息*/
    @OnMessage
    public void onMessage(String message, Session session) {
        System.out.println("来自客户端的消息:" + message);

//        //群发消息
//        for (MyWebSocket item : webSocketSet) {
//            try {
//                item.sendMessage(message);
//            } catch (IOException e) {
//                e.printStackTrace();
//            }
//        }


    }

    /**
     * 发生错误时调用
     @OnError
     public void onError(Session session, Throwable error) {
     System.out.println("发生错误");
     error.printStackTrace();
     }


     public void sendMessage(String message) throws IOException {
     this.session.getBasicRemote().sendText(message);
     this.session.getAsyncRemote().sendText(message);
     }
     */
    public void sendMessage(String message) throws IOException {
        this.session.getBasicRemote().sendText(message);
        //this.session.getAsyncRemote().sendText(message);
    }

        /**
         * 群发自定义消息
         * */
        public static void sendInfo (String message) throws IOException {

            for (VoteWebSocket item : webSocketSet) {
                try {
                    item.sendMessage(message);
                } catch (IOException e) {
                    continue;
                }
            }
        }




        /////////////////////下达通知任务/////////////////////////////////

        public static Runnable getTeamListTask(){
            Runnable runnable = new Runnable() {
                @Override
                public void run() {
                    List<TeamVo> list = voteTeamService.getTeamListRealTime();
                    Date lastTime = voteTeamService.getLastTime();
                    if (CollectionUtils.isEmpty(list)){
                        list = Collections.EMPTY_LIST;
                    }
                    Map map = new HashMap();
                    map.put("list",list);
                    map.put("lastTime",lastTime);
                    AjaxResult ajaxResult = AjaxResult.success(map);
                    String json = new Gson().toJson(ajaxResult);
                    try {
                        VoteWebSocket.sendInfo(json);
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            };
            return runnable;
        }


}
```



### 40.线程池-定时任务

```java
Runnable runnable = new Runnable() {
    @Override
    public void run() {
        try {
            MyWebSocket.sendInfo("1");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
};
ScheduledExecutorService executor = Executors.newScheduledThreadPool(1);
executor.scheduleAtFixedRate(runnable, 0, 1, TimeUnit.SECONDS);
```

1.如果重复调用 `executor.scheduleAtFixedRate()` 方法，将会启动多个定时任务，这些任务将会在指定的时间间隔内重复执行

2.关闭定时任务

```java
ScheduledExecutorService executor = Executors.newScheduledThreadPool(1);
// 启动一个定时任务，并保存 ScheduledFuture 对象
ScheduledFuture<?> future = executor.scheduleAtFixedRate(new Runnable() {
    public void run() {
        // 执行任务
    }
}, 0, 1, TimeUnit.SECONDS);
// 取消任务的执行
future.cancel(true);
// 关闭 ScheduledExecutorService
executor.shutdown();
```

我们通过调用 `cancel()` 方法取消了任务的执行，并通过调用 `shutdown()` 方法关闭了 `ScheduledExecutorService`。





### 40.mysql redo log（持久化）

事务提交后，按照一定频率刷盘时，如果发生错误，内存buffer Pool 缓冲池中的数据已丢失，会读取redolog进行数据恢复再进行刷盘。

### 41.mysql undo log(提供回滚、MVCC(多版本并发控制))（一致性、原子性）

记录一条相反的一条操作日志 

### 42.mysql 隔离性

![image-20230512114042601](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230512114042601.png)

  

**mvcc:**

​	**1.隐藏字段:**

​		**1.1 trx_id** (事务id)，记录每一次操作的事务id，自增。

​		1.2 roll_pointer(回滚指针)，指向上一个版本的事务版本记录地址。

​	**2.undo log:**

​		2.1 回滚日志，存储老版本数据

​		2.2 版本链

​	**3.readView 事务开启后，根据不同的事务隔离级别，执行select指令时，会生成一个视图记录，通过它可以进行版本的选择。**



###  **43.主从同步原理**

![image-20230518102124213](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518102124213.png)



### 44.分库分表

​	![image-20230518105629522](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518105629522.png)

### 45.spring框架

#### 	1.spring bean线程安全吗？

​		不是的，默认情况下springbean是单例的，但是可以通过注解@scope设置为多例。

​		但由于springbean通常是注入使用的无状态不可修改bean，所以一般情况下springbean是线程安全的。

####    2.spring bean的生命周期

​		![image-20230523112110135](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230523112110135.png)

 ![image-20230523112945383](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230523112945383.png)

aop：代理对象enhancer 最后返回的是代理对象。该步骤是在beanpostprocessor#after中进行的。

#### 3.spring循环依赖

1.一级缓存存储单例bean

2.二级缓存存储早期的bean 解决循环依赖

3.三级缓存存储对象工厂 解决代理对象循环依赖

 

手动解决循环依赖

构造方法出现了循环依赖？

![image-20230524102616232](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230524102616232.png)

#### 4.springmvc执行流程

 ![image-20230524104305617](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230524104305617.png)

#### 5.springboot自动配置原理

![image-20230524111145874](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230524111145874.png)

#### 6.spring、springboot、springmvc常见注解

![image-20230524111351706](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230524111351706.png)

![image-20230524111531702](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230524111531702.png)

 springboot 注解三兄弟

![image-20230524114059787](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230524114059787.png)

####   46.mybatis执行流程

读取mybatis-config.xml

![image-20230525102229119](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230525102229119.png)

#### 47.mybatis是否支持延迟加载

 ![image-20230525103912474](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230525103912474.png)

支持的，但默认是关闭的。需要增加fetchType属性开启延迟加载。

```
{
“id”:"1",
"name":“张三”，
“orderList”:[
​	{
​	}，
​	{
​	}
]
}
```

延迟加载是通过CGLIB动态代理实现

#### 48.mybatis得到一级、二级缓存

1.一级、二级缓存都是基于本地缓存perpetualcache本质是一个hashmap

2.一级缓存作用域是sqlsession级别

3.二级缓存作用域是整个namespace命名空间

### 49.微服务

#### 	49.1 springcloud五大组件

​	![image-20230525111029730](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230525111029730.png)

####  49.2 服务注册和发现

![image-20230525111911403](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230525111911403.png)

####  49.3 ribbon负载均衡

 ![image-20230525112908498](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230525112908498.png)

#### 49.4 服务雪崩

​	1.熔断降级（解决  ） hystix框架

​		当服务不可用时会进行降级，如果还有大量请求进来会进行熔断。

​		![image-20230525113847170](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230525113847170.png)

​	2.限流（预防）防止服务器资源消耗殆尽

#### 49.5 微服务监控 skywalking

![image-20230525120200766](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230525120200766.png)

###  50.分布式事务

1、Seata框架（XA、AT、TCC）MOS

2、MQ

 ![image-20230530110533836](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230530110533836.png) 

### 51.接口幂等

1.数据库唯一索引

2.token+redis

3.分布式锁，快速失败

### 52.rabbitMQ

1.**如何保证消息不丢失**

1.1 生产者确认机制 publisher confirm

![image-20230530113804484](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230530113804484.png)

  1.2 mq宕机 **消息持久化**

![image-20230530114446822](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230530114446822.png)

1.3 消费者确认机制

 ![image-20230530114833539](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230530114833539.png)



**2.重复消费问题**



1.每条消息设置一个唯一的标识id 通过验证id是否消费 进行确认

2.幂等方案：分布式锁，数据库锁



**3.延迟队列=死信交换机+TTL**

![image-20230602110900343](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230602110900343.png)

![image-20230602110909876](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230602110909876.png)



**4.当有100万条消息需要被消费，超过队列存储上限怎么办？**



​	增加消费者数量

​	消费者中开启线程池

​	增加队列容量上限 （使用**惰性队列**）

​	![image-20230602111414534](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230602111414534.png)

**5.mq的高可用？**

![image-20230602112357357](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230602112357357.png)



  通过搭建集群保证高可用，普通集群（采用引用方式，无法达到高可用会数据丢失），镜像集群（主从同步，但当同步数据前，主节点宕机会数据丢失），仲裁队列（弥补镜像集群的缺点）

 

### 53.限流

 **1.nginx限流**

​	控制速率，采用漏桶算法以固定的速率处理请求

​	控制并发数，限制单个ip的连接数和并发链接的总数

**2.网关限流**

​	在spring cloud gateway中支持局部过滤器requestRateLimiter来做限流，使用的是令牌桶算法

![image-20230602104947137](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230602104947137.png)

### 54.远程debug

1.给jar包加参数

```linux
-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005

java -jar -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 project.jar
```



2.idea打开debug configurations

配置remote

![image-20230613114641872](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230613114641872.png)



7、如果是调试war包的话我们需要修改tomcat的startup.bat文件

1》需要先将项目部署到tomcat目录下的webapp目录下

2》修改Tomcat/bin/startup.bat文件

    # vim startup.bat
    
    #编辑配置文件信息，在最前面加上如下代码：
    
    SET CATALINA_OPTS=-server -Xdebug -Xnoagent -Djava.compiler=NONE -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005

 其他步骤如上即可。

### 55.多线程如何顺序执行？

使用join（）方法：它是线程实例的方法，调用后当前线程必须等待调用join方法的线程结束运行之后才可以运行。

### 56.线程加锁后调用wait()

调用线程的wait方法会使当前线程进入等待状态，并且释放锁，等待其他线程调用notify或notifyAll方法唤醒线程。但是，锁并不会立即释放，而是在当前线程进入等待状态后才会释放锁。其他线程需要等待当前线程释放锁之后才能获取锁。

### 57.java中wait和sleep的区别

![image-20230614111621600](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230614111621600.png)

### 58.零拷贝技术

零拷贝（Zero Copy）技术是指在数据传输过程中，不需要把数据先从内核缓冲区拷贝到用户缓冲区，再从用户缓冲区拷贝到网络协议栈缓冲区，而是直接在内核空间中进行数据传输，避免了数据在多个缓冲区之间的拷贝，从而提高了数据传输的效率和速度。 传统的IO模型，数据需要经过多次的拷贝才能到达网络协议栈，而零拷贝技术可以避免这些拷贝，从而减少了CPU的负载和内存的消耗，提高了系统的性能。 零拷贝技术的实现需要依赖硬件设备和操作系统的支持，主要分为以下几种方式：

1. sendfile方式：通过操作系统提供的sendfile系统调用，将文件内容直接传输到网络协议栈缓冲区，避免了数据在用户空间和内核空间之间的拷贝。
2. mmap方式：通过将文件映射到内存中，将内存中的数据直接传输到网络协议栈缓冲区，避免了数据在用户空间和内核空间之间的拷贝。
3. DMA方式：通过直接内存访问（Direct Memory Access），将内存中的数据直接传输到网络协议栈缓冲区，避免了CPU的干预和数据在内存之间的拷贝。 零拷贝技术在网络通信、文件传输、视频流等领域都有广泛的应用，可以提高数据传输的效率和速度，减少系统的负载和内存的消耗。

### 59.查看class字节码信息

javap -v xx.class

### 60.monitor重量级锁

![image-20230615101236885](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230615101236885.png)

![image-20230615101629032](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230615101629032.png)










































# idea快捷键

ctrl+h 查看接口所有实现类

CTRL +alt +B 查看实现类

ctrl+r 替换文本  

alt +1 打开/关闭project

ctrl+alt+l 格式化代码

ctrl+alt+o 删除未导入的包



# idea插件

1.http client





# 架构图 pressOn

https://www.processon.com/template/framework 

https://www.figma.com/file/xMOO021cYeMaKJx2YShChm/Untitled?type=whiteboard&node-id=0%3A1&t=geIKI3SgEqM19WmE-1



figma





# 云服务器

【腾讯云】云产品限时秒杀，爆款1核2G云服务器，首年74元
https://cloud.tencent.com/act/cps/redirect?redirect=1077&cps_key=2fa23ab757f2e13bb49c404757dc6bce&from=console
