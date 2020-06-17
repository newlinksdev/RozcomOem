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
                    password = "c76fe427b27498f947d5aa3b8be97ca5f8c26df0"// OEM
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
    implementation ('com.newlinks.intercomclient:sdk:1.0-alpha0.0'){
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

        RozcomOem rozcomSDK = new RozcomOem(this, getSupportFragmentManager(), R.id.contentFragment, 
        new RozcomOEMCallback() {
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
