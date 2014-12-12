---
layout: post
title: "Android development on OS X without Eclipse"
date: 2012-04-18 23:44
comments: true
categories: mac
---

* [出处](http://blog.beyondthecorner.co.uk/2011/01/15/android-on-os-x-without-eclipse/)

### 介绍

因为我只是想在OS X下编译Android项目，所以不需要IDE（主要是我不喜欢Eclipse）。首先搭建开发环境。 下面是详细步骤.

### Homebrew

To get the ball rolling we’re going to start with everyone’s favourite missing package manager, [Homebrew]((http://livv.github.com/blog/2012/02/16/homebrew/). If you haven’t got Homebrew installed already then you’ll be glad to know that installation is pretty simple to do;

```
ruby -e "$(curl -fsSLk https://gist.github.com/raw/323731/install_homebrew.rb)"
```

If you haven’t got Xcode installed yet this script will install it for you. If this is the case you may want to go get a drink as it may take some time.

### Android SDK

Now that we have Homebrew installed we can get the Android SDK tools installed. Thanks to Homebrew this is a simple process and you don’t even have to visit a website, this appeals to the exceedingly lazy developer in me. Just go ahead and run;

```
brew install android
```

Once Homebrew has installed the Android SDK you can just straight away run the android command thanks to Homebrew setting everything up for you. So go ahead and run the Android SDK and AVD manager by running android on the command line. Then you can make your AVD and install the desired versions of the Android SDK. You may need to update your android tools since it appears that the Homebrew formula is a little out of date with the current version, but this is simple enough to do.
At this point let’s create an android project to make sure that everything is ready to go. I created a HelloAndroid application targeted for Android 2.1;

```
android create project --package com.example.helloandroid --activity HelloAndroid --target 3 --path <path-to-project-folder>/HelloAndroid
```

Then to make sure that everything is set up right and working fire up your Android emulator and then run ant install. Once this is done go ahead and make sure the app runs on the emulator. Assuming this works then run ant uninstall to uninstall the app from the emulator.

### Apache Maven

Whilst I do prefer to avoid a full blown IDE I do like some automation in places and Apache Maven is a big old help with this. The first thing to do is get maven installed, again thanks to Homebrew this is simple;

```
brew install maven
```

Now we need to get the project set up with maven. We will be using the Maven Android Plugin to help us out. The first thing we need to do is remove the following files;

```
rm -r bin build.xml build.properties libs
```
Next we setup our environment for the Maven Android Plugin. We need to set a ANDROID_HOME environment variable. In .bash_profile add the following line;

```
export ANDROID_HOME=`brew --prefix android`
```
Setting up the project for use with maven needs the following pom.xml file created in the root of the project;

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example.helloandroid</groupId>
  <artifactId>helloandroid</artifactId>
  <packaging>apk</packaging>
  <version>0.0.1-SNAPSHOT</version>
  <name>HelloAndroid</name>
  
  <dependencies>
    <dependency>
      <groupId>com.google.android</groupId>
      <artifactId>android</artifactId>
      <version>2.1.2</version>
      <scope>provided</scope>
    </dependency>
  </dependencies>
  
  <build>
    <sourceDirectory>src</sourceDirectory>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <configuration>
          <source>1.6</source>
          <target>1.6</target>
        </configuration>
      </plugin>
      <plugin>
        <groupId>com.jayway.maven.plugins.android.generation2</groupId>
        <artifactId>maven-android-plugin</artifactId>
        <configuration>
          <sdk>
            <path>${env.ANDROID_HOME}</path>
            <platform>1.6</platform>
          </sdk>
          <emulator>
             <avd>standard</avd>
             <wait>6000</wait>
          </emulator>
          <deleteConflictingFiles>true</deleteConflictingFiles>
        </configuration>
        <extensions>true</extensions>
      </plugin>
    </plugins>
  </build>
  
</project>
```
Once the pom.xml file is created then we can see if it is all set up right by running;

```
mvn help:describe -Dplugin=android
```

Running this should give details about goals available for the android maven plugin. For reference here are the goals;

```
Name: Maven Android Plugin - maven-android-plugin
Description: Maven Plugin for Android
Group Id: com.jayway.maven.plugins.android.generation2
Artifact Id: maven-android-plugin
Version: 2.8.3
Goal Prefix: android
 
This plugin has 16 goals:
 
android:apk
  Description: Creates the apk file. By default signs it with debug keystore.
    Change that by setting configuration parameter
    <sign><debug>false</debug></sign>.
 
android:deploy
  Description: Deploys the built apk file, or another specified apk, to a
    connected device.
    Automatically performed when running mvn integration-test (or mvn install)
    on a project with instrumentation tests.
 
android:deploy-dependencies
  Description: Deploys all directly declared dependencies of <type>apk</type>
    in this project's pom.
    Usually used in a project with instrumentation tests, to deploy the apk to
    test onto the device before running the deploying and running the
    instrumentation tests apk.
    Automatically performed when running mvn integration-test (or mvn install)
    on a project with instrumentation tests.
 
android:dex
  Description: Converts compiled Java classes to the Android dex format.
 
android:emulator-start
  Description: EmulatorStartMojo can start the Android Emulator with a
    specified Android Virtual Device (avd).
 
android:emulator-stop
  Description: EmulatorStartMojo can stop the Android Emulator with a
    specified Android Virtual Device (avd).
 
android:generate-sources
  Description: Generates R.java based on resources specified by the resources
    configuration parameter.
    Generates java files based on aidl files.
     
    If the configuration parameter deleteConflictingFiles is true (which it is
    by default), this goal has the following side-effects:
    - deletes any R.java files found in the source directory.
    - deletes any .java files with the same name as an .aidl file found in the
      source directory.
    - deletes any Thumbs.db files found in the resource directory.
 
android:instrument
  Description: Runs the instrumentation apk on device.
 
android:internal-integration-test
  Description: Internal. Do not use.
    Called automatically when the lifecycle reaches phase integration-test.
    Figures out whether to call goals in this phase; and if so, calls
    android:instrument.
 
android:internal-pre-integration-test
  Description: Internal. Do not use.
    Called automatically when the lifecycle reaches phase pre-integration-test.
    Figures out whether to call goals in this phase; and if so, calls
    android:deploy-dependencies and android:deploy.
 
android:pull
  Description: Copy file/dir from device.
 
android:push
  Description: Copy file/dir to device.
 
android:redeploy
  Description: Redeploys the built apk file, or another specified apk, to a
    connected device. This simply tries to undeploy the APK and re-deploy it.
 
android:undeploy
  Description: Undeploys the built apk file, or another specified apk, from a
    connected device.
 
android:unpack
  Description: unpack library.
 
android:zipalign
  Description: ZipalignMojo can run the zipalign command against the apk.
```

If you see that then you are all set and ready to go. I’m hoping to get some more blog posts up about my development exploits on android. If you want to read more about the maven android plugin then have a look at their website http://code.google.com/p/maven-android-plugin.

> 本该淡淡然~~~