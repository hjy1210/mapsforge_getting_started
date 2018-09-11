## Problem
I use GettingStarted.java as template to diaplay germany.map in 
android device, but failed, the screen is almost blank(see below). Hope some one can help me.

My senario is as follows:

1. clone mapsforge project, build it, run sample application in my android device, every thing is OK. When I tap on gettingStarted button, germany.map show up on screen as expected. So my germany.map is located at correct location.

2. Using android studio, 
    1. create new android application with empty activity
    2. replace content of MainActivity.java with that of GettingStarted.java appeared in mapsforge-samples-android.
    3. run application in my android device. 
        1) The screen is almost blank, lower left corner show up scale of 10000 km
        2) tap on lower right corner, zoon in/out buttons appeared.
3. I post the porject on https://github.com/hjy1210/mapsforge_getting_started, hope some one can tell me how to fix it.

PS: If I set debug breakpoint at line 84 of MainActivity.ja,
```
84 File mapFile = new File(Environment.getExternalStorageDirectory(), MAP_FILE);
85 Log.i("mapfile","size="+mapFile.length()); 
86 MapDataStore mapDataStore = new MapFile(mapFile);
```

1. When step over line 84, in debug window, we can see variable mapFile=(File@4896)"/storage/emulated/0/germany.map"
2. After step over line 85,  log message show : "I/mapfile: size=49023281", which is the correct size of germany.map.(germany.map is acturally berlin.map renamed)
3. When step over line 86, error thrown as:
```
W/System.err: org.mapsforge.map.reader.header.MapFileException: cannot read file: /storage/emulated/0/germany.map
W/System.err:     at org.mapsforge.map.reader.MapFile.<init>(MapFile.java:247)
W/System.err:     at org.mapsforge.map.reader.MapFile.<init>(MapFile.java:207)
W/System.err:     at com.example.mapsforge_getting_started.MainActivity.onCreate(MainActivity.java:86)
W/System.err:     at android.app.Activity.performCreate(Activity.java:7016)
W/System.err:     at android.app.Instrumentation.callActivityOnCreate(Instrumentation.java:1214)
W/System.err:     at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2780)
W/System.err:     at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:2902)
W/System.err:     at android.app.ActivityThread.-wrap11(Unknown Source:0)
W/System.err:     at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1603)
W/System.err:     at android.os.Handler.dispatchMessage(Handler.java:105)
W/System.err:     at android.os.Looper.loop(Looper.java:169)
W/System.err:     at android.app.ActivityThread.main(ActivityThread.java:6578)
W/System.err:     at java.lang.reflect.Method.invoke(Native Method)
W/System.err:     at com.android.internal.os.Zygote$MethodAndArgsCaller.run(Zygote.java:240)
W/System.err:     at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:767)
```
Hope some one can help me.

## Solution
On android device, at information page of app, enable storage permission.