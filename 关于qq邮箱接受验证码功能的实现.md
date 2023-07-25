---
title: 关于qq邮箱接受验证码功能的实现
date: 2022-11-08 11:07:59
tags: java
categories: qq邮箱接收验证码
# qq邮箱接收验证码
## 第一步:pom.[xml](https://so.csdn.net/so/search?q=xml&spm=1001.2101.3001.7020)导入配置
```java
    <!--QQ邮箱验证码所需jar包-->
    <dependency>
      <groupId>javax.activation</groupId>
      <artifactId>activation</artifactId>
      <version>1.1.1</version>
    </dependency>
 
    <dependency>
      <groupId>javax.mail</groupId>
      <artifactId>mail</artifactId>
      <version>1.4.7</version>
    </dependency>
 
    <dependency>
      <groupId>org.apache.commons</groupId>
      <artifactId>commons-email</artifactId>
      <version>1.4</version>
    </dependency>
```
## 第二步:写一个工具类
```java
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.springframework.stereotype.Component;
 
@Component
public class SendMail {
 
    /**
     * 发送邮件代码
     * @param targetEmail 目标邮箱
     * @param authCode 验证码
     */
    public  void sendEmailCode(String targetEmail, String authCode) {
        try {
            SimpleEmail mail = new SimpleEmail();
            // 发送邮件的服务器
            mail.setHostName("smtp.qq.com");
            // 刚刚记录的授权码，是开启SMTP的密码
            mail.setAuthentication("邮箱号", "授权码");
            // 发送邮件的邮箱和发件人
            mail.setFrom("邮箱号", "用户名");
            // 使用安全链接
            mail.setSSLOnConnect(true);
            // 接收的邮箱
            mail.addTo(targetEmail);
            // 邮件的主题
            mail.setSubject("注册验证码");
            // 邮件的内容
            mail.setMsg("验证码为:" + authCode);
            // 发送
            mail.send();
        } catch (EmailException e) {
            e.printStackTrace();
        }
    }
}
```
## 第三步再controller层调用
```java
@ApiOperation(value ="发送验证码",notes = "邮箱账号不要写错",httpMethod = "POST")
    @PostMapping("/getCode")
    @ResponseBody
    public Response mail(@RequestParam("targetEmail") String targetEmail) {
        //生成六位数验证码
        authCode = String.valueOf(new Random().nextInt(899999) + 100000);
        //sendMail.sendMail(email, "你的验证码为" + captcha + "(五分钟内有效)");
        sendMail.sendEmailCode(targetEmail, "你的验证码为" + authCode + "(五分钟内有效)");
        return Response.ok(0,"验证码发生成功");
    }
```
## 总结:
如此就可以实现qq邮箱接收验证码,可以用于账号找回的验证以及邮箱注册等功能
