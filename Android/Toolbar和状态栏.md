# Toolbar和状态栏

​	themes

```java
//设置为NoActionbar
<style name="Theme.WanAndroid" parent="Theme.MaterialComponents.DayNight.DarkActionBar">
//设置状态栏虚化
 <item name="android:windowTranslucentStatus">true</item>
```

layout

```java
    <androidx.appcompat.widget.Toolbar
        android:id="@+id/register_toolbar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/white"
        android:fitsSystemWindows="true"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
        app:popupTheme="@style/ThemeOverlay.AppCompat.Light"
        app:titleTextColor="@color/white">

    </androidx.appcompat.widget.Toolbar>
```

Activity

```java
Toolbar toolbar=(Toolbar) findViewById(R.id.register_toolbar);
        setSupportActionBar(toolbar);
        ActionBar actionBar=getSupportActionBar();
        if (actionBar!=null){
            actionBar.setDisplayHomeAsUpEnabled(true);
            actionBar.setHomeAsUpIndicator(R.drawable.return1);
        }
//--------------------------------------------------------------------------------
public boolean onCreateOptionsMenu(Menu menu){
        getMenuInflater().inflate(R.menu.toolbar_register,menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        if (item.getItemId() == android.R.id.home) {
            finish();
            overridePendingTransition(android.R.anim.fade_in, android.R.anim.fade_out);
        }
        return true;
    }
```

