# RozcomOem


Android alpha:

Top level gradle:

allprojects {
    repositories {
        google()
        jcenter()
        mavenCentral()
            maven {
                name = "GitHubPackages"
                url = uri("https://maven.pkg.github.com/newlinksdev/RozcomOem")
                credentials {
                    username = "nablai"
                    password = "d633adffe58a5e042da1d2040af9b493926f4409"
                }
            }
        maven {
            url "https://github.com/QuickBlox/quickblox-android-sdk-releases/raw/master/"
        }
    }
}


App level gragel:

dependencies {
    implementation ('com.newlinks.intercomclient:sdk:1.0-alpha0.0'){
        transitive=true
    }
}

sample:

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
    }
}
