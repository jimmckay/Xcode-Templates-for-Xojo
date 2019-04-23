**Installation:**

Download the templates. Move the iOS and macOS folders to "~/Library/Developer/Xcode/Templates/Project Templates" creating folders as needed.

**Usage:**

Create an Xcode project with the same name as your Xojo project. 
***BE CAREFUL NOT TO OVERWRITE THE Xojo PROJECT!***

After creating your Xcode project, move everything in the Xcode project folder to your Xojo project folder.


Next, add a build script to the Xojo project, active for release.

```
dim setAppPath as string = "export XOJO_BUILD_LOCATION="""+CurrentBuildLocationNative+"/"+CurrentBuildAppName+".app"";"

call doshellcommand(setAppPath + "cd ""$PROJECT_PATH""; xcodebuild clean -scheme Release > build_log.txt")
call doshellcommand(setAppPath + "cd ""$PROJECT_PATH""; xcodebuild -scheme Release >> build_log.txt")
call doshellcommand(setAppPath + "cd ""$PROJECT_PATH""; xcodebuild archive -scheme Release >> build_log.txt")
```



To debug the Xojo app in sandboxed mode, add a Build script active for debug:

```
dim setAppPath as string = "export XOJO_BUILD_LOCATION="""+CurrentBuildLocationNative+"/"+CurrentBuildAppName+".app"";"

call doshellcommand(setAppPath + " cd ""$PROJECT_PATH"";  xcodebuild -scheme Debug > debug_log.txt")
```


*Be sure to set "Auto Increment Version" to On in Xojo and make sure you're building 64bit.*


You can safely delete this file!
