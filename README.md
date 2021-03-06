#LoggingInterceptor

[![Build Status](https://travis-ci.org/ihsanbal/LoggingInterceptor.svg?branch=master)](https://travis-ci.org/ihsanbal/LoggingInterceptor)
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-LoggingInterceptor-green.svg?style=flat-square)](https://android-arsenal.com/details/1/5342)
[![API](https://img.shields.io/badge/API-9%2B-brightgreen.svg?style=flat-square)](https://developer.android.com/about/versions/android-2.3.html)
[![SwaggerUI](https://img.shields.io/badge/Swagger-mockable.io-orange.svg?style=flat-square)](https://www.mockable.io/swagger/index.html?url=https%3A%2F%2Fdemo2961085.mockable.io%3Fopenapi#!/demo2961085)

Interceptor for [OkHttp3](https://github.com/square/okhttp) with pretty logger

<p align="center">
    <img src="https://github.com/ihsanbal/LoggingInterceptor/blob/master/logging.gif" width="580" height="440"/>
</p>

Usage
--------

```java

OkHttpClient.Builder client = new OkHttpClient.Builder();
        client.addInterceptor(new LoggingInterceptor.Builder()
                .loggable(BuildConfig.DEBUG)
                .setLevel(Level.BASIC)
                .log(Log.INFO)
                .request("Request")
                .response("Response")
                .addHeader("version", BuildConfig.VERSION_NAME)
                .build());
        OkHttpClient okHttpClient = client.build();

//You can use with Retrofit
Retrofit retrofitAdapter = new Retrofit.Builder()
            .addConverterFactory(GsonConverterFactory.create())
            .addCallAdapterFactory(RxJavaCallAdapterFactory.create())
            .baseUrl("https://.../")
            .client(okHttpClient)
            .build();
```

Download
--------

Gradle:
```groovy
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}

dependencies {
	    compile 'com.github.ihsanbal:LoggingInterceptor:1.0.4'
	}
```

Maven:
```xml
<repository>
   <id>jitpack.io</id>
   <url>https://jitpack.io</url>
</repository>

<dependency>
	    <groupId>com.github.ihsanbal</groupId>
	    <artifactId>LoggingInterceptor</artifactId>
	    <version>1.0.4</version>
</dependency>
```
#Tips
Level
--------
	setLevel(Level.BASIC)
		      .NONE // No logs
		      .BASIC // Logging url,method,headers and body.
		      .HEADERS // Logging headers
		      .BODY // Logging body
Log
--------
	loggable(BuildConfig.DEBUG) // enable/disable sending logs output.
	log(Log.INFO) // setting log type
`<link>` : https://developer.android.com/reference/android/util/Log.html

Tag
--------
	tag("LoggingI") // Request & response each log tag
	request("request") // Request log tag
	response("response") // Response log tag
Header
--------
	addHeader("token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9 ") // Adding to request
`<link>` : https://github.com/square/okhttp/wiki/Recipes

#Notes
Use the filter & configure logcat header for a better result

<p align="left">
    <img src="https://github.com/ihsanbal/LoggingInterceptor/blob/master/images/screen_shot_5.png" width="280" height="155"/>
    <img src="https://github.com/ihsanbal/LoggingInterceptor/blob/master/images/screen_shot_4.png" width="280" height="155"/>
</p>