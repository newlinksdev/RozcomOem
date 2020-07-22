# RozcomOem


Android alpha:

Top level gradle:

```gradle
allprojects {
    repositories {
        google()
        jcenter()
        mavenCentral()
         maven {
                name = "GitHubPackages"
                url = uri("https://maven.pkg.github.com/newlinksdev/RozcomOemAndroid")
                credentials {
                    username = "nablai"
                    password = "0c3d6d5ba247d4b949ee60ce5424c4c52bef42c8"// OEM READ
                }
            }
            
        maven {
            url "https://github.com/QuickBlox/quickblox-android-sdk-releases/raw/master/"
        }
    }
}

```


App level gragel:
```gradle
dependencies {
    implementation ('com.newlinks.intercomclient:sdk:1.0-alpha0.08rc'){
        transitive=true
    }
}
```

sample by fragment:

```
import com.newlinks.rozcomsdk.RozcomOEMCallback;
import com.newlinks.rozcomsdk.RozcomOem;


public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

       RozcomOEMCallback rozcomOEMCallback = new RozcomOEMCallback() {
            @Override
            public void onError(int i, String s) {

            }

            @Override
            public void onShowProgress() {

            }

            @Override
            public void onHideProgress() {

            }

            @Override
            public void onConnected() {

            }

            @Override
            public void onCallEnded() {

            }

            @Override
            public void onCallStarted() {

            }

            @Override
            public void onClientClosed() {

            }
        };

        RozcomOem rozcomSDFragment = new RozcomOem(this,getSupportFragmentManager(), R.id.contentFragment,rozcomOEMCallback);
        rozcomSDFragment.openClient("05444444444");

        String versionName = rozcomSDFragment.getVersionName();
        int versionCode = rozcomSDFragment.getVersionCode();

        //rozcomOem.pushReceived();
   
        //rozcomOem.close();
    }
}

 ```
 
 
 
old method, by activity
```java
import com.newlinks.rozcomsdk.RozcomOEMCallback;
import com.newlinks.rozcomsdk.RozcomOem;


public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        RozcomOem rozcomOem = new RozcomOem(this, new RozcomOEMCallback() {
            @Override
            public void onShowProgerss() {

            }

            @Override
            public void onHideProgerss() {

            }

            @Override
            public void onConnected() {

            }

            @Override
            public void onCallEnded() {

            }
        });
        rozcomOem.openClient();

        //rozcomOem.pushReceived();
        //rozcomOem.getVersionCode();
        //rozcomOem.getVersionName();
        //rozcomOem.close();
    }
}
```
