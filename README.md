# KothaZ

**KothaZ** is a Volley-powered Android networking library by **KothaLab**.

Owner: `dranjanbiswas`  
Company: `KothaLab`  
Package: `com.kothalab.kothaz`  
Version: `v1.1.0`

## What KothaZ can do

- GET, POST, PUT, PATCH, DELETE requests
- JSON Object response
- JSON Array response
- String response
- Form parameters
- JSON request body
- Custom headers
- Request timeout and retry
- Request cache control
- Cancel single request by tag
- Cancel all requests
- Multipart file upload
- File download
- Volley-powered request queue

## Install with Gradle

### 1. Add JitPack repository

`settings.gradle`:

```gradle
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}
```

### 2. Add KothaZ dependency

`app/build.gradle`:

```gradle
dependencies {
    implementation 'com.github.dranjanbiswas:KothaZ:v1.1.0'
}
```

### 3. Add Internet permission

`AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

### 4. Sync Android Studio

```text
Android Studio -> File -> Sync Project with Gradle Files
```

## Documentation

- [Gradle Implementation Guide](docs/GRADLE_IMPLEMENTATION.md)
- [Java Usage Guide](docs/JAVA_USAGE.md)
- [Kotlin Usage Guide](docs/KOTLIN_USAGE.md)
- [Windows 10 Upload Guide](START_HERE_WINDOWS_10.md)
- [Publishing Guide](PUBLISHING.md)

## Java quick example

```java
KothaZ.init(getApplicationContext());

KothaZ.get("https://example.com/api/posts")
        .executeJsonObject(new KothaCallback<JSONObject>() {
            @Override
            public void onSuccess(JSONObject response) {
                Log.d("KothaZ", response.toString());
            }

            @Override
            public void onError(KothaError error) {
                Log.e("KothaZ", error.getMessage());
            }
        });
```

## Kotlin quick example

```kotlin
KothaZ.init(applicationContext)

KothaZ.get("https://example.com/api/posts")
    .executeJsonObject(object : KothaCallback<JSONObject> {
        override fun onSuccess(response: JSONObject) {
            Log.d("KothaZ", response.toString())
        }

        override fun onError(error: KothaError) {
            Log.e("KothaZ", error.message)
        }
    })
```

## License

MIT License.
