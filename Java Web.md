## JavaWeb介绍

### 什么是JavaWeb?

- Web:全球广域网，也称为万维网(www),能够通过浏览器访问的**网站**
- JavaWeb:是用Java技术来解决相关web互联网领域的技术栈

![image-20221002214228510](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002214228510.png)

1.网页：展现数据
2.数据库：存储和管理数据
3.JavaWeb程序：逻辑处理

### Javaweb整体框架

![JavaWeb](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/JavaWeb.png)

### Maven

#### 一.Maven作用

Maven是专门用于管理和构建ava项目的工具，它的主要功能有：

- 提供了一套标准化的项目结构
- 提供了一套标准化的构建流程(编译，测试，打包，发布)
- 提供了一套依赖管理机制

##### 1.标准化的项目结构

![image-20221002215725794](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002215725794.png)

**不同的ide之间,项目结构不一样,不通用**

![image-20221002215956893](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002215956893.png)

**Maven提供了一套标准化的项目结构，所有lDE使用Maven构建的项目结构完全一样，所有IDE创建的Maven.项目可以通用**

##### 2.标准化构建流程

![image-20221002220154661](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002220154661.png)

Maven提供了一套简单的命令来完成项目构建

##### 3.依赖管理机制

依赖管理其实就是管理你项目所依赖的第三方资源(G包、插件.…)

以前的导入依赖

![image-20221002220416091](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002220416091.png)

通过Maven导入依赖

![image-20221002220535056](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002220535056.png)

1.Maven使用标准的坐标配置来管理各种依赖
2.只需要简单的配置就可以完成依赖管理

#### 二.Maven简介

**Apache Maven**是一个项目管理和构建**工具**，它基于项目对象模型(POM)的概念，通过一小段描述信息来管理项目的构建、报告和文档

官网：http:/maven.apache.org

##### 1.Maven模型

![image-20221002221331353](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002221331353.png)

- 项目对象模型(Project Object Model)
- 依赖管理模型(Dependency)
- 插件Plugin)

##### 2.Maven仓库

![image-20221002221849751](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002221849751.png)

- 本地仓库：自己计算机上的一个目录

- 中央仓库：由Maven团队维护的全球唯一的仓库

  ​				地址：https://repo1.maven.org/maven2/

- 远程仓库（私服）：一般由公司团队搭建的私有仓库

![image-20221002222701718](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002222701718.png)

当项目中使用坐标引入对应依赖jar包后，首先会查找本地仓库中是否有对应的jar包：
如果有，则在项目直接引用；
如果没有，则去中央仓库中下载对应的jar包到本地仓库。

![image-20221002223351311](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221002223351311.png)

还可以搭建远程仓库，将来jar包的查找顺序则变为：
本地仓库→远程仓库→中央仓库

#### 三.Maven的安装&配置及基本使用

##### 1.安装及配置

1.解压apache-maven-3.6.1.rar既安装完成
2.配置环境变量MAVEN HOME为安装路径的bin目录
3.配置本地仓库：修改conf/settings.xml中的<localRepository>为一个指定目录
4.配置阿里云私服：修改conf/settings.Xml中的<mirrors>标签，为其添加如下子标签：

```xml
<mirror>
  <id>nexus-aliyun</id>
  <name>Nexus aliyun</name>
  <url>http://maven.aliyun.com/nexus/content/groups/public</url>
  <mirrorOf>central</mirrorOf>
</mirror>
```

##### 2.Maven基本使用

###### 2.1常用命令

- compile：编译
- clean:清理
- test:测试
- package:打包
- install:安装

###### 2.2Maven生命周期

Maven构建项目生命周期描述的是一次构建过程经历经历了多少个事件

Maven对项目构建的生命周期划分为3套

- clean:清理工作
- default:核心工作，例如编译，测试，打包，安装等
- site产生报告，发布站点等

**同一生命周期内，执行后边的命令，前边的所有命令会自动执行**

![image-20221003143311665](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003143311665.png)

#### 四.IDEA配置Maven

##### 1.IDEA配置Maven环境

1. 选择IDEA中File->Settings
2. 搜索maven
3. 设置IDEA使用本地安装的Maven,并修改配置文件路径

![image-20221003144630939](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003144630939.png)

![image-20221003145156489](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003145156489.png)

![image-20221003145133214](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003145133214.png)

##### 2.Maven坐标详解

###### 2.1坐标:

- Maven中的坐标是资源的唯一标识I
- 使用坐标来定义项目或引入项目中需要的依赖

###### 2.2Maven坐标主要组成

- groupld:定义当前Maven.项目隶属组织名称（通常是域名反写，例如：com.itheima)
- artifactld:定义当前Maven项目名称（通常是模块名称，例如order--service、goods-service)
- version:定义当前项目版本号

```xml
<groupId>com.itheima</groupId>
<artifactId>maven-demo</artifactId>
<version>1.0-SNAPSHOT</version>
```

```xml
<dependency>
		<groupId>mysql</groupId>
		<artifactId>mysql-connector-java</artifactId>
		<version>5.1.46</version>
</dependency>
```

##### 3.IDEA创建Maven项目

1.创建模块，选择Maven,点击Next
2.填写模块名称，坐标信息，点击finish,创建完成
3.编写HelloWorld,并运行

![image-20221003153426773](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003153426773.png)

![image-20221003153604046](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003153604046.png)

##### 4.IDEA导入Maven项目

###### 4.1.导入

1.选择右侧Maveni面板，点击+号
2.选中对应项目的pom.xml文件，双击即可
3.如果没有Maven面板，选择View→Appearance→Tool Window Bars

![uTools_1664783221554](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/uTools_1664783221554.png)

![uTools_1664783259299](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/uTools_1664783259299.png)

![image-20221003154825413](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003154825413.png)

#### 五.依赖管理

##### 1.使用坐标导入jar包

1.在pom.xml中编写<dependencies>:标签
2.在<dependencies>标签中使用<dependency>引入坐标
3.定义坐标的groupld,artifactld,version
4.点击刷新按钮，使坐标生效

![image-20221003211227798](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003211227798.png)

![image-20221003211245410](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003211245410.png)

##### 2.依赖范围

通过设置坐标的依赖范围(scope),可以设置对应jar包的作用范围：编译环境、测试环境、运行环境

![image-20221003211354689](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221003211354689.png)

| 依赖范围 | 编译classpath | 测试classpath | 运行classpath | 例子              |
| -------- | :-----------: | :-----------: | :-----------: | ----------------- |
| compile  |       Y       |       Y       |       Y       | logback           |
| test     |       -       |       Y       |       -       | Junit             |
| provided |       Y       |       Y       |       -       | servlet-api       |
| runtime  |       -       |       Y       |       Y       | jdbc驱动          |
| system   |       Y       |       Y       |       -       | 存储在本地的jar包 |
| import   |     引入      |  Dependency   |    Manage     | ment              |

<scope>:默认值：compile

### MyBatis

#### 一.MyBatis简介

##### 1.什么是MyBatis

- MyBatis是一款优秀的**持久层框架**，用于简化 JDBC 开发
- MyBatis本是Apache的一个开源项目iBatis,2010年这个项目由apache software
  foundation迁移到了google code,并且改名为MyBatis。2013年11月迁移到Github
- 官网：https://mybatis.org/mybatis-3/zh/index.html

##### 2.持久层

- 负责将数据到保存到数据的那一层代码
- JavaEE三层架构：表现层、业务层、持久层

##### 3.框架

- 框架就是一个半成品软件，是一套可重用的、通用的、软件基础代码模型
- 在框架的基础之上构建软件编写更加高效、规范、通用、可扩展

#### 二.MyBatis简化

##### 1.JDBC缺点

1.硬编码

>注册驱动，获取连接
>SQL语句

2.操作繁琐

>手动设置参数
>手动封装结果集

```java
//1.注册驱动
Class.forName("com.mysql.jdbc.Driver");
//2.获取Connection.连接
String url = "jdbc:mysql:///db1?useSSL=false";
String uname "root";
String pwd ="1234";
Connection conn = DriverManager.getConnection(url,uname,pwd);
∥接收输入的查询条件
String gender="男"；
∥定义sql
String sql "select from tb_user where gender = ?";
∥获取pstmt对象
PreparedStatement pstmt =  conn.prepareStatement(sql);
∥设置?的值
pstmt.setString(1,gender);
∥执行sql
ResultSet rs = pstmt.executeQuery();
∥遍历Result,获取数据
User user = null;
ArrayList<User>users new ArrayList<>();
while (rs.next(){
∥获取数据
    int id rs.getInt("id");
    String username = rs.getString("username");
    String password = rs.getString("password");
    ∥创建对象，设置属性值
    user = new User();
    user.setld(id);
    user.setUsername(username);
    user.setPassword(password);
    user.setGender(gender);
    ∥装入集合
    users.add(user);
}
```

​			**MyBatis免除了几乎所有的JDBC代码**
​			**以及设置参数和获取结果集的工作**

#### 三.MyBatis快速入门

##### 1.查询user表中所有数据

1.创建user表，添加数据

2.创建模块，导入坐标

3.编写小yBatis核心配置文件->替换连接信息解决硬编码问题

4.编写SQL映射文件->统一管理sq语句，解决硬编码问题

5.编码

			1.定义P0J0类
			2.加载核心配置文件，获取SqlSessionFactory对象
			3.获取SqlSession对象，执行SQL语句
			4.释放资源

```mysql
create database mybatis;
use mybatis;

drop table if exists tb_user;

create table tb_user(
		id int PRIMARY key auto_increment,
		username varchar(20),
		password varchar(20),
		gender char(1),
		addr varchar(30)
);


insert into tb_user values(1,'张三','123','男','北京');
insert into tb_user values(2,'李四','345','女','上海');
insert into tb_user values(3,'王五','567','男','成都');
```

##### 2.解决SQL映射文件的警告提示

- 产生原因：Idea和数据库没有建立连接，不识别表信息
- 解决方式：在ldea中配置MySQL数据库连接

#### 四.Mapper代理开发

##### 1.目的

>​		解决原生方式中的硬编码
>
>​		简化后期执行SQL

```java
        List<User> users = sqlSession.  selectList("test.selectAll");
        System.out.println(users);
```

```java
        //3.获取接口代理对象
        UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
        //4.执行方法，其实就是执行sgL语句
        List<User>users = userMapper.selectAll();
```

##### 2.使用Mapper代理方式完成入门案例

>1.定义与SQL映射文件同名的Mapper接口，并且将Mapper接口和SQL映射文件放置在同一目录下
>
>2.设置SQL映射文件的namespace)属性为Mapper接口全限定名
>
>3.在Mapper接口中定义方法，方法名就是SQL映射文件中sql语句的id,并保持参数类型和返回值类型一致
>4.编码
>
>​			4.1.通过SqlSession的getMapper方法获取Mapper接口的代理对象
>​			4.2.调用对应方法完成sq的执行

**细节：如果Mapper接口名称和SQL映射文件名称相同，并在同一目录下，则可以使用包扫描的方式简化SQL映射文件的加载**

#### 五.MyBatis核心配置文件

##### 1.environments

配置数据库连接环境信息.可以配置多个environment,通过不同的default属性切换不同的environment

```xml
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <!-- 数据库连接信息 -->
                <property name="driver" value="com.mysql.cj.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql:///mybatis?useSSL=false"/>
                <property name="username" value="root"/>
                <property name="password" value="123456"/>
            </dataSource>
        </environment>
    </environments>
```

##### 2.mappers

```xml
    </environments>
    <mappers>
        <!-- 加载sql映射文件 -->
        <mapper resource="com/gbx/mapper/UserMapper.xml"/>

        <!-- Mapper代理方式 -->
        <package name="com.gbx.mapper"/>
    </mappers>
```

##### 3.typeAliases

类型别名可为Java类型设置一个缩写名字。它仅用于XML配置，意在降低冗余的全限定类名书写。

```xml
    <typeAliases>
        <package name="com.gbx.pojo"/>
    </typeAliases>
```

#### 六.MyBatis完成CURD

查询

- 查询所有数据
- 查看条件
- 条件查询

添加

修改

- 修改全部字段
- 修改动态字段

删除

- 删除一个
- 批量删除

##### 1.通过配置xml文件

###### 1.1准备环境

​		数据库表tb_ brand
​		实体类Brand
​		测试用例
​		安装MyBatisX:插件

```mysql
#删除tb_brand表
drop table if exists tb_brand;
#创建tb_brand表
create table tb_brand
(
    #id  主键
    id  int primary key auto_increment,
    # 品牌名称
    brand_name  varchar(20),
    # 企业名称
    company_name  varchar(20),
    #排序字段
    ordered  int,
    # 描述信息
    description  varchar(100),
    #状态: 0 :禁用  1: 启动
    status int
);
insert into tb_brand(brand_name,company_name,ordered,description,status)
values('三只松鼠','三只松鼠股份有限公司',5,'好吃不上火',0),
      ('华为','华为技术有限公司',100,'华为致力于把数字世界带入每个人、每个家庭、每个组织，构建万物互联的智能世界',1),
      ('小米','小米科技有限公司',50,'are you ok',1);
select * from tb_brand;
```

```java
@Data
public class Brand {
    //id 主键
    private Integer id;
    //品牌名称
    private String brandName;
    //企业名称
    private String companyName;
    //排序字段
    private Integer ordered;
    //描述信息
    private String description;
    //状态：0：禁用1：启用
    private Integer status;
}
```

###### 1.2MyBatisX

> MyBatisX是一款基于IDEA的快速开发插件，为效率而生。

主要功能：

- XML和接口方法相互跳转
- 根据接口方法生成statement

###### 1.3查询

**查询所有**

1.编写接口方法：Mapper接口

- 参数：无
- 结果：List<Brand>

2.编写SQL语句：SQL映射文件：
3.执行方法，测试

```java
public interface BrandMapper {
    /**
     * 查询所有
     */
    public List<Brand> selectAll();
}

```

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "https://mybatis.org/dtd/mybatis-3-mapper.dtd">
<!--
namespace:名称空间
-->
<mapper namespace="com.gbx.mapper.BrandMapper">
    <select id="selectAll" resultType="brand">
        select * from
        tb_brand;
    </select>
</mapper>
```

```java
public class MyBatisTest {
    @Test
    public void testSelectAll() throws IOException {
        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        List<Brand> brands = brandMapper.selectAll();
        System.out.println(brands);
        //5.释放资源
        sqlSession.close();

    }
}
```

MyBatis完成操作需要几步？
三步：编写接口方法>>编写>>执行方法

实体类属性名和数据库表列名不一致，不能自动封装数据
1)起别名：在SQL语句中，对不一样的列名起别名，别名和实体类属性名一样
		可以定义<sql>片段，提升复用性
2)resultMap:定义<resultMap>完成不一致的属性名和列名的映射

```xml
<!--
    数据库表的字段名称  和  实体类的属性名称不一样,则不能自动封装数据
       *起别名: 对不一样的列名起别名,让别名和实体类的属性名一样
            *缺点:每次查询都要定义一次别名
				*解决办法:sql 片段
					缺点:不灵活
-->
<select id="selectAll" resultType="com.gbx.pojo.Brand">
    select id,brand_name as brandName,company_name as companyName,ordered,description,status
    from tb_brand;
</select>
```

```xml
<!--
  sql 片段
-->
<sql id="brand_column">
    id,brand_name as brandName,company_name as companyName,ordered,description,status
</sql>
<select id="selectAll" resultType="com.gbx.pojo.Brand">
    select 
        <include refid="brand_column"/>
    from tb_brand;
</select>
```

```xml
<!--
    数据库表的字段名称  和  实体类的属性名称不一样,则不能自动封装数据
    *resultMap:
        1.定义<resultMap>标签
        2.使用resultMap属性替换 resultType属性
-->
<!--
    id:唯一标识
    type:映射的类型,支持别名
 -->
<resultMap id="brandResultMap" type="brand">
    <!--
        id:完成主键的映射
            column:表的列名
            property:实体类的属性名
        result:完成一般字符的映射
     -->
    <result column="brand_name" property="brandName"/>
    <result column="company_name" property="companyName"/>
</resultMap>
<select id="selectAll" resultType="brandResultMap">
    select
    *
    from tb_brand;
</select>
```

**查看详情**

1.编写接口方法：Mapper接口
参数：id
结果：Brand
2.编写SQL语句：SQL映射文件
3.执行方法，测试

```xml
<!--
 *参数占位符:
            1.#{}:会将其替换成 ? .为了防止sql注入
            2.${}:拼sql 会存在sql注入问题
            3.使用时机:
                    *在参数传递的时候: #{}
                    *表明或者列名不固定的情况下:${}会存在sql注入问题
            *参数类型:parameterType:可以省略
            *特殊字符处理:
                    1.转义字符:
                    2.CDATA区
                    <I[CDATA[内容]>
 -->
<select id="selectById" parameterType="int" resultMap="brandResultMap">
    select * from tb_brand where id = #{id};
</select>
```

**条件查询**

1.多条件查询

1.编写接口方法：Mapper接口

​	参数：所有查询条件
​	结果：List<Brand>

2.编写SQL语句：SQL映射文件
3.执行方法，测试

```java
	List<Brand> selectByCondition(@Param("status")int status,@Param("companyName") String companyName,@Param("brandName")String brandName);

    <select id="selectByCondition" resultType="brandResultMap">
        select * from tb_brand
        where status = #{status} and company_name like #{companyName}
        and brand_name like #{brandName}
    </select>
        
    @Test
    public void testSelectByCondition() throws IOException {
        //接收参数
        int status = 1;
        String companyName = "华为";
        String brandName = "华为";

        //处理参数
        companyName="%"+companyName+"%";
        brandName="%"+brandName+"%";
        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        List<Brand> brands = brandMapper.selectByCondition(status, companyName, brandName);
        System.out.println(brands);
        //5.释放资源
        sqlSession.close();
    }

```

```java
    List <Brand> selectByCondition(Brand brand);

    <select id="selectByCondition" resultType="brandResultMap">
        select * from tb_brand
        where status = #{status} and company_name like #{companyName}
        and brand_name like #{brandName}
    </select>
    
	@Test
    public void testSelectByCondition() throws IOException {
        //接收参数
        int status = 1;
        String companyName = "华为";
        String brandName = "华为";

        //处理参数
        companyName="%"+companyName+"%";
        brandName="%"+brandName+"%";

        //封装对象
        Brand brand = new Brand();
        brand.setStatus(status);
        brand.setCompanyName(companyName);
        brand.setBrandName(brandName);
        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        List<Brand> brands = brandMapper.selectByCondition(brand);
        System.out.println(brands);
        //5.释放资源
        sqlSession.close();
    }
```

```java
    List <Brand> selectByCondition(Map map);

    <select id="selectByCondition" resultType="brandResultMap">
        select * from tb_brand
        where status = #{status} and company_name like #{companyName}
        and brand_name like #{brandName}
    </select>
    
    @Test
    public void testSelectByCondition() throws IOException {
        //接收参数
        int status = 1;
        String companyName = "华为";
        String brandName = "华为";

        //处理参数
        companyName="%"+companyName+"%";
        brandName="%"+brandName+"%";

        //Map集合
        Map map = new HashMap();
        map.put("status",status);
        map.put("companyName",companyName);
        map.put("brandName",brandName);
        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        List<Brand> brands = brandMapper.selectByCondition(map);
        System.out.println(brands);
        //5.释放资源
        sqlSession.close();
    }
```

##### 2.动态查询 

SQL语句会随着用户的输入或外部条件的变化而变化，我们称为动态SQL

```xml
<select id="selectByCondition"resultMap="brandResultMap">
    select  *
    from tb_brand
    where
    		if(status!=null)
    			   	  status =#status)
    	and company name like #{companyName}
    	and brand name like #{brandName)
<select>
```

MyBatis对动态SQL有很强大的支撑：

- if
- choose (when,otherwise)
- trim (where,set)
- foreach

###### 2.1if查询

```xml
    <!--
    动态条件查询
		*if:条件判断
			*test:逻辑表达式
		*问题:第一个条件不需要逻辑运算符
			*恒等式
			*<where>替换where关键字
    -->
    <select id="selectByCondition" resultType="brandResultMap">
        select * from tb_brand
        where
        <if test="status!=null">
            status = #{status}
        </if>
        <if test="companyName!=null and companyName!=''">
            and company_name like #{companyName}
        </if>
        <if test="brandName!=null and brandName!=''">
            and brand_name like #{brandName}
        </if>
    </select>
```

###### 2.2choose(when,otherwise)查询

从多个条件中选择个.

类似于Java中的switch语句

```xml
<select id="selectByConditionSingle"resultMap="brandResultMap">
    select
    from tb_brand
    where
    <choose><!-类似于switch->
        <when test=:"status=nul"><!-类似于case->
        	status =#{status)
        </when>
        <when test="companyName!=null and companyName !="">
            company_name like #{companyName}
        </when>
        <when test="brandName !null and brandName !=""
            brand_name like #{brandName}
        </when>
        <otherwise><I-类似于default->
            1=1
        </otherwise>
	</choose>
</select>
```

##### 3.添加

1.编写接口方法：Mapper接口

- 参数：除了id之外的所有数据
- 结果：void

2.编写SQL语句：SQL映射文件

3.执行方法，测试

MyBatis事务：

- openSession0:默认开启事务，进行增删改操作后需要使用sqlSession.commit0;手动提交事务
- openSession(true):可以设置为自动提交事务（关闭事务）

```java
	/**
	 * 添加
	 */
	void add(Brand brand);
```

```xml
	<insert id="add">
		insert into tb_brand (brand_name,company_name,ordered,description,status)
		values (#{brandName},#{companyName},#{ordered},#{description},#{status});
	</insert>
```

```xml
<insert id="add">
    insert into tb_brand (brand_name,company_name,ordered,description,status)    
    values (#{brandName},#{companyName},#{ordered},#{description},#{status});
</insert>
```

```java
    @Test
    public void testAdd() throws IOException {
        //接收参数
        int status = 1;
        String companyName = "菠萝手机";
        String brandName = "菠萝";
        String description = "菠萝手机,手机中的战斗机";
        int ordered = 100;
		
		//封装对象
		Brand brand = new Brand();
		brand.setStatus(status);
		brand.setCompanyName(companyName);
		brand.setBrandName(brandName);
		brand.setDescription(description);
		brand.setOrdered(ordered);
		
        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        //方式一
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //方式二  自动提交事务
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        brandMapper.add(brand);
        //提交事务
        sqlSession.commit();
        //5.释放资源
        sqlSession.close();
    }
```

###### 3.1主键返回

在数据添加成功后，需要获取插入数据库数据的主键的值

- 比如：添加订单和订单项

1.添加订单

2.添加订单项，订单项中需要设置所属订单的id

```xml
<insert id="add" useGeneratedKey="true" keyProperty="id">
    insert into tb_brand (brand_name,company_name,ordered,description,status)    
    values (#{brandName},#{companyName},#{ordered},#{description},#{status});
</insert>
```

```java
    @Test
    public void testAdd2() throws IOException {
        //接收参数
        int status = 1;
        String companyName = "菠萝手机";
        String brandName = "菠萝";
        String description = "菠萝手机,手机中的战斗机";
        int ordered = 100;
		
		//封装对象
		Brand brand = new Brand();
		brand.setStatus(status);
		brand.setCompanyName(companyName);
		brand.setBrandName(brandName);
		brand.setDescription(description);
		brand.setOrdered(ordered);
		
        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        //方式一
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //方式二  自动提交事务
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        brandMapper.add(brand);
        Integer id = brand.getId();
        System.out.println(id);
        //提交事务
        sqlSession.commit();
        //5.释放资源
        sqlSession.close();
    }
```

返回添加数据的主键
<insert useGeneratedKeys="true"keyProperty="id">

##### 4.修改

###### 4.1修改全部字段

1.编写接口方法：Mapper接口

- 参数：所有数据
- 结果：void

2.编写SQL语句：SQL映射文件
3.执行方法，测试

```java
	/**
     * 修改
     */
	
	int update(Brand brand);
```

```xml
<update id="update">
	update tb_brand
    set 
    brand_name=#{brandName},
    company_name=#{companyName},
    ordered=#{brandName},
    description=#{description},
    status=#{status}
    where id = #{id};
</update>
```

```java
    @Test
    public void testUpdate() throws IOException {
        //接收参数
        int status = 1;
        String companyName = "菠萝手机";
        String brandName = "菠萝";
        String description = "手机中的战斗机";
        int ordered = 200;
        int id = 5;
		
		//封装对象
		Brand brand = new Brand();
		brand.setStatus(status);
		brand.setCompanyName(companyName);
		brand.setBrandName(brandName);
		brand.setDescription(description);
		brand.setOrdered(ordered);
        brand.setId(id);
		
        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        //方式一
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //方式二  自动提交事务
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        int count = brandMapper.update(brand);
        System.out.println(count);
        //提交事务
        sqlSession.commit();
        //5.释放资源
        sqlSession.close();
    }
```

###### 4.2修改动态字段

1.编写接口方法：Mapper接口

- 参数：部分数据，封装到对象中
- 结果：void

2.编写SQL语句：SQL映射文件
3.执行方法，测试

```xml
<update id="update">
    update tb_brand
    <set>
        <if test="brandName !=null and brandName !=''>
            brand_name=#{brandName},
        </if>
        <if test="companyName !=null and companyName !=''>
            company_name=#{companyName,
        </if>
        <if test="ordered !=null">
            ordered=#{fordered},
        </if>
        <if test="description !=null and description !=''>
            description=#{description},
        </if>
        <if test="status !=null>
            status=#{status}
        </if>
    </set>
    where id #{id};
</update>
```

##### 5.删除

###### 5.1删除一个

1.编写接口方法：Mapper接口

- 参数：id
- 结果：void

2.编写SQL语句：SQL映射文件

3.执行方法，测试

```java
	void deleteById(int id);
```

```xml
<delete id="deleteById">
	delete from tb_brand where id = #{id};
</delete>
```

```java
    @Test
    public void testDeleteById() throws IOException {
        //接收参数
        int id = 6;

        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        //方式一
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //方式二  自动提交事务
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        brandMapper.deleteById(id);
        //提交事务
        sqlSession.commit();
        //5.释放资源
        sqlSession.close();
    }
```

###### 5.2批量删除

1.编写接口方法：Mapper接口

- 参数：id数组
- 结果：void

2.编写SQL语句：SQL映射文件

3.执行方法，测试

```java
void deleteByIds(@Param("ids")int[]ids);
```

mybatis会将数组参数，封装为一个Map集合。
				*默认：array=数组

​				*使用@Param注解改变map集合的默认key的名称

```xml
<delete id="deleteByIds">
	delete from tb_brand where id 
	in
		<foreach collection="array" separator="," open="(" close=")">
			#{id}
		</foreach>
	;
</delete>
```

```java
    @Test
    public void testDeleteByIds() throws IOException {
        //接收参数
        int ids = {5,7,8};

        //1.获取SqlSessionFactory
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        //方式一
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //方式二  自动提交事务
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        //3.获取Mapper接口的代理对象
        BrandMapper brandMapper = sqlSession.getMapper(BrandMapper.class);
        //4.执行方法
        brandMapper.deleteByIds(ids);
        //提交事务
        sqlSession.commit();
        //5.释放资源
        sqlSession.close();
    }
```

##### 6.MyBatis参数传递

MyBatis接口方法中可以接收各种各样的参数，MyBatis底层对于这些参数进行不同的封装处理方式

- 单个参数：

  1.POO类型：直接使用，属性名和参数占位符名称一致
  2.Map集合：直接使用，键名和参数占位符名称一到
  3.Collection:封装为Map集合

  ​	map.put("arg0",collection集合)；
  ​	map.put("collection",collection集合)；

  4.List:封装为Map集合

  ​	map.put("arg0",List集合)：
  ​	map.put("collection",List集合)；
  ​	map.put("List",List集合)；

  5.Array:封装为Map集合

  ​	map.put("argo",数组)；
  ​	map.put("array",数组)；

  6.其他类型：直接使用

- 多个参数：封装为Map集合

  map.put("arg0",参数值1)

  map.put("param1",参数值1)

  map.put("param2",参数值2)

  map.put("arg1",参数值2)

> MyBatisj提供了ParamNameResolver类来进行参数封装

```java
User select(String username,String password);
```

```xml
<select id="select"resultType="user">
    select *
    from tb_user
    where
    	username = #{arg0}
    and password = #{arg1}
</select>
```

##### 7.通过注解开发

使用注解开发会比配置文件开发更加方便

```java
@Select("select from tb_user where id =#{id}")
public User seectByld(int id);
```



- 查询：@Select
- 添加：@Insert
- 修改：@Update
- 删除：@Delete

提示：
		注解完成简单功能
		配置文件完成复杂功能

>​		使用注解来映射简单语句会使代码显得更加简洁，但对于稍微复杂一点的语句，Java注解不仅力不从心，还会让你本就复杂的SQL语句更加混乱不堪。因此，如果你需要做一些很复杂的操作，最好用XML来映射语句
>​		选择何种方式来配置映射，以及认为是否应该要统一映射语句定义的形式，完全取决于你和你的团队。换句话说，永远不要拘泥于一种方式，你可以很轻松的在基于注解和XML的语句映射方式间自由移植和切换

### HTML和CSS

#### 什么是HTML?

- HTML是一门语言，所有的网页都是用HTML这门语言编写出来的
- HTML(HyperText Markup Language):超文本标记语言

> ​				超文本：超越了文本的限制，比普通文本更强大。除了文字								信息，还可以定义图片、音频、视频等内容
> ​				标记语言：由标签构成的语言

- HTML运行在浏览器上，HTML标签由浏览器来解析

- HTML标签都是预定义好的。例如：使用<img>展示图片

- W3C标准：网页主要由三部分组成

  > 结构：**HTML**
  > 表现：**CSS**
  > 行为：**JavaScript**

#### 一.HTML

##### 1.快速入门

1.新建文本文件，后缀名改为.html
2.编写HTML结构标签
3.在<body>中定义文字

```html
<html>
    <head>
    	<title></title>
    </head>
    <body>
    	<font color = "red">乾坤未定,你我皆是黑马</font>
    </body>
</html>
```

##### 2.基础标签

| 标签      | 描述                               |
| --------- | ---------------------------------- |
| <h1>~<h6> | 定义标题，h1最大，h6最小           |
| <font>    | 定义文本的字体、字体尺寸、字体颜色 |
| <b>       | 定义粗体文本                       |
| <i>       | 定义斜体文本                       |
| <u>       | 定义文本下划线                     |
| <center>  | 定义文本居中                       |
| <p>       | 定义段落                           |
| <br>      | 定义折行                           |
| <hr>      | 定义水平线                         |

html表示颜色：
1.英文单词：red,pink,blue...
2.rgb(值1，值2，值3)：值的取值范围：0~255rgb(255,0,0)
3.#值1值2值了：值的范围：00~FF

###### 转义字符

| HTML原代码 | 现实结果 | 描述                   |
| ---------- | -------- | ---------------------- |
| &lt        | <        | 小于号或显示标记       |
| &gt        | >        | 大于号或显示标记       |
| &amp       | &        | 可用于显示其它特殊字符 |
| &quot      | "        | 引号                   |
| &reg       | ®        | 已注册                 |
| &copy      | ©        | 版权                   |
| &trade     | ™        | 商标                   |
| &nbsp      |          | 不断行的空白           |

##### 3.图片、音频、视频标签

| 标签    | 描述     |
| ------- | -------- |
| <img>   | 定义图片 |
| <audio> | 定义音频 |
| <video> | 定义视频 |

- img:定义图片

  > src:规定显示图像的URL(统一资源定位符)
  >
  > height:定义图像的高度
  > width:定义图像的宽度

- audio:定义音频。支持的音频格式：MP3、WAV、OGG

  > src:规定音频的URL
  > controls:显示播放控件

- video:定义视频。支持的音频格式：MP4,WebM、OGG

  > src:规定视频的URL
  > controls:显示播放控件

##### 4.超链接标签

| 标签 | 描述                             |
| ---- | -------------------------------- |
| <a>  | 定义超链接，用于链接到另一个资源 |

- href:指定访问资源的URL

- target:指定打开资源的方式

  >_seIf:默认值，在当前页面打开
  >_blank:在空白页面打开

##### 5.列表标签

| 标签 | 描述         |
| ---- | ------------ |
| <ol> | 定义有序列表 |
| <ul> | 定义无序列表 |
| <li> | 定义列表项   |

**有序列表**

![image-20221008142020977](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221008142020977.png)

**无序列表**

![image-20221008142043292](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221008142043292.png)

type:设置项目符号

##### 6.表格标签

| 标签    | 描述           |
| ------- | -------------- |
| <table> | 定义表格       |
| <tr>    | 定义行         |
| <td>    | 定义单元格     |
| <th>    | 定义表头单元格 |

- table:定义表格

  >border:规定表格边框的宽度
  >width:规定表格的宽度
  >cellspacing:规定单元格之间的空白

- tr:定义行

  >align:定义表格行的内容对齐方式

- td:定义单元格

  >rowspan:规定单元格可横跨的行数
  >
  >colspan:规定单元格可横跨的列数

##### 7.表格标签



| 标签   | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| <div>  | 定义HTML文档中的一个区域部分，经常与CSS一起使用，用来布局网页 |
| <span> | 用于组合行内元素。                                           |

##### 8.表单标签

- 表单：在网页中主要负责数据采集功能，使用<fom>标签定义表单

- 表单项（元素）：不同类型的input元素、下拉列表、文本域等

- form:定义表单

  > action：规定当提交表单时向何处发送表单数据，UL
  > method：规定用于发送表单数据的方式

  - get:浏览器会将数据直接附在表单的action URL
    之后。大小有限制
  - post:浏览器会将数据放到http请求消息体中。大
    小无限制

| 标签       | 描述                                 |
| ---------- | ------------------------------------ |
| <form>     | 定义表单                             |
| <input>    | 定义表单项，通过type属性控制输入形式 |
| <label>    | 为表单项定义标注                     |
| <select>   | 定义下拉列表                         |
| <option>   | 定义下拉列表的列表项                 |
| <textarea> | 定义文本域                           |

##### 9.表单项标签

![image-20221008225456705](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221008225456705.png)

![image-20221008223511359](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221008223511359.png)





#### 二.CSS

##### 什么是CSS?

- CSS是一门语言，用于控制网页表现

​	   CSS(Cascading Style Sheet):层叠样式表

- W3C标准：网页主要由三部分组成

>结构：HTML
>表现：CSS
>行为：JavaScript

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Title</title>
	<style>
		div{
			color:red;
		}
	</style>
</head>
<body>

<div>Hello CSS~</div>

</body>
</html>
```

##### 1.CSS导入方式

CSS导入HTML有三种方式：

> 1.内联样式：在标签内部使用style属性，属性值是css属性键值对
>
> ```html
> <div style="color:red">Hello CSS~</div>
> ```
>
> 2.内部样式：定义<style>标签，在标签内部定义css样式
>
> ```html
> <style type="text/css">
>     div{
>     	color:red;
>     }
> </style>
> ```
>
> 3.外部样式：定义ink标签，引入外部的css文件
>
> ```html
> <link rel="stylesheet"href="demo.css">
> ```
>
> demo.css
>
> ```css
> div{
> 	color:red;
> }
> ```

##### 2.CSS选择器

###### 2.1概念：选择器是选取需设置样式的元素（标签）

```css
div{
	color:red;
}
```

###### 2.2分类

2.2.1元素选择器

```
元素名称{color:red;}
 div{color:red;}
```

2.2.2id选择器

```html
#id属性值{color:red;}

#name{color:red;)
<div id="name">hello css2</div>
```

2.2.3类选择器

```html
.class属性值{color:red;}

.cls{color:red;}
<div class="cls">hello css3</div>
```

### JS

#### 什么是JavaScript?

- JavaScript是一门跨平台、面向对象的脚本语言，来控制网页行为的，它能使网页可交互

- W3C标准：网页主要由三部分组成

  > 结构：**HTML**
  > 表现：**CSS**
  > 行为：**JavaScript**

- JavaScript和Java是完全不同的语言，不论是概念还是设计。但是基础语法类似。

- JavaScript(简称：JS)在1995年由Brendan Eich发明，并于1997年成为一部ECMA标准

- ECMAScript6(ES6)是最新的JavaScript版本（发布于2015年）：

#### 一.JS引入

##### 1.两种引入

1.1内部脚本：将JS代码定义在HTML页面中

在HTML中，JavaScript代码必须位<script>与</script>标签之间

```js
<script>
	alert("hello,JS~");
</script>
```

提示：

- 在HTML文档中可以在任意地方，放置任意数量的<script>。
- 一般把脚本置于<body>元素的底部，可改善显示速度，因为脚本执行会拖慢显示

1.2外部脚本：将JS代码定义在外部S文件种，然后引入到HTML页面中

- 外部文件：demo.js 	alert("hello,JS~");
- 引入外部js文件            <script src="../js/demo.js></script>

注意：
1.外部脚本不能包含<script>标签
2.<script>标签不能自闭合

#### 二.JS基础语法

##### 1.书写语法

1. 区分大小写：与va一样，变量名、函数名以及其他一切东西都是区分大小写的
2. 每行结尾的分号可有可无
3. 注释：
   - 单行注释：//注释内容
   - 多行注释：/*     */注释内容
4. 大括号表示代码块

```js
if (count =3){
	alert(count);
}
```

##### 2.输出语句

- 使用window.alert()写入警告框
- 使用document.write()写入HTML输出
- 使用console.1og()写入浏览器控制台

```js
window.alert("hello JS~");//弹出警告框
document.write("hello JS~");//写入HTML
console.log("hello JS~");//写入控制台
```

##### 3.变量

- JavaScript中用var关键字(varable的缩写)来声明变量

```js
	var test = 20;
	test = "张三";
```

var:

​		1.作用域:全局变量

​		2.变量可重复定义

- JavaScript是一门弱类型语言，变量可以存放不同类型的值
- 变量名需要遵循如下规则

>组成字符可以是任何字母、数字、下划线（_)或美元符号($)
>数字不能开头
>建议使用驼峰命名

- ECMAScript6新增了**Iet**关键字来定义变量。它的用法类似于**var**,但是所声明的变量，只在**Iet**关键字所在的代码块内有效，且不允许重复声明

- ECMAScript6新增了**const**关键字，用来声明一个只读的常量。一旦声明，常量的值就不能改变。

##### 4.数据类型

JavaScript中分为：原始类型和引用类型

>5种原始类型：
>**number**:数字（整数、小数、NaN(Not a Number)
>**string**:字符、字符串，单双引皆可
>**boolean**:布尔。true,false
>**null**:对象为空
>**undefined**:当声明的变量未初始化时，该变量的默认值是undefined

使用typeof运算符可以获取数据类型

```js
alter(typeof age);
```

##### 5.运算符

- 一元运算符：++，--
- 算术运算符：+，-，*，/，%
- 赋值运算符：=,+=,-=…
- 关系运算符：>，<，>=，<=，!=，==,===
- 逻辑运算符：&&，||，！
- 三元运算符：条件表达式？true_value:false_value

>== :
>
>1.判断类型是否一样，如果不一样，则进行类型转换
>2.再去比较其值
>
>===:全等于
>
>1.判断类型是否一样，如果不一样，直接返回faLs
>2.再去比较其值

>类型转换:
>
>​	*其他类型转为number:
>
>​		1.string:按照字符串的字面值，转为数字,如果字面值不是		数字，则转为NaN。一般使用parseInt
>​		2.boolean:true转为1，false转为0
>
>​	*其他类型转boolean:
>
>​		1.number:0和NaN转为false,其他的数字转为trUe
>
>​		2.string:空字符串转为false,其他的字符串转为true
>
>​		3.null:false
>
>​		4.undefined:false

#### 三.流程控制语句&函数

##### 1.流程控制语句

###### 1.1if:

```js
    var count 3;
    if (count ==3){
    	alert(count);
    }
```

###### 1.2switch:

```js
    var num =3;
    switch (num){
        case 1:{
            alert("星期一")；
            break;
    	}
        case 2:{
            alert("星期二")；
            break;
        }
        case 3:{
        alert("星期三")；
        break;
        }
        case 4:{
        alert("星期四")；
        break;
        }
        case 5:{
        alert("星期五")；
        break;
        }
        case 6:{
        alert("星期六")；
        break;
        }        
        case 7:{
        alert("星期日")；
        break;
        }
        default:{
        	alert("输入星期有误");
        	break;
        }
    }
```



###### 1.3for:

```js
	var sum 0;
    for(let i=1;i<=100;i++){
        sum +=i;
        }
    }
    alert(sum);
```



###### 1.4while:

```js
    var sum =0;
    var i = 1;
    while (i<=100){
        sum +i;
        i++;
    }
    alert(sum);
```



###### 1.5do...while:

```js
    var sum = 0;
    var i = 1;
    do{
		sum +i;
    	i++;
    }
    while (i<=100);
    alert(sum);
```

##### 2.函数

函数（方法）是被设计为执行特定任务的代码块

定义一:JavaScript函数通过function关键词进行定义，语法为：

```js
function functionName(参数1，参数2....){
	要执行的代码
}
```

注意：

形式参数不需要类型。因为JavaScript是弱类型语言
返回值也不需要定义类型，可以在函数内部直接使用return:返回即可

定义方式一:

```js
function add(a,b){
	return a+b;
}
```

调用：函数名称（实际参数列表）；

```
let result = add(1,2);
```

定义二:

```js
var functionName=function(参数列表){
	要执行的代码
}
```

```js
var add function (a,b){
	return a b;
}
```

调用:JS中，函数调用可以传递任意个数参数

```js
let result add(1,2,3);
```

#### 四.JS对象

##### 1.Array数组对象

JavaScript Array对象用于定义数组

- 定义

```js
var 变量名 = new Array(元素列表);	//方式一
var 变量名 = [元素列表];			//方式二 
```

- 访问

```js
arr[索引] = 值;
arr[0] = 1;
```

- 注意：Js数组类似于Java集合，长度，类型都可变

```js
//变长
var arr3=[1,2,3];
arr3[10]=10;
//alert(arr3[10]);
alert(arr3[9]);
//变类型
arr3[5]="hello";
//alert(arr3[5]);
alert(arr3);
```

- 属性

属性：Length:数组中元素的个数

```js
var arr4=[1,2,3];
for (let i=0;i<arr4.Length;i++){
	alert(arr4[i]);
}
```

- 方法

push方法:添加方法

```js
var arr5=[1,2,3];
arr5.push(10);
alert(arr5);
```

splice:删除元素

```js
arr5.splice(0,1);//这里的方法重载,能传3个参数
alert(arr5);
```

##### 2.String

- 定义

```js
var变量名=new String(s);	//方式-
var变量名=s;			 	//方式二
```

- 属性

length		字符串的长度

- 方法

charAt()						 返回在指定位置的字符。
indexof()					   检索字符串。
trim()							 去除字符串前后两端的空白字符

##### 3.自定义对象

- 格式

```
var对象名称={
    属性名称1：属性值1，
    属性名称2：属性值2，
    ......
    函数名称：function(形参列表){}
    ......
};

var person ={
    name:"zhangsan",
    age:23,
    eat:function {
    	alert("干饭~")；
    }
}
```

#### 五.BOM

- **B**rowser **O**bject Model浏览器对象模型

- JavaScript将浏览器的各个组成部分封装为对象

- 组成Window:浏览器窗口对象

- 组成

  >- Window:浏览器窗口对象
  >- Navigator:浏览器对象
  >- Screen:屏幕对象
  >- History:历史记录对象
  >- Location:地址栏对象



##### 1.Window

- Vindow:刘览器窗口对象
- 获取：直接使用window,其中window.可以省略

```js
window.alert("abc");
```

- 属性：获取其他BOM对象

| history   | 对History对象的只读引用。请参数History对象。       |
| --------- | -------------------------------------------------- |
| Navigator | 对Navigator对象的只读引用。请参数Navigator对象。   |
| Screen    | 对Screen对象的只读l用。请参数Screen对象：          |
| location  | 用于窗口或框架的Location对象。请参阅Location对象。 |

- 方法

| alert()       | 显示带有一段消息和一个确认按钮的警告框。           |
| ------------- | -------------------------------------------------- |
| confirm()     | 显示带有一段消息以及确认按钮和取消按钮的对括框。   |
| setInterval() | 按照指定的周期（以毫秒计）来调用函数或计算表达式。 |
| setTimeout()  | 在指定的毫秒数后调用函数或计算表达式。             |

##### 2.History

- History:历史记录
- 获取:使用window.history获取,其中window可以省略

```js
window.history.方法();
history.方法();
```

- 方法

| back()    | 加载history列表中的前一个URL。 |
| --------- | ------------------------------ |
| forward() | 加载history列表中的下一个URL。 |

#### 六.DOM

- **D**ocument **O**bject **M**odel文档对象模型

- 将标记语言的各个组成部分封装为对象

  >- Document:整个文档对象
  >- Element:元素对象
  >- Attribute:属性对象
  >- Text:文本对象
  >- Comment:注释对象

```js
<html>
    <head>
    	<title>文档标题</title:>
    </head>
    <body>
    	<h1>我的标题<h1>
    	<a href仁"#">我的链接</a>
    </body>
</html>
```



![image-20221011211644458](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221011211644458.png)

- JavaScript通过DOM,就能够对HTML进行操作了

  >- 改变HTML元素的内容
  >- 改变HTML元素的样式(CSS)
  >- 对HTML DOM事件作出反应
  >- 添加和删除HTML元素

- DOM是W3C(万维网联盟)的标准

- DOM定义了访问HTML和ML文档的标准：

- W3CDOM标准被分为3个不同的部分：

  >1.核心DOM:针对任何结构化文档的标准模型
  >
  >>- Document:整个文档对象
  >>- Element:元素对象
  >>- Attribute:属性对象
  >>- Text:文本对象
  >>- Comment:注释对象
  >
  >2.XML DOM:针对XML文档的标准模型
  >
  >3.HTML DOM:针对HTML文档的标准模型
  >
  >>- Image:<img>
  >>- Button <input type='button'>

##### 1.获取Element

- 获取：使用Document)对象的方法来获取

1.getElementByld:根据id属性值获取，返回一个Element对象
2.etElementsByTagName:根据标签名称获取，返回Element对象数组

>style:设置元素css样式
>innerHTML:设置元素内容
>
>```js
>divs[i].innerHTML="呵呵"；
>```

3.getElementsByName:根据name属性值获取，返回Element>对象数组
4.getElementsByClassName:根据class/属性值获取，返回Element对象数组

#### 七.事件监听

- 事件：HTML事件是发生在HTML元素上的"事情”。比如：

  >- 按钮被点击
  >- 鼠标移动到元素之上
  >- 按下键盘按键

- 事件监听:JavaScript可以在事件被侦测到时执行代码

##### 1.事件绑定

- 两种方式

方式一：通过HTML标签中的事件属性进行绑定

```
<input type="button"onclick='on()'>
function on{
	alert("我被点了")；
}
```

方式二:通过DOM元素属性绑定

```JS
<input type="button"id="btn">

document.getElementByld("btn").onclick=function(){
	alert("我被点了")：
}
```

##### 2.常见事件

| 事件名      | 说明                     |
| ----------- | ------------------------ |
| onclick     | 鼠标单击事件             |
| onblur      | 元素失去焦点             |
| onfocus     | 元素获得焦点             |
| onload      | 某个页面或图像被完成加载 |
| onsubmit    | 当表单提交时触发该事件   |
| onkeydown   | 某个键盘的键被按下       |
| onmouseover | 鼠标被移到某元素之上     |
| onmouseout  | 鼠标从某元素移开         |

Event代表事件对象

#### 八.RE表达式

- 概念:正则表达式定义了字符串组成的规则

- 定义

  >1.直接量：注意不要加引号
  >
  >```reStructuredText
  >var reg = /^\w{6,12}$/;
  >```
  >
  >2.创建RegExp对象
  >
  >```reStructuredText
  >var reg = new RegExp{"Aw6,12)$"};
  >```

- 方法

  >- test(str):判断指定字符串是否符合规侧，返回true或false

- 语法

  >- ^:表示开始
  >- $:表示结束
  >- []:代表某个范围内的单个字符，比如：[0-9]单个数字字符
  >- .:代表任意单个字符，除了换行和行结束符
  >- \w:代表单词字符：字母、数字、下划线(_)，相当于[A-Za-z0-9_]
  >- \d:代表数字字符：相当于[0-9]
  >- 量词：
  >- +:至少一个  var reg = /^\w+$/;
  >- *:零个或多个
  >- ?:零个或一个
  >- {x}:x个
  >- {m,}:至少m个
  >- {m,n}:至少m个，最多n个

## Web

### Java技术栈

- B/S架构：Browser/Server,浏览器/服务器架构模式，它的特点是，客户端只需要浏览器，应用程序的逻辑和数据都存储在服务器端。浏览器只需要请求服务器，获取Wb资源，服务器把Wb资源发送给浏览器即可

  >- 好处：易于维护升级：服务器端升级后，客户端无需任何部署就可以使用到新的版本

![image-20221013094052473](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013094052473.png)

- 静态资源：HTML、CSS、JavaScript、图片等。负责页面展现
- 动态资源：Servlet、JSP等。负责逻辑处理

- 数据库:负责存储数据
- HTTP协议:定义通信规则
- Web服务器:负责解析HTTP协议,解析请求数据,并发送响应数据

#### 一.HTTP

- 概念:HyperText Transfer Protocol,超文本传输协议，规定了浏览器和服务器之间数据传输的规则

![image-20221013095242136](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013095242136.png)

- HTTP协议特点

1. 基于TCP协议：面向连接，安全

2. 基于请求-响应模型的：一次请求对应一次响应

3. HTTP协议是无状态的协议：对于事务处理没有记忆能力。每次请求-响应都是独立的。

   缺点：多次请求间不能共享数据。	Java中使用会话技术(Cookie、Session)来解决这个问题
   优点：速度快

##### 1.请求数据的格式

- 请求数据分为3部分：
  1. **请求行**：请求数据的第一行。其中GET表示请求方式，/表示请求资源路径，HTTP/1.1表示协议版本
  2. **请求头**：第二行开始，格式为key:value形式。
  3. **请求体**：POST请求的最后一部分，存放请求参数

- 常见的HTTP请求头：

  >- Host:表示请求的主机名
  >- User-Agent:.浏览器版本，例如Chrome浏览器的标识类似Mozilla/5.0 Chrome/79,IE浏览器的标识类似Mozilla/5.0(Windows NT)like Gecko;
  >- Accept:表示浏览器能接收的资源类型，如text/*,image/*或者*/*表示所有；
  >- Accept-Language:表示浏览器偏好的语言，服务器可以据此返回不同语言的网页；
  >- Accept-Encoding:表示浏览器可以支持的压缩类型，例如gzip,deflate等。

- GET请求和POST请求区别：
  1.GET请求请求参数在请求行中，没有请求体。
     POST请求请求参数在请求体中
  2.GET请求请求参数大小有限制，POST没有

##### 2.响应数据格式

- 响应数据分为3部分：

  > 1.**响应行**：响应数据的第一行。其中HTTP/1.1表示议版
  > 本，200表示响应状态码，OK表示状态码描述
  > 2.**响应头**：第二行开始，格式为key:value形式
  > 3.**响应体**：最后一部分。存放响应数据

- 常见的HTTP响应头：

  > - Content-Type:表示该响应内容的类型，例如text/html,image/jpeg;
  > - Content-Length:表示该响应内容的长度（字节数）：
  > - Content-Encoding:表示该响应压缩算法，例如gzip;
  > - Cache-Control:指示客户端应如何缓存，例如max-age=300
  > - 表示可以最多缓存300秒

###### 2.1状态码大类

| 状态码分类 | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| 1XX        | **响应中**一一临时状态码，表示请求已经接受，告诉客户端应该继续请求或者如果它已经完成则忽略它 |
| 2XX        | **成功**一一表示请求已经被成功接收，处理已完成               |
| 3XX        | **重定向**一一重定向到其它地方：它让客户端再发起一个请求以完成整个处理。 |
| 4XX        | 客户端错误一一处理发生错误，责任在客户端，如：客户端的请求一个不存在的资源，客户端未被授权，禁止访问等 |
| 5XX        | 服务器端错误一一处理发生错误，责任在服务端，如：服务端抛出异常，路由出错，HTTP版本不支持等 |

###### 2.2常见的响应状态码

| 状态码  | 英文描述                            | 解释                                                         |
| ------- | ----------------------------------- | ------------------------------------------------------------ |
| **200** | **OK**                              | 客户瑞请求成功，即**处理成功**，这是我们最想看到的状态码     |
| 302     | **Found**                           | 指示所请求的资源已移动到由Location响应头给定的URL,浏览器会自动重新访问到这个页面 |
| 304     | **Not Modified**                    | 告诉客户端，你请求的资源至上次取得后，服务端并未更改，你直接用你本地缓存吧。隐式重定向 |
| 400     | **Bad Request**                     | 客户端请求有**语法错误**，不能被服务器所理解                 |
| 403     | **Forbidden**                       | 服务器收到请求，但是**拒绝提供服务**，比如：没有权限访问相关资源 |
| **404** | **Not Found**                       | **请求资源不存在**，一般是URL输入有误，或者网站资源被删除了  |
| 428     | **Precondition Required**           | **服务器要求有条件的请求**，告诉客户端要想访问该资源，必须携带特定的请求头 |
| 429     | **Too Many Requests**               | **太多请求**，可以限制客户端请求某个资源的数量，配合Retry-After(多长时间后可以请求)响应头一起使用 |
| 431     | **Request Header Fields Too Large** | **请求头太大**，服务器不愿意处理请求，因为它的头部字段太大。请求可以在减少请求头域的大小后重新提交。 |
| 405     | **Method Not Allowed**              | 请求方式有误，比如应该用GET请求方式的资源，用了POST          |
| **500** | **Internal Server Error**           | **服务器发生不可预期的错误。**服务器出异常了，赶紧看日志去吧 |
| 503     | **Service Unavaiable**              | **服务器尚未准备好处理请求**，服务器刚刚启动，还未初始化好   |
| 511     | **Network Authentication Required** | **客户端需要进行身份验证才能获得网络访问权限**               |

#### 二.Web服务器

- Web服务器是一个应该程序（软件），对HTTP协议的操作进行封装，使得程序员不必直接对协议进行操作，让Wb开发更加便捷。主要功能是“提供网上信息浏览服务”

>1.Web服务器作用？
>	封装HTTP协议操作，简化开发
>	可以将web项目部署到服务器中，对外提供网上浏览服务
>2.Tomcat是一个轻量级的Web服务器，支持Servlet/小SP少量
>JavaEE规范，也称为Web容器，Servlet容器

##### 1.Tomcat简介

- 概念:Tomcat是Apache软件基金会一个核心项目，是一个开源免费的轻量级Web服务器，支持Servlet/JSP少量JavaEE规范。
- JavaEE:Java Enterprise Edition,Java企业版。指Java企业级开发的技术规范总和。包含13项技术规范：JDBC、JNDl、EJB、RMl、JSP、Servlet、XML、JMS、Java IDL、JTS、JTA、JavaMail、JAF
- Tomcat也被称为Web容器、Servlet容器。Servlet需要依赖于Tomcat才能运行
- 官网:https://tomcat.apache.org/

##### 2.Tomcat基本使用

- 下载：官网下载
- 安装：绿色版，直接解压即可
- 卸载：直接删除目录即可
- 启动：双击：bin\startup.bat

![image-20221013111255834](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013111255834.png)

![image-20221013111233595](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013111233595.png)

![image-20221013111323271](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013111323271.png)

![image-20221013111343084](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013111343084.png)

- 关闭：

  > 1.直接×掉运行窗口：强制关闭

  > 2.bin\shutdown.bat:正常关闭

  > 3.Ctrl+C:正常关闭

##### 3.配置

- 配置

>1.修改启动端口号:config/server.xml
>
>```xml
><Connector port="8080"protocol="HTTP/1.1"
>		   connectionTimeout="20000"
>		   redirectPort="8443"/>
>```
>
>注：HTTP协议默认端口号为80，如果将Tomcati端口号改为80，则将来访问Tomcat时，将不用输入端口号

- 启动时可能出现的问题：

>1.端口号冲突：找到对应程序，将其关闭掉
>
>![image-20221013154044325](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013154044325.png)
>
>2.启动窗口一闪而过：检查JAVA_HOME环境变量是否正确配置

##### 4.部署项目

- Tomcat部署项目：
  将项目放置到webapps目录下，即部署完成

- 一般JavaWeb项目会被打成**war**包，然后将war包放到webapps目录下，Tomcats会自动解压缩war文件

![image-20221013154451881](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013154451881.png)

##### 5.Web项目结构

###### 5.1IDEA创建Maven Web项目

- Web项目结构:

![image-20221013155223638](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013155223638.png)

- 编译后的ava字节码文件和resources的资源文件，放到WEB-lNF下的classes目录下
- pom.xml中依赖坐标对应的jar包，放入WEB-NF下的Iib目录下



- 使用骨架

> - 骨架:项目模板

1.选择web项目骨架，创建项目

![image-20221013185233785](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185233785.png)

2.删除pom.xml中多余的坐标

![image-20221013185312804](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185312804.png)

3.补齐缺失的目录结构

![image-20221013185553883](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185553883.png)

![image-20221013185609664](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185609664.png)



- 不使用骨架

1.选择web项目骨架，创建项目

![image-20221013185740554](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185740554.png)

此处不勾选

2.pom.xml中添加打包方式为war

![image-20221013185834181](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185834181.png)

3.补齐缺失的目录结构：webapp

![image-20221013185420694](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185420694.png)



![image-20221013185441540](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185441540.png)

![image-20221013185459360](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185459360.png)

![image-20221013185512853](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013185512853.png)

##### 6.IDEA中使用Tomcat

###### 6.1集成本地Tomcat

- 将本地Tomcat集成到ldea中，然后进行项目部署即可

![image-20221013191303224](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013191303224.png)

###### 6.2Tomcat Maven插件

- pom.xml添加Tomcat插件

![image-20221013194438231](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013194438231.png)

- 使用Maven Helper插件快速启动项目，选中项目，右键->Run Maven->tomcat7:run

![image-20221013194504837](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221013194504837.png)

## Servlet

- Servlet是Java提供的一门动态web资源开发技术
- Servlet是avaEE规范之一，其实就是一个接口，将来我们需要定义Servlet类实现Servlet接口，并由web服务器运行Servlet

### 一.入门

#### 1.快速入门

- 创建web项目，导入Servlet依赖坐标

```xml
<dependency>
    <groupld>javax.servlet</groupld>
    <artifactld>javax.servlet-api</artifactld>
    <version>3.1.0</version>
    <scope>provided</scope>
</dependency>
```

- 创建：定义一个类，实现Servlet接口，并重写接口中所有方法，并在service方法中输入一句话

````java
public class ServletDemo1 implements Servlet{
	public void service(){}
}
````

- 配置：在类上使用@WebServlet注解，配置该Servlet的访问路径

```java
@WebServlet("/demo1")
public class ServletDemo1 implements Servlet{}
```

- 访问：启动Tomcat,浏览器输入URL访问该Servlet

```html
http://localhost:8080/web-demo/demo1
```

#### 2.执行流程

![image-20221014113508871](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221014113508871.png)

##### 2.1Servlet由谁创建？Servlet方法由谁调用？

Servlet由web服务器创建，Servlet方法由web服务器调用。

##### 2.2服务器怎么知道Servlet中一定有service方法？

因为我们自定义的Servlet,必须实现Servlet接口并复写其方法，而Servlet接口中有service方法

### 二.流程

#### 1.生命周期

- 对象的生命周期指一个对象从被创建到被销毁的整个过程

![image-20221014113914318](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221014113914318.png)

- Servleti运行在Servlet容器(web服务器)中，其生命周期由容器来管理，分为4个阶段：

  >1.**加载和实例化**：默认情况下，当Servlet?第一次被访问时，由容器创建Servlet对象
  >
  >2**.初始化**：在Servlet实例化之后，容器将调用Servlet的**init()**方法初始化这个对象，完成一些如加载配置文件、创建连接等初始化的工作。该方法只**调用一次**
  >
  >3.**请求处理**：**每次**请求Servlet时，Servlet容器都会调用Servlet的**service()**方法对请求进行处理。
  >
  >4.**服务终止**：当需要释放内存或者容器关闭时，容器就会调用Servlet实例的destroy()方法完成资源的释放。在destroy()方法调用之后，容器会释放这个Servlet实例，该实例随后会被Java的垃圾收集器所回收

```java
@WebServlet(urlPatterns = "/demo",loadOnStartup =1)
```

- 负整数：第一次被访问时创建Servlet对象
- 0或正整数：服务器启动时创建Servlet对象数字越小优先级越高

```java
/**
 *初始化方法
 *1.调用时机：默认情况下，Servlet被第一次访问时，调用
 *		*loadOnStartUp:
 *2.调用次数：1次
 *@param config
 *@throws ServletException
 */
 @override
 public void init(ServletConfig config)throws ServletException{
 	System.out.println("init...");
 }
```

```java
/**
 *提供服务
 *1.调用时机：每一次ServLet被访问时，调用
 *2.调用次数：多次
 *
 *@param reg
 *@param res
 *@throws ServletException
 *@throws IOException
*/
 @override
 public void service(ServletRequest req,ServletResponse res)throws ServletException,IOException{
 	System.out.println("servlet hello world~");
 }

```

```
/**
 *销毁方法
 *1.调用时机：内存释放或者服务器关闭的时候，Servlet对象会被销毁，调用
 *2.调用次数：1次
 */
 @override
 public void destroy(){
 	System.out.println("destroy...");
}
```

#### 2.方法介绍

- 初始化方法，在Servleti被创建时执行，只执行一次

  ```java
  void init(ServletConfig config)
  ```

- 提供服务方法，每次Servleti被访问，都会调用该方法

  ```java
  void service(ServletRequest req,ServletResponse res)
  ```

- 销毁方法，当Servlet被销毁时，调用该方法。在内存释放或服务器关闭时销毁Servlet

  ```
  void destroy()
  ```

- 获取ServletConfig对象
  ```java
  ServletConfig getServletConfig()
  ```

- 获取Servlet信息
  ```java
  String getServletInfo()
  ```

#### 4.体系结构 

![image-20221014171415209](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221014171415209.png)

我们将来开发B/S架构的web项目，都是针对HTTP协议,所以我们自定义Servlet,会继承**HttpServlet**

![image-20221014171514348](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221014171514348.png)

#### 5.urlPattern配置

- Servlet要想被访问，必须配置其访问路径(urlPattern)

  >1.一个Servlet,可以配置多个
  >
  >```java
  >urlPattern@Webservlet(urlPatterns ={"/demo1","/demo2"})
  >```
  >
  >2.urlPattern配置规则
  >①精确匹配
  >
  >```java
  >配置路径：@WebServlet("/user/select")
  >访问路径：localhost:8080web-demo/user/select
  >```
  >
  >②目录匹配
  >
  >```java
  >配置路径：WebServlet("/user/*")
  >		localhost:8080/web-demd/user/aaa
  >访问路径：
  >		localhost:8080/web-demo/user/bbb 
  >```
  >
  >③扩展名匹配
  >
  >```java
  >配置路径：@WebServlet("*.do")
  >    	localhost:8080/web-demd/aaa.do
  >访问路径:
  >		localhost:8080/web-demo/bbb.do
  >```
  >
  >④任意匹配
  >
  >```java
  >		@WebServlet("/")
  >配置路径：
  >		@WebServlet("/*")
  >		
  >		localhost:8080/web-demd/hehe
  >访问路径：
  >		localhost:8080/web-demo/haha
  >```

> /和/*区别：
> 当我们的项目中的Servleti配置了"/”，会覆盖掉tomcat中的
> DefaultServlet,当其他的url-pattern都匹配不上时都会走这
> 个Servlet
>
> 当我们的项目中配置了“/*”，意味着匹配任意访问路径

#### 6.XML配置方式编写Servlet

- Servlet从3.0版本后开始支持使用注解配置，3.0版本前只支持XML配置文件的配置方式

- 步骤

  >1.编写Servlet类
  >2.在web.xml中配置该Servlet
  >
  >```xml
  ><servlet>
  >    <servlet-name>demo5</servlet-name>
  >    <servlet-class>com.itheima.web.servlet.ServletDemo5</servlet-class>
  ></servlet>
  ><servlet-mapping>
  >    <servlet-name>demo5</servlet-name>
  >    <url-pattern>/demo5</url-pattern>
  ></servlet-mapping>
  >```

## Request&Response

![image-20221015084537789](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015084537789.png)

- Request:获取请求数据
- Response:设置响应数据

### 一.Request对象

#### 1.Request继承体系

![image-20221015095402692](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015095402692.png)

- Tomcat需要解析请求数据，封装为requestx对象并且创建requestx对象传递到service方法中
- 使用request对象，查阅JavaEE API文档的HttpServletRequest接口

#### 2.Request获取请求数据

##### 2.1获取请求数据

- 请求数据分为3部分:

  >1.请求行:
  >
  >GET /request-demo/req1?username=zhangsan HTTP/1.1
  >
  >- String getMethod():获取请求方式：GET
  >- String getContextPath():获取虚拟目录（项目访问路径）：/request-demo
  >- StringBuffer getRequestURL0:获取URL(统一资源定位符)：http:/localhost:8080/request-demo/req1
  >- String getRequestURI():获取URI(统一资源标识符)：/request-demo/req1
  >- String getQueryString() :获取请求参数(GET方式)：username=zhangsan&password=123
  >
  >2.请求头
  >
  >User-Agent:Mozilla/5.0 Chrome/91.0.4472.106
  >
  >- String getHeader(String name):根据请求头名称，获取值
  >
  >- 
  >
  >3.请求体
  >
  >username=superbaby&password=123
  >
  >- ServletInputStream getlnputStream():获取字节输入流
  >- BufferedReader getReader(():获取字符输入流

##### 2.2通用方式获取请求参数

- 请求参数获取方式

  >get方式:
  >
  >String getQueryString()
  >
  >
  >
  >post方式:
  >
  >BufferedReader getReader()

##### 思考：

GET请求方式和POST请求方式区别主要在于获取请求参数的方式不一样，是否可以提供一种**统一**获取请求参数的方式，从而**统一**doGet和doPost方法内的代码？

#### 3.Request通用方式获取请求参数

![image-20221015104523429](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015104523429.png)

- Map<String,String[]>getParameterMap():获取所有参数Map集合
- String[]getParameterValues(String name):根据名称获取参教值（数组）
- String getParameter(String name):根据名称获取参数值（单个值）



- 使用通用方式获取请求参数后，屏蔽了GET和POST的请求方式代码的不同，则代码可以定义为如下格式：

  >```java
  >@WebServlet("/reqDemo3")
  >public class RequestDemo3 extends HttpServlet{
  >	@override
  >	protected void doGet(HttpServletRequest req,HttpServletResponse resp){
  >	
  >	}
  >	@override
  >	protected void doPost(HttpServletRequest req,HttpServletResponse resp){
  >	this.doGet(req,resp);
  >	}
  >}
  >```



- 可以使用Servlet模板创建Servlet更高效

![image-20221015111250096](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015111250096.png)

##### 若是没有new Servlet选项

1. 在pom.xml文里导入servlet得依赖
   ![image-20221015132441685](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015132441685.png)
2. 在File里的Project Structure找到Modules
   ![image-20221015132704638](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015132704638.png)
3. 点击Dependencies勾选servlet-api的选项
   ![image-20221015132818874](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015132818874.png)

- 若想改变模板的格式

![image-20221015133518929](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015133518929.png)

#### 4.Request请求参数中文乱码

- 请求参数如果存在中文数据，则会乱码

```java
//POST的乱码
//1.解决乱码：PoST的底层实现是getReader
request.setCharacterEncoding("UTF-8");//设置字符输入流的编码

//要先设置编码格式,否则后续仍然会中文乱码

//2.获取username
String username = request.getParameter("username");
System.out.println(username);

//GET的乱码
//1.GET,获取参数的方式：getQuerystring
//乱码原因：tomcat进行URL解码，默认的字符集IS0-8859-1
//1.1先对乱码数据进行编码：转为字节数组
username.getByte(StandardCharsets.IS0_8859_1);
//1.2字节数组解码
username = new String(bytes,StandardCharsets.ISO_8859_1)
//1.1和1.2可合为一行
username = new String(username.getBytes((StandardCharsets.ISO_8859_1),StandardCharsets.ISO_8859_1);
```

- get的乱码原因

![image-20221015135515956](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015135515956.png)

- URL编码
  >1.将字符串按照编码方式转为二进制
  >2.每个字节转为2个16进制数并在前边加上%
  >
  >![image-20221015135803178](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015135803178.png)

- 解决方案:

  >POST:设置输入流的编码
  >
  >```java
  >req.setCharacterEncoding("UTF-8");
  >```
  >
  >通用方式(GET/POST):先编码，再解码
  >
  >new String(username.getBytes("ISO-8859-1"),"UTF-8");

**Tomcat8.0之后，已将GET请求乱码问题解决，设**
**置默认的解码方式为UTF-8**

#### 5.Request请求转发

- 请求转发(forward):一种在服务器内部的资源跳转方式

![image-20221015141804163](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015141804163.png)

- 实现方式

```java
req.getRequestDispatcher(("资源B路径").forward(req,resp);
```

- 请求转发资源间共享数据：使用Request对象
  >- void setAttribute(String name,Object o):存储数据到request域中
  >- Object getAttribute(String name):根据key,获取值
  >- void removeAttribute(String name):根据key,
  >  删除该键值对

- 请求转发特点：
  >浏览器地址栏路径不发生变化
  >只能转发到当前服务器的内部资源
  >一次请求，可以在转发的资源间使用request共享数据

### 二.Response对象

#### 1.Response设置响应数据功能介绍

- 响应数据分为3部分

  >1.响应行：
  >
  >HTTP/1.1 200 OK
  >
  >- void setStatus(int sc):设置响应状态码
  >
  >2.响应头：
  >
  >Content-Type:text/html
  >
  >- void setHeader((String name,String value):设置响应头键值对
  >
  >3.响应体：
  >
  ><html><head>head><body></body></html>
  >
  >- PrintWriter getWriter():获取字符输出流
  >- ServletOutputStream getQutputStream():获取字节输出流

#### 2.Response完成重定向

- 重定向(Redirect):一种资源跳转方式

![image-20221015143524237](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221015143524237.png)

- 实现方式：

```java
resp.setStatus(302);
resp.setHeader("location",“资源B的路径")；
```

```java
resp.sendRedirect("资源B的路径")；
```

- 重定向的特点
  >浏览器地址栏路径发生变化
  >可以重定向到任意位置的资源（服务器内部、外部均可）
  >两次请求，不能在多个资源使用request共享数据

- 路径问题

是否要加虚拟目录

明确路径谁使用？
**浏览器使用：需要加虚拟目录（项目访问路径）**
**服务端使用：不需要加虚拟目录**

```java
//简化方式完成重定向
//动态获取虚拟目录
String contextPath = request.getContextPath();
response.sendRedirect(contextPath+"/resp2");
```

#### 3.Response响应字符数据

- 使用
  1.通过Response对象获取字符输出流

  ```java
  PrintWriter writer = resp.getWriter()
  ```

  2.写数据

  ```java
  writer.write("aaa");
  ```

  正常写入数据就调用write方法即可,如想要写入html文本语言,则要设置ContentType

```
response.setContentType("text/html;charset=utf-8");
//1.获取字符输出流
PrintWriter writer response.getWriter();
//content-type
//response.setHeader("content-type","text/html");
writer.write(s:"你好")；
writer.write(s:"<h1>aaa</h1>");
//细节：流不需要关闭
```

- 注意
  该流**不需要关闭**，随着响应结束，response对象销毁，由服务器关闭
  中文数据乱码：原因通过Response获取的字符输出流默认编码：ISO-8859-1

  ```java
  resp.setContentType("text/html;charset=utf-8");
  ```

#### 4.Response响应字节数据

- 使用
  1.通过Responsel对象获取字符输出流

  ```java
  ServletOutputStream outputStream = resp.getOutputStream();
  ```

  2.写数据

  ```java
  outputStream,write(字节数据)：
  ```

- IOUtils工具类使用
  1.导入坐标

  ```xml
  <dependency>
      <groupld>commons-io</groupld>
      <artifactld>commons-io</artifactld>
      <version>2.6</version>
  </dependency>
  ```

  2.使用

  ```java
  IOUtils.copy(输入流，输出流)；
  ```

#### 5.SqlSession工具类抽取

- 创建SqlSessionFactory代码优化
  ```java
  //2.1获取SqlSessionFactory对象
  String resource "mybatis-config.xml";
  Inputstream inputstream = Resources.getResourceAsstream(resource);
  SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputstream);
  ```

- 问题
  1.代码重复:工具类
  2.SqlSessionFactory工厂只创建一次,不要重复创建:静态代码块

## JSP

### 一.入门

#### 1.概念	

- Java Server Pages,Java服务端页面
- 一种动态的网页技术，其中既可以定义HTML、JS、CSS等静态内容，还可以定义Java代码的动态内容
- JSP = HTML+Java

![image-20221016082337865](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016082337865.png)

#### 2.快速入门

- 导入JSP坐标
  ```xml
  <dependency>
      <groupld>javax.servlet.jsp</groupld>
      <artifactld>jsp-api</artifactld>
      <version>2.2</version>
      <scope>provided</scope>
  </dependency>
  ```

- 创建JSP文件
  ![image-20221016084526668](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016084526668.png)

- 编写HTML标签和Java代码
  ```jsp
  <body>
  	<h1>hello jsp~<h1>
  	<%System.out.printf("jsp,hello~");%>
  <body>
  ```

#### 3.原理

- 概念：Java Server Pages,Java服务端页面
- JSP=HTML+Java,用于简化开发的
- JSP本质上就是一个Servlet

![image-20221016102956490](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016102956490.png)

### 二.脚本

#### 1.JSP脚本

- JSP脚本用于在JSP页面内定义Java代码
- JSP脚本分类：
  1. <%..%>:内容会直接放到」jspService()方法之中
  2. <%=...%>:内容会放到out.print()中，作为out.print()的参数
  3. <%!...%>:内容会放到jspService()方法之外，被类直接包含
     成员位置

#### 2.JSP缺点

- 由于JSP页面内，既可以定义HTML标签，又可以定义Java代码，造成了以下问题
  1. 书写麻烦：特别是复杂的页面
  2. 阅读麻烦
  3. 复杂度高：运行需要依赖于各种环境，JRE,JSP容器，JavaEE.
  4. 占内存和磁盘：JSP会自动生成.java和.class文件占磁盘，运行的是.class文件占内存
  5. 调试困难：出错后，需要找到自动生成的java文件进行调试
  6. 不利于团队协作：前端人员不会Java,后端人员不精HTML
  7. ...

![image-20221016110020331](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016110020331.png)
![image-20221016110312645](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016110312645.png)
![image-20221016110342901](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016110342901.png)

#### 3.EL表达式

- Expression Language表达式语言，用于简化JSP页面内的Java代码

- 主要功能:获取数据

- 语法:${expression}

  ```java
  ${brands}    :获取域中存储的key为brands的数据
  ```

- JavaWeb中的四大域对象

  1. page:当前页面有效
  2. request:当前请求有效
  3. session:当前会话有效
  4. application:当前应用有效

  **表达式获取数据，会依次从这4个域中寻找，直到找到为止**

![image-20221016132220144](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016132220144.png)

#### 4.JSTL标签

- JSP标准标签库(Jsp Standarded Tag Library),使用标签取代JSP页面上的Java代码
  ```jsp
  <c:if test="$(flag==1}">
  	男
  </c:if>
  <c:if test="$(flag==2)">
  	女
  </c:if>
  ```

##### 4.1快速入门

- 导入坐标
  ```xml
  <dependency>
      <groupld>jstl</groupld>
      <artifactld>jstl</artifactld>
      <version>1.2</version>
  </dependency>
  <dependency>
      <groupld>taglibs</groupld>
      <artifactld>standard</artifactld>
      <version>1.1.2</version>
  </dependency>
  ```

- 在JSP页面上引入JSTL标签库
  ```jsp
  <%@taglib prefix = "c" uri = "http://java.sun.com/jsp/jstl/core"%>
  ```

##### 4.2 c:if

```
<c:if>:相当于if判断
```

```jsp
<c:if>
    
    <c:if test="true">
        <h1>true</h1>
    </c:if>
    <c:if test="false">
        <h1>false</h1>
    </c:if>
    
```

##### 4.3 c:foreach

```
<c:foreach>:相当于for循环
```

- items:被遍历的容器
- var:遍历产生的临时变量
- varStatus:遍历状态对象

```jsp
<c:forEach items="${brands}"var="brand">
    <tr align="center">
        <td>${brand.id}</td>
        <td>${brand.brandName}</td>
        <td>${brand.companyName}</td>
        <td>${brand.description}</td>
    </tr>
</c:forEach>
```

```java
for (Brandbrand:brands){
    Integer id = brand.getld();
    String imgUrl = brand.getlmgUrl();
    String brandName = brand.getBrandName();
    String companyName = brand.getCompanyName();
}
```

- begin:开始数
- end:结束数
- step:步长

```jsp
<c:forEach begin="O"end="10"step="1"var="i">
	${i}
</c:forEach>
```

```java
for (int i=0;i<=10;i++){
	System.out.println(i)
} 
```

### 三.MVC模式及三层架构

#### 1.MVC模式

- MVC是一种分层开发的模式，其中：
  - M:Model,业务模型，处理业务
  - V:View,视图，界面展示
  - C:Controller,控制器，处理请求，调用模型和视图

![image-20221016154849908](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016154849908.png)

- MVC好处
  - 职责单一，互不影响
  - 有利于分工协作
  - 有利于组件重用

#### 2.三层架构

![image-20221016160023181](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016160023181.png)

- 数据访问层：对数据库的CRUD基本操作
- 业务逻辑层：对业务逻辑进行封装，组合数据访问层层中基本功能，形成复杂的业务逻辑功能
- 表现层：接收请求，封装数据，调用业务逻辑层，响应数据

#### 3.MVC模式和三层架构

![image-20221016160321419](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221016160321419.png)

## 会话跟踪技术

- 会话:用户打开浏览器，访问wb服务器的资源，会话建立，直到有一方断开连接，会话结束。在一次会话中可以包含**多次**请求和响应

![image-20221018184927775](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221018184927775.png)

- 会话跟踪：一种维护浏览器状态的方法，服务器需要识别多次请求是否来自于同一浏览器，以便在同一次会话的多次请求间**共享数据**

- HTTP协议是**无状态**的，每次浏览器向服务器请求时，服务器都会将该请求视为新的请求，因此我们需要会话跟踪技术来实现会话内数据共享

- 实现方式：
  1.客户端会话跟踪技术：**Cookie**
  2.服务端会话跟踪技术：**Session**

### 一.Cookie

#### 1.Cookie基本使用

- Cookie：客户端会话技术，将数据保存到客户端，以后每次请求都携带Cookie数据进行访问

- 基本使用

  **发送Cookie**

  1.创建Cookie对象,设置数据

  ```java
  Cookie dookie = new Cookie("key","value");
  ```

  2.发送Cookie到客户端

  ```java
  response.addCookie(cookie);
  ```

  **获取Cookie**

  3.获取客户端携带的所有Cookie,使用request对象

  ```java
  Cookie[]cookies = request.getCookies();
  ```

  4.遍历数组，获取每一个Cookie对象：for

  5.使用Cookie对象方法获取数据

  ```java
  cookie.getName();
  ```

  ```java
  cookie.getValue();
  ```

#### 2.Cookie原理

- Cookie的实现是基于HTTP协议的
  - 响应头：set-cookie
  - 请求头：cookie

![image-20221018190944866](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221018190944866.png)

#### 3.Cookie使用细节

- Cookie存活时间
  - 默认情况下，Cookie存储在浏览器内存中，当浏览器关闭，内存释放，则Cookie被销毁
  - setMaxAge(int seconds).:设置Cookie存话时间
    1.正数：将Cookie写入浏览器所在电脑的硬盘，持久化存储。到时间自动删除
    2.负数：默认值，Cookie在当前浏览器内存中，当浏览器关闭，则Cookie被销毁
    3.零：删除对应Cookie
- Cookie存储中文
  - Cookie不能直接存储中文
  - 如需要存储，则需要进行转码：URL编码

### 二.Session

#### 1.Session基本使用

- 服务端会话跟踪技术：将数据保存到服务端

- JavaEE提供HttpSession接口，来实现一次会话的多次请求间数据共享功能

- 使用:
  1.获取Session对象

  ```java
  HttpSession session = request.getSession();
  ```

  2.Session对象功能:

  - void setAttribute(String name,Object o):存储数据到session域中
  - Object getAttribute(String name:根据key,获取值
  - void removeAttribute(String name):根据key,删除该键值对

#### 2.Session原理 

- Session是基于Cookie实现的

![image-20221018200541455](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221018200541455.png)

#### 3.Session使用细节

- Session钝化、活化:

  - 服务器重启后，Session中的数据是否还在？
  - 钝化：在服务器正常关闭后，Tomcat:会自动将Session数据写入硬盘的文件中
  - 活化：再次启动服务器后，从文件中加载数据到Session中

- Session销毁:

  - 默认情况下，无操作，30分钟自动销毁
    ```xml
    <session-config>
    	<session-timeout>30</session-timeout>
    </session-config>
    ```

  - 调用Session对象的invalidate()方法

### 三.小结

- Cookie和Session都是来完成一次会话内多次请求间数据共享的
- 区别
  - 存储位置：Cookie是将数据存储在客户端，Session将数据存储在服务端
  - 安全性：Cookie不安全，Session安全
  - 数据大小：Cookie最大3KB,Session无大小限制
  - 存储时间：Cookie可以长期存储，Session默认30分钟
  - 服务器性能：Cookie不占服务器资源，Session占用服务器资源

## Filter和Listener

### 一.Filter

- 概念：Filter表示过滤器，是JavaWeb三大组件(Servlet、Filter、Listener)之一。
- 过滤器可以把对资源的请求**拦截**下来，从而实现一些特殊的功能。
- 过滤器一般完成一些**通用**的操作，比如：权限控制、统一编码处理、敏感字符处理等等

![image-20221020204824927](C:\Users\24946\AppData\Roaming\Typora\typora-user-images\image-20221020204824927.png)

#### 1.快速入门

- 定义类，实现Filter接口，并重写其所有方法
  ```java
  public class FilterDemo implements Filter{
      public void init(FilterConfig filterConfig)
      public void doFilter(ServletRequest request
      public void destroy(){}
  }
  ```

- 配置Filter拦截资源的路径：在类上定义@WebFilter注解
  ```java
  @WebFilter("/*")
  public class FilterDemo implements Filter{}
  ```

- 在doFilter方法中输出一句话，并放行

  ```java
  public void doFilter(ServletRequest request,Ser
      System.out.println("filter被执行了...")；
      //放行
      chain.doFilter(request,response);
  }
  ```

#### 2.Filter执行流程

![image-20221020205708487](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221020205708487.png)

1.放行后访问对应资源，资源访问完成后，还会回到Fter中吗？  会

2.如果回到Filter中，是重头执行还是执行放行后的逻辑呢？		放行后逻辑

![image-20221020211035097](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221020211035097.png)

#### 3.使用细节

##### 3.1Filter拦截路径配置

- Filter可以根据需求，配置不同的拦截资源路径
  ```java
  @WebFilter("/*")
  public class FilterDemo
  ```

  - 拦截具体的资源：/index,jsp:只有访问lindex,jsp时才会被拦截。
  - 目录拦截：/user/*:访问/user下的所有资源，都会被拦截
    后缀名拦截：*
  - jsp:访问后缀名为jsp的资源，都会被拦截
  - 拦截所有：*：访问所有资源，都会被拦截

##### 3.2过滤器链

- 一个Web应用，可以配置多个过滤器，这多个过滤器称为过滤器链

![image-20221021175505738](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221021175505738.png)

- 注解配置的Filter,优先级按照过滤器类名（字符串）的自然排序

### 二.监听器

- 概念：Listener表示监听器，是JavaWeb三大组件(Servlet、Filter、Listener)之一。
- 监听器可以监听就是在application,session,request:三个对象创建、销毁或者往其中添加修改删除
  属性时**自动**执行代码的功能组件
- Listener分类：JavaWeb中提供了8个监听器

| 监听器分类         | 监听器名称                      | 作用                                            |
| ------------------ | ------------------------------- | ----------------------------------------------- |
| ServletContext监听 | ServletContextListener          | 用于对ServletContextx对象进行监听（创建、销毁） |
|                    | ServletContextAttributeListener | 对ServletContext对象中属性的监听（增删改属性）  |
| Session监听        | HttpSessionListener             | 对Session对象的整体状态的监听（创建、销毁）     |
|                    | HttpSessionAttributeListener    | 对Session对象中的属性监听（增删改属性）         |
|                    | HttpSessionBindingListener      | 监听对象于Sessionl的绑定和解除                  |
|                    | HttpSessionActivationListener   | 对Session数据的钝化和活化的监听                 |
| Request监听        | ServletRequestListener          | 对Request对象进行监听（创建、销毁）             |
|                    | ServletRequestAttributeListener | 对Request对象中属性的监听（增删改属性）         |

## Ajax&Axios&JSON

- 概念:AJAX(**A**synchronous **J**avaScript **A**nd **X**ML):**异步**的JavaScript和XML

- AJAX作用:
  1.与服务器进行数据交换：通过AJAX可以给服务器发送请求，并获取服务器响应的数据

  - 使用了AJAX和服务器进行通信，就可以使用HTML+AJAX来**替换JSP**页面了
    ![image-20221022084321376](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221022084321376.png)

  2.异步交互：可以在**不重新加载整个页面**的情况下，与服务器交换数据并**更新部分**网页的技术，如：搜索联想、用户名是否可用校验，等等.

### 一.AJAX

#### 1.同步异步

##### 1.1同步

![image-20221022084940902](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221022084940902.png)

##### 1.2异步

![image-20221022085234917](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221022085234917.png)

#### 2.快速入门

- 编写AjaxServlet,并使用response输出字符串

- 创建XMLHttpRequest对象：用于和服务器交换数据
  ```js
  var xmlhttp;
  if (window.XMLHttpRequest){
  	//code for IE7+,Firefox,Chrome,Opera,Safari
  	xmlhttp = new XMLHttpRequest();
  )else{
  	∥code for IE6,IE5
  	xmlhttp new = ActiveXObject("Microsoft.XMLHTTP");
  }
  
  ```

- 向服务器发送请求
  ```js
  xmlhttp.open("GET","url");
  xmlhttp.send(O;∥发送请求
  ```

- 获取服务器响应数据
  ```js
  xmlhttp.onreadystatechange function (){
  	if(xmlhttp.readyState ==4 && xmlhttp.status ==200){
  	alert(xmlhttp.responseText);
  }
  
  ```

### 二.AXIOS

#### 1.Axios异步框架

- Axios对原生的AJAX进行封装，简化书写
- 官网：https://www.axios-http.cn

#### 2.快速入门

##### 2.1引入axios的js文件

```js
<script src="js/axios-0.18.0.js"></script>
```

##### 2.2使用axios发送请求，并获取响应结果

```js
axios({
    method:"get",
    url:"http://localhost:8080/ajax-demo1/aJAXDemo1?username=zhangsan"
}).then(function (resp){
	alert(resp.data);
})
```

```js
axios((
    method:"post",
    url:"http://localhost:8080/ajax-demo1/aJAXDemo1",
    data:"username=zhangsan"
}).then(function (resp){
	alert(resp.data);
}:
```

#### 3.Axios请求方式别名

- 为了方便起见，Axos已经为所有支持的请求方法提供了别名，

  axios.get(url[,config])
  axios.delete(url[,config])
  axios.head(url[,config])
  axios.options(url[,config])
  axios.post(url[,data[,config]])
  axios.put(url[,data[,config]])
  axios.patch(url[,data[,config]])



| 方法名             | 作用             |
| ------------------ | ---------------- |
| get(url)           | 发起GET方式请求  |
| post(url,请求参数) | 发起POST方式请求 |

- 发送get请求
  ```js
  axios.get("url")
      .then(function (resp){
  		alert(resp.data);
  });
  ```

- 发送psot请求
  ```js
  axios.post("ur","参数")
  	.then(function(resp){
  	alert(resp.data);
  }
  ```

### 三.JSON

- 概念：**J**avaScript **O**bject **N**otation。JavaScript对象表示法

![image-20221022105317460](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221022105317460.png)

#### 1.JSON基础语法

- 定义:

  ```json
  var变量名={
  	"key1":value1,
  	"key2":value2,
  	...
  	};
  ```

  value的数据类型为:

  数字（整数或浮点数）
  字符串（在双引号中）
  逻辑值(true或false)
  数组（在方括号中）
  对象（在花括号中）
  null

  - 实例:

    ```json
    var json {
    	"name":"zhangsan",
    	"age":23,
    	"addr":["北京"，"上海"，"西安]
    	};
    ```

- 获取数据:
  ```json
  变量名.key
  ```

  ```json
  json.name
  ```

#### 2.JSON数据和Java对象转换

![image-20221022110050344](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221022110050344.png)

- 请求数据：JSON字符串转为Java对象
- 响应数据：Java对象转为JSON字符串



- Fastjson是阿里巴巴提供的一个Java语言编写的高性能功能完善的JSON库，是目前Java语言中最快的JSON库，可以实现Java对象和SON字符串的相互转换。

- 使用
  1.导入坐标

  ```xml
  <dependency>
  	<groupld>com.alibaba</groupld>
  	<artifactld>fastjson</artifactld>
  	<version>1.2.62</version>
  </dependency>
  ```

  2.Java对象转JSON

  ```java
  String jsonStr = JSON.toJSONString(obj);
  ```

  3.JSON字符转转Java对象

  ```java
  User user = JSON.parseobject(jsonStr,User.class);
  ```

## Vue&Element

### 一.Vue

#### 1.概述

- **Vue**是一套**前端框架**，免除原生lavaScriptr中的DOM操作，简化书写
- 基于**MVWM**(Model--View-ViewModel))思想，实现数据的**双向绑定**，将编程的关注点放在数据上
- 官网：https://cn.vuejs..org
  ![image-20221025155949797](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221025155949797.png)
  ![image-20221025160102518](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221025160102518.png)

##### 1.1快速入门

- 新建HTML页面，引入Vue.js文件
  ```js
  <script src="js/vue.js"></script>
  ```

- 在JS代码区域，创建Vue核心对象，进行数据绑定
  ```js
  new Vue({
      el:"#app",
      data(){
      	return{
      		username:""
      	}
      }
  });
  ```

- 编写视图
  ```html
  <div id="app">
      <input name="username"v-model="username">
      {{username)}
  </div>
  ```

#### 2.常用指令

- 指令:HTML标签上带有V-前缀的特殊属性，不同指令具有不同含义。例如：V-if,V-for.

- 常用指令

  | 指令      | 作用                                                |
  | --------- | --------------------------------------------------- |
  | v-bind    | 为HTML标签绑定属性值，如设置href,css样式等          |
  | v-model   | 在表单元素上创建双向数据绑定                        |
  | v-on      | 为HTML标签绑定事件                                  |
  | v-if      | 条件性的渲染某元素，判定为true时渲染，否则不渲染    |
  | v-else    | 条件性的渲染某元素，判定为true时渲染，否则不渲染    |
  | v-else-if | 条件性的渲染某元素，判定为true时渲染，否则不渲染    |
  | v-show    | 根据条件展示某元素，区别在于切换的是display属性的值 |
  | v-for     | 列表渲染，遍历容器的元素或者对象的属性              |



##### 2.1指令

- v-bind:
  ```vue
  <a v-bind:href="url">百度一下</a>
  ```

  ```vue
  <!--
  v-bind可以省略
  -->
  <a:href="url">百度一下</a>
  ```

- v-model:
  ```vue
  <input name="username"v-model="username">
  ```

- v-on:

  - html
    ```html
    <input type-="button" value="一个按钮"v-on:click="show()">
    ```

    ```html
    <input type="button"value="一个按钮"@click="shoW">
    ```

  - vue
    ```vue
    new Vue({
        el:"#app",
        methods:{
        	show(){
            	alert("我被点了");
            }
        }
    });
    ```

- v-if
  ```vue
  <div v-if="count == 3">div1</div>
  <div v-else-if="count == 2">div2</div>
  <div v-else>div3</div>
  ```

- v-show
  ```vue
  <div v-show="count == 3">div4</div>
  ```

- v-for
  ```vue
  <div v-for="addr in addrs">
  	{{addr}}<br>
  </div>
  ```

- 加索引
  ```vue
  <div v-for="(addr,i)in addrs">
      <!-i表示索引，从0开始->
      {{i+1}}:{{addr}}<br>
  </div>
  ```

#### 3.生命周期

- 生命周期的八个阶段：每触发一个生命周期事件，会自动执行一个生命周期方法（钩子）
  

| 状态          | 阶段周期     |
| ------------- | ------------ |
| beforeCreate  | 创建前       |
| created       | 创建后       |
| beforeMount   | 载入前       |
| **mounted**   | **挂载完成** |
| beforeUpdate  | 更新前       |
| updated       | 更新后       |
| beforeDestroy | 销毁前       |
| destroyed     | 销毁后       |

- mounted:挂载完成，Vue初始化成功，HTML页面渲染成功。

  - 发送异步请求,加载数据

- 示例
  ```vue
  new Vue({
      el:"#app",
      mounted(){
      	alet("vue挂载完毕，发送异步请求")；
      }
  });
  ```


### 二.Element

#### 1.概述

- Element:是饿了么公司前端开发团队提供的一套基于Vue的网站组件库，用于快速构建网页
- 组件：组成网页的部件，例如超链接、按钮、图片、表格等等~
- 自己完成的按钮
  ![image-20221026084943140](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221026084943140.png)
- Element提供的按钮
  ![image-20221026085049447](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221026085049447.png)
- Element官网：https://element.eleme.cn/#/zh-CNListener

##### 1.1快速入门

- 引入Element的css、js文件和Vue.js
  ```js
  <script src="vue.js"></script>
  <script src="element-ui/lib/index.js"></script>
  <link rel="stylesheet"href="element-ui/lib/theme-chalk/index.css">
  ```

- 创建Vue核心对象
  ```vue
  <script>
      new Vue({
      	el:"#app"
      })
  </script>
  ```

- 官网复制Element组件代码

#### 2.Element布局

- Element中有两种布局方式:

  - Layout布局:通过基础的24分栏，迅速简便地创建布局

  ![image-20221026090505447](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221026090505447.png)

  - Container布局容器：用于布局的容器组件，方便快速搭建页面的基本结构

    ![image-20221026090637459](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221026090637459.png)

#### 3.Element组件

![image-20221026091658345](https://xingqiu-tuchuang-1256524210.cos.ap-shanghai.myqcloud.com/00325/image-20221026091658345.png)

都多余了,上官网上找代码就行
