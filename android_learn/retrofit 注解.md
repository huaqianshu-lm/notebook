@GET：

```java
/** Make a GET request. */
@Documented
@Target(METHOD)
@Retention(RUNTIME)
public @interface GET {
  String value() default "";
}
```

作用：创建一个 get 请求。作用于方法。

参数：一个相对或绝对的路径（path），或是一个完整的 url 路径（[endpoint：终点](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)）。如果方法的第一个参数被 @Url 注解，那么这个值（value）是可选的。

***例子***

```java
@GET
Call<ResponseBody> list(@Url String url);
```

@Url:

```java
@Documented
@Target(PARAMETER)
@Retention(RUNTIME)
public @interface Url {
}
```

作用：作用于参数，指定一个 url。

@Path:

```java
@Documented
@Retention(RUNTIME)
@Target(PARAMETER)
public @interface Path {
  String value();

  /**
   * Specifies whether the argument value to the annotated method parameter is already URL encoded.
   */
  boolean encoded() default false;
}
```

作用：作用于参数。根据名字替换 url 中的一个片断。值会被转换成 String 类型，参数默认 URL 编码。

参数：不可为 null

1. String value：要替换的值
2. boolean encode：是否是 url 编码。默认是，设置 true 时，取消 url 编码。

***例子：***

```java
@GET("/image/{id}")
Call<ResponseBody> example(@Path("id") int id);

//执行 foo.example(1) GET 中的 id 就会被替换成『1』。
```

```java
// 使用 url 编码
@GET("/user/{name}")
Call<ResponseBody> encoded(@Path("name") String name);
// 执行 foo.encoded("John+Doe) 结果是("/user/John%2BDoe")

// 不使用 url 编码
@GET("/user/{name}")
Call<ResponseBody> notEncoded(@Path(value="name", encoded=true) String name);
// 执行 foo.encoded("John+Doe) 结果是("/user/John%2BDoe")
```

@Query：

```java
@Documented
@Target(PARAMETER)
@Retention(RUNTIME)
public @interface Query {
  /** The query parameter name. */
  String value();

  /**
   * Specifies whether the parameter {@linkplain #value() name} and value are already URL encoded.
   */
  boolean encoded() default false;
}
```

作用:作用于参数。查询参数拼接到 url 中。

参数：

1. String value：查询的参数的名字。该值会被转换成 String 类型，默认 url 编码。null 值会被忽略。如果是一个 list 或是 array，则每一个不为 null 的值都会被作为查询的参数。
2. boolean encode() default false：是否为 url 编码。默认为 url 编码，设置为 true 时，取消 url 编码。

***例子：***



```java
@GET("/list")
Call<ResponseBody> list(@Query("page") int page);

// 执行 foo.list(1)，结果为 (/list?page=1)
```

```java
// 值为 null 时
@GET("/list")
Call<ResponseBody> list(@Query("category") String category);

// 执行 foo.list(1)，结果为 (/list)
```

```java
// 数组(可变参数)时
@GET("/list")
Call<ResponseBody> list(@Query("category") String... categories);
// 执行foo.list("bar", "baz")，结果为 (/list?category=bar&category=ba)
```

``` java
// 不使用 url 编码
@GET("/search")
Call<ResponseBody> list(@Query(value="foo", encoded=true) String foo);
// 执行 foo.list("foo+bar")，结果为(/search?foo=foo+bar)
```

@Multipart：

```java
@Documented
@Target(METHOD)
@Retention(RUNTIME)
public @interface Multipart {
}
```

作用：作用于方法，使用该注解，表示请求体是多部分的，每个部分作为一个参数，且用Part注解声明。



@Part：

```java
@Documented
@Target(PARAMETER)
@Retention(RUNTIME)
public @interface Part {
  /**
   * The name of the part. Required for all parameter types except
   * {@link okhttp3.MultipartBody.Part}.
   */
  String value() default "";
  /** The {@code Content-Transfer-Encoding} of this part. */
  String encoding() default "binary";
}
```

作用：作用于参数。表示是 Multipart 的一个部分。使用该注解时有三种方法：

- 如果类型是 ***okhttp2.MulitpartBody.Part*** ，内容将被直接使用，省略 part 中的名称，即***@Part MultipartBody.Part part***
- 如果类型是RequestBody，那么该值直接与其内容类型一起使用。在注解中提供part名称，例如，***@Part("foo") RequestBody foo***
- 其它对象类型将通过使用转换器转换为适当的格式。在注解中提供part名称，例如，***@Part("foo") Image photo***

part 注解的参数可以为 null，为 null 时被忽略。

参数：

1. String value：除了***okhttp3.MultipartBody.Part*** 类型可以省略，其他的都不能省略。
2. String encoding：这个 part 的内容传输编码，默认为二进制。

part 的参数不能为 null。

例子：

```java
@Multipart
@POST("/")
Call<ResponseBody> example(
    @Part("description") String description,
    @Part(value = "image", encoding = "8-bit") RequestBody image);
```

#### baseUrl() of retrofit2.Retrofit.Builder

Set the API base URL. The specified endpoint values (such as with GET) are resolved against this value using HttpUrl#resolve(String). The behavior of this matches that of an link on a website resolving on the current URL. Base URLs should always end in /. A trailing / ensures that endpoints values which are relative paths will correctly append themselves to a base which has path components.

Correct: 

Base URL: http://example.com/api/ 

Endpoint: foo/bar/ 

Result: http://example.com/api/foo/bar/

 Incorrect:

 Base URL: http://example.com/api 

Endpoint: foo/bar/ 

Result: http://example.com/foo/bar/ 

This method enforces that baseUrl has a trailing /. Endpoint values which contain a leading / are absolute. Absolute values retain only the host from baseUrl and ignore any specified path components. 

Base URL: http://example.com/api/ 

Endpoint: /foo/bar/ 

Result: http://example.com/foo/bar/ 

Base URL: http://example.com/ 

Endpoint: /foo/bar/ 

Result: http://example.com/foo/bar/ 

Endpoint values may be a full URL. Values which have a host replace the host of baseUrl and values also with a scheme replace the scheme of baseUrl. 

Base URL: http://example.com/ 

Endpoint: https://github.com/square/retrofit/ 

Result: https://github.com/square/retrofit/ 

Base URL: http://example.com 

Endpoint: //github.com/square/retrofit/

Result: http://github.com/square/retrofit/ (note the scheme stays 'http')