# NavigationR8MinRepro
This is a minimum application example of R8 removing composables that are only referenced by navigation routes in Jetpack Fragment Navigation. 

The FirstScreen Composable function is referenced as the first destination in the main nav graph using the composable tag

```
<composable
        android:id="@+id/first_screen"
        android:name="com.example.navigationr8minrepro.FirstScreenKt$FirstScreen"
        android:label="fragment_schedule"/>
```

Minification is enabbled on the debug build for simplicity of replecation of the issues. 

When trying to run the application a run time error occurs because the file FirstScreen.kt cannot be found, this does not occur if minification is disabled, or an @Keep annotation is added to the FirstScreen composable function. 

```
FATAL EXCEPTION: main
Process: com.example.navigationr8minrepro, PID: 9951
java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
  at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:558)
  at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:936)
Caused by: java.lang.reflect.InvocationTargetException
  at java.lang.reflect.Method.invoke(Native Method)
  at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:548)
  at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:936) 
Caused by: java.lang.ClassNotFoundException: com.example.navigationr8minrepro.FirstScreenKt
```
