---

  layout: post
  title: "http1.0和http1.1对比"
  excerpt_separator: "<!--more-->"
  categories:

- Post Formats

 tags:

- Post Formats

- readability

- standard

  last_modified_at: 2017-03-09T10:55:59-05:00

---

## http1.0和http1.1对比

### http1.0

**只支持短暂连接**： 交互完数据后，立即断开TCP连接

### http1.1

**持续连接**：一次TCP连接，可以发送多个请求

**流水线方式请求**：在收到响应前就可以发送新请求



**举个例子**:  

第一次访问www.tracup.com

![image-20210222141958378](/img/image-20210222141958378.png)

第二次访问www.tracup.com

![image-20210222142059276](/img/image-20210222142059276.png)





说明：第一次包含了初始化连接时间和SSL时间，第二次没有，如果是http1.0协议，则每次请求都会有这2个开销

![image-20210222142210696](/img/image-20210222142210696.png)

