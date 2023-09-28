# Optimize Android Studio performance on Windows
Android Studio performance on Windows can be impacted by a variety of factors.
This section describes how you can optimize Android Studio settings to get the best possible performance on Windows.

#Minimize the impact of Antivirus Software on build speed
Some antivirus software can interfere with the Android Studio build process, causing builds to run dramatically slower. When you run a build in Android Studio, Gradle compiles your app’s resources and source code and then packages the compiled resources together in an APK or AAB. During this process, many files are created on your computer. If your antivirus software has real-time scanning enabled, the antivirus software can force the build process to halt each time a file is created while it scans that file.

To avoid this issue, you can exclude certain directories from real-time scanning in your antivirus software.

The following list shows the default location of each Android Studio directory that you can exclude from real-time scanning:

gradle
```gradle file
  Gradle cache
      %USERPROFILE%\.gradle
```

Android Studio projects
%USERPROFILE%\AndroidStudioProjects
Android SDK
%USERPROFILE%\AppData\Local\Android\SDK
Android Studio system files

Syntax: %LOCALAPPDATA%\Google\<product><version>

Example: C:\Users\YourUserName\AppData\Local\Google\AndroidStudio4.1

# Customize directory locations for Group Policy controlled environments
If a Group Policy limits which directories you can exclude from real-time scanning on your computer, you can move your Android Studio directories to one of the locations that the centralized Group Policy already excludes.

The following list shows how to customize the location of each Android Studio directory, where C:\WorkFolder is the directory that your Group Policy already excludes:

Gradle cache
  Define the GRADLE_USER_HOME environment variable to point to C:\WorkFolder\.gradle.
Android Studio projects
  Move or create project directories in an appropriate subdirectory of C:\WorkFolder. For example, C:\WorkFolder\AndroidStudioProjects.
Android SDK
Follow these steps to customize location:

In Android Studio, open the Settings dialog (Preferences on macOS), then navigate to Appearance & Behavior > System Settings > Android SDK.

Change the value of Android SDK Location to C:\WorkFolder\AndroidSDK.

To avoid downloading the SDK again, copy the existing SDK directory, located at %USERPROFILE%\AppData\Local\Android\SDK by default, to the new location.

Android Studio system files
Follow these steps to customize location:

In Android Studio, click Help > Edit Custom Properties.

Android Studio prompts you to create an idea.properties file if you don't already have one.

Add the following line to your idea.properties file:


idea.system.path=c:/workfolder/studio/caches/trunk-system
