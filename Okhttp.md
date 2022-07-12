# Okhttp

post

```java
//一个常用bean
public static  void  registerWithOkHttp(String username,String password,String repassword,okhttp3.Callback callback){
        OkHttpClient client  = new OkHttpClient();
        RequestBody body  =  new FormBody.Builder()
                .add("username",username)
                .add("password",password)
                .add("repassword",repassword)
                .build();
        Request request  =  new Request.Builder()
                .url("https://www.wanandroid.com/user/register")
                .post(body)
                .build();
        client.newCall(request).enqueue(callback);
    }
```

