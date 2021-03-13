---

  layout: post
  title: "Seesion 和 Cookie"
  excerpt_separator: "<!--more-->"
  categories:

- Post Formats

 tags:

- Post Formats

- readability

- standard

  last_modified_at: 2017-03-09T10:55:59-05:00

---

## Session 和 Cookie

引用自：[https://blog.csdn.net/java_faep/article/details/78082802](https://blog.csdn.net/java_faep/article/details/78082802)

### **服务器端Session**

```
浏览器 第一次 访问服务器会在服务器端生成一个session，有一个sessionid和它对应。tomcat生成的sessionid叫做jsessionid。session在访问tomcat服务器HttpServletRequest的getSession(true)的时候创建，tomcat的ManagerBase类提供创建sessionid的方法：随机数+时间+jvmid；它存储在服务器的内存中，tomcat的StandardManager类将session存储在内存中，也可以持久化到file， 数据库 ，memcache， Redis 等
```

<!--more-->

### **客户端Session**:

```
当用户首次与Web服务器建立连接时，服务器会给用户分发一个SessionID. 客户端只保存SessionID到cookie中，而不保存Session。
```

PS :  SessionID是一个随机字符串。用户每次提交页面，浏览器都会把这个SessionID包含在 HTTP头中提交给Web服务器，这样Web服务器就能区分当前请求页面的是哪一个客户端

### **session会因为浏览器的关闭而删除吗？**

```
看Cookie类型
若使用的是进程中的cookie(大部分使用的是这种，又叫回话Cookie),保存在内存中，关闭浏览器后，进程消失，则cookie消失，SessionID消失，再次请求服务器就无法找到原来的Session了。其实该Session对象仍然保存在服务端，超过Session的最大有效时间后Session被删除
若使用的是硬盘中的cookie（又叫持久Cookie）,这时SessionID将长期保存在硬盘的Cookie中，直到失效为止(会设置过期时间，应用场景：CSDN的“记住我一周”）
```



