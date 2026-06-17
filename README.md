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

KothaZ Java Usage Guide
_____________________________

KothaZ is a Volley-powered Android networking library by KothaLab.

Required Imports

import android.os.Bundle;
import android.util.Log;

import androidx.appcompat.app.AppCompatActivity;

import com.kothalab.kothaz.KothaCallback;
import com.kothalab.kothaz.KothaDownloadCallback;
import com.kothalab.kothaz.KothaError;
import com.kothalab.kothaz.KothaZ;

import org.json.JSONArray;
import org.json.JSONException;
import org.json.JSONObject;

import java.io.File;
import java.util.HashMap;
import java.util.Map;

Complete Java Example

public class KothaZJavaExamplesActivity extends AppCompatActivity {

    private static final String TAG = "KothaZ-Java";
    private static final String BASE_URL = "https://example.com/api";

    private final Object profileRequestTag = "profile_request_tag";
    private final Object uploadRequestTag = "upload_request_tag";
    private final Object downloadRequestTag = "download_request_tag";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        /*
         * Volley-powered RequestQueue initialize.
         * Call this once before using KothaZ.
         */
        KothaZ.init(getApplicationContext());

        /*
         * Call any method when needed.
         * Example:
         * getJsonObjectResponse();
         */
    }

    // 1. GET Request + JSON Object response
    private void getJsonObjectResponse() {
        KothaZ.get(BASE_URL + "/user/1")
                .header("Accept", "application/json")
                .executeJsonObject(new KothaCallback<JSONObject>() {
                    @Override
                    public void onSuccess(JSONObject response) {
                        Log.d(TAG, "GET JSON Object: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 2. GET Request + JSON Array response
    private void getJsonArrayResponse() {
        KothaZ.get(BASE_URL + "/posts")
                .header("Accept", "application/json")
                .executeJsonArray(new KothaCallback<JSONArray>() {
                    @Override
                    public void onSuccess(JSONArray response) {
                        Log.d(TAG, "GET JSON Array: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 3. GET Request + String response
    private void getStringResponse() {
        KothaZ.get(BASE_URL + "/plain-text")
                .executeString(new KothaCallback<String>() {
                    @Override
                    public void onSuccess(String response) {
                        Log.d(TAG, "GET String: " + response);
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 4. POST Request + Form parameters + String response
    private void postFormParametersStringResponse() {
        KothaZ.post(BASE_URL + "/login")
                .header("Accept", "application/json")
                .param("email", "doctor@example.com")
                .param("password", "123456")
                .executeString(new KothaCallback<String>() {
                    @Override
                    public void onSuccess(String response) {
                        Log.d(TAG, "POST Form String: " + response);
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 5. POST Request + Form parameters + JSON Object response
    // Use this when your server returns JSON but form data is submitted.
    private void postFormParametersJsonObjectResponse() {
        KothaZ.post(BASE_URL + "/login")
                .header("Accept", "application/json")
                .param("email", "doctor@example.com")
                .param("password", "123456")
                .executeString(new KothaCallback<String>() {
                    @Override
                    public void onSuccess(String response) {
                        try {
                            JSONObject jsonObject = new JSONObject(response);
                            Log.d(TAG, "POST Form JSON Object: " + jsonObject.toString());
                        } catch (JSONException e) {
                            Log.e(TAG, "JSON Parse Error: " + e.getMessage());
                        }
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 6. POST Request + JSON request body + JSON Object response
    private void postJsonBody() {
        try {
            JSONObject body = new JSONObject();
            body.put("title", "KothaZ");
            body.put("message", "Hello from KothaLab");

            KothaZ.post(BASE_URL + "/create")
                    .header("Accept", "application/json")
                    .header("Content-Type", "application/json")
                    .body(body)
                    .executeJsonObject(new KothaCallback<JSONObject>() {
                        @Override
                        public void onSuccess(JSONObject response) {
                            Log.d(TAG, "POST JSON Body: " + response.toString());
                        }

                        @Override
                        public void onError(KothaError error) {
                            logError(error);
                        }
                    });

        } catch (JSONException e) {
            Log.e(TAG, "JSON Create Error: " + e.getMessage());
        }
    }

    // 7. PUT Request + JSON body + JSON Object response
    private void putJsonBody() {
        try {
            JSONObject body = new JSONObject();
            body.put("name", "Dr. Anjan Biswas Kabbo");
            body.put("company", "KothaLab");

            KothaZ.put(BASE_URL + "/user/1")
                    .header("Accept", "application/json")
                    .header("Content-Type", "application/json")
                    .body(body)
                    .executeJsonObject(new KothaCallback<JSONObject>() {
                        @Override
                        public void onSuccess(JSONObject response) {
                            Log.d(TAG, "PUT Response: " + response.toString());
                        }

                        @Override
                        public void onError(KothaError error) {
                            logError(error);
                        }
                    });

        } catch (JSONException e) {
            Log.e(TAG, "JSON Create Error: " + e.getMessage());
        }
    }

    // 8. PATCH Request + JSON body + JSON Object response
    private void patchJsonBody() {
        try {
            JSONObject body = new JSONObject();
            body.put("status", "active");

            KothaZ.patch(BASE_URL + "/user/1")
                    .header("Accept", "application/json")
                    .header("Content-Type", "application/json")
                    .body(body)
                    .executeJsonObject(new KothaCallback<JSONObject>() {
                        @Override
                        public void onSuccess(JSONObject response) {
                            Log.d(TAG, "PATCH Response: " + response.toString());
                        }

                        @Override
                        public void onError(KothaError error) {
                            logError(error);
                        }
                    });

        } catch (JSONException e) {
            Log.e(TAG, "JSON Create Error: " + e.getMessage());
        }
    }

    // 9. DELETE Request + JSON Object response
    private void deleteRequest() {
        KothaZ.delete(BASE_URL + "/user/1")
                .header("Accept", "application/json")
                .executeJsonObject(new KothaCallback<JSONObject>() {
                    @Override
                    public void onSuccess(JSONObject response) {
                        Log.d(TAG, "DELETE Response: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 10. Custom headers
    private void requestWithCustomHeaders() {
        Map<String, String> headers = new HashMap<>();
        headers.put("Accept", "application/json");
        headers.put("Authorization", "Bearer YOUR_ACCESS_TOKEN");
        headers.put("X-App-Name", "KothaZ");

        KothaZ.get(BASE_URL + "/secure/profile")
                .headers(headers)
                .executeJsonObject(new KothaCallback<JSONObject>() {
                    @Override
                    public void onSuccess(JSONObject response) {
                        Log.d(TAG, "Custom Headers Response: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 11. Request timeout and retry
    private void requestWithTimeoutAndRetry() {
        KothaZ.get(BASE_URL + "/slow-endpoint")
                .timeout(15000)
                .retry(2, 1.5f)
                .executeJsonObject(new KothaCallback<JSONObject>() {
                    @Override
                    public void onSuccess(JSONObject response) {
                        Log.d(TAG, "Timeout Retry Response: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 12. Request cache control: enable cache

    private void requestWithCacheEnabled() {
        KothaZ.get(BASE_URL + "/cached-posts")
                .cache(true)
                .executeJsonArray(new KothaCallback<JSONArray>() {
                    @Override
                    public void onSuccess(JSONArray response) {
                        Log.d(TAG, "Cached Response: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 13. Request cache control: disable cache
    private void requestWithCacheDisabled() {
        KothaZ.get(BASE_URL + "/fresh-data")
                .cache(false)
                .executeJsonObject(new KothaCallback<JSONObject>() {
                    @Override
                    public void onSuccess(JSONObject response) {
                        Log.d(TAG, "Fresh Response: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 14. Clear all Volley cache
    private void clearAllCache() {
        KothaZ.clearCache();
        Log.d(TAG, "KothaZ cache cleared");
    }

    // 15. Cancel single request by tag
    private void startTaggedRequest() {
        KothaZ.get(BASE_URL + "/profile")
                .tag(profileRequestTag)
                .executeJsonObject(new KothaCallback<JSONObject>() {
                    @Override
                    public void onSuccess(JSONObject response) {
                        Log.d(TAG, "Tagged Request Response: " + response.toString());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    private void cancelSingleRequestByTag() {
        KothaZ.cancel(profileRequestTag);
        Log.d(TAG, "Single request cancelled by tag");
    }

    // 16. Cancel all requests
    private void cancelAllRequests() {
        KothaZ.cancelAll();
        Log.d(TAG, "All requests cancelled");
    }

    // 17. Multipart file upload
    private void multipartFileUpload() {
        File file = new File(getExternalFilesDir(null), "photo.jpg");

        KothaZ.upload(BASE_URL + "/upload")
                .tag(uploadRequestTag)
                .header("Accept", "application/json")
                .param("user_id", "10")
                .param("type", "profile_photo")
                .addFile("avatar", file, "image/jpeg")
                .timeout(60000)
                .retry(1, 1.0f)
                .executeString(new KothaCallback<String>() {
                    @Override
                    public void onSuccess(String response) {
                        Log.d(TAG, "Upload Response: " + response);
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 18. File download
    private void fileDownload() {
        File outputFile = new File(getExternalFilesDir(null), "kothaz_report.pdf");

        KothaZ.download(BASE_URL + "/download/report.pdf")
                .tag(downloadRequestTag)
                .header("Accept", "application/pdf")
                .timeout(60000)
                .retry(1, 1.0f)
                .executeDownload(outputFile, new KothaDownloadCallback() {
                    @Override
                    public void onSuccess(File file) {
                        Log.d(TAG, "File downloaded: " + file.getAbsolutePath());
                    }

                    @Override
                    public void onError(KothaError error) {
                        logError(error);
                    }
                });
    }

    // 19. Volley-powered RequestQueue
    private void initializeVolleyPoweredRequestQueue() {
        KothaZ.init(getApplicationContext());
        Log.d(TAG, "KothaZ Volley-powered RequestQueue initialized");
    }

    // Common error handler
    private void logError(KothaError error) {
        Log.e(TAG, "Error Message: " + error.getMessage());
        Log.e(TAG, "Status Code: " + error.getStatusCode());

        byte[] responseBody = error.getResponseBody();
        if (responseBody != null) {
            Log.e(TAG, "Response Body: " + new String(responseBody));
        }
    }
}


## License

MIT License.
