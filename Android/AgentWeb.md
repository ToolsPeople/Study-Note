# AgentWeb

​	AgentWeb 是一个高度封装的 Android WebView ，简单易用 ， 带有进度条 、 支持文件上传 、 下载 、 简化 Javascript 通信 ，加强 Web 安全的库 。

​	不建议看github开源库，因为简介里作者根本就没有教你怎么用。

依赖：

```java
implementation 'com.just.agentweb:agentweb-androidx:4.1.4'
```

Layout:

```Java
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity"
    android:id="@+id/agentweb">

</LinearLayout>
```

Activity:

```java
public class MainActivity extends AppCompatActivity {

    private AgentWeb agentWeb;

    private LinearLayout linWeb;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        linWeb= (LinearLayout) findViewById(R.id.agentweb);
        agentWeb=AgentWeb.with(this)
                .setAgentWebParent(linWeb, new LinearLayout.LayoutParams(-1, -1))
                .useDefaultIndicator()//进度条
                .createAgentWeb()
                .ready()
                .go("https://blog.csdn.net/iamchan/article/details/78743074");
    }


    @Override

    public boolean onKeyDown(int keyCode, KeyEvent event) {

        if (agentWeb.handleKeyEvent(keyCode, event)) {

            return true;

        }

        return super.onKeyDown(keyCode, event);

    }

    @Override

    protected void onPause() {

        agentWeb.getWebLifeCycle().onPause();

        super.onPause();

    }

    @Override

    protected void onResume() {

        agentWeb.getWebLifeCycle().onResume();

        super.onResume();

    }

    @Override

    protected void onDestroy() {

        agentWeb.getWebLifeCycle().onDestroy();

        super.onDestroy();

    }
}
```

