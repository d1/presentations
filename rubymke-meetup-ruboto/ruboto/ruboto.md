!SLIDE center subsection
#Anatomy of a Ruboto project
![](ruboto_anatomy.png)

!SLIDE bullets
#src/org/ruboto/
* RubotoActivity.java
* RubotoBroadcastReceiver.java
* RubotoService.java

!SLIDE bullets transition=scrollUp
#src/org/ruboto/
* Look, don't touch
* Make subclasses in com.yourapp

!SLIDE bullets
#src/com/yourapp/
#YourActivity.java
    @@@java
    onCreate(Bundle priorState)
    onRestart()
    onStart()
    onResume()
    onPause()
    onStop()
    onDestroy()

!SLIDE bullets transition=scrollUp
    @@@java
    package com.myapp;
    import android.os.Bundle;

    public class MyActivity extends org.ruboto.RubotoActivity {
      public void onCreate(android.os.Bundle arg0) {
        try {
          setSplash(
            Class.forName("com.my.ruboto.R$layout")
              .getField("splash")
              .getInt(null)
          );
        } catch (Exception e) {}
        setScriptName("my_activity.rb");
        super.onCreate(arg0);
      }
    }


!SLIDE bullets
#assets/scripts/my_activity.rb
* def on_create
* activity.content_view = some_widget
* def on_pause

!SLIDE bullets
#assets/scripts/ruboto.rb
* Require from your script
* Witchcraft!

!SLIDE
#AndroidManifest.xml
!SLIDE bullets transition=scrollUp
    <application>
        @name, @icon, @label
    <activity>
        <intent-filter>
            <action>
            <category>
    <service>
    <receiver>
!SLIDE transition=scrollUp
    <uses-permission>
        CALL_PHONE
        SEND_SMS
        RECORD_AUDIO
        WRITE_EXTERNAL_STORAGE
        INSTALL_SHORTCUT
        INTERNET
        ACCESS_COARSE_LOCATION
        ACCESS_FINE_LOCATION
        ...


!SLIDE bullets
#res/drawable/myimage.png

!SLIDE transition=scrollUp
## Reference with:
    @@@ruby
    java_import "com.my.ruboto.R"

    R::drawable::myimage

!SLIDE bullets
#res/values/strings.xml
    <string name="my_string_name">
      Any Value
    </string>

!SLIDE transition=scrollUp
# Reference with:
    @@@ruby
    java_import "com.my.ruboto.R"
    
    get_string(R::string::my_string_name)
    