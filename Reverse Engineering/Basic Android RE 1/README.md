# Basic Android RE 1
[Link to the challenge](https://ctflearn.com/challenge/962)

My first RE CTF!

## Step 1
We are given an APK. I downloaded it and used some basic commands (`file`, `strings`, and `exiftool`).

Nothing interesting.

## Step 2
I knew a tool called `apktool` that I used in class.
So I tried to reverse this APK using this tool.

```
$ apktool d BasicAndroidRE1.apk 
I: Using Apktool 2.5.0 on BasicAndroidRE1.apk
I: Loading resource table...
I: Decoding AndroidManifest.xml with resources...
I: Loading resource table from file: 
I: Regular manifest package...
I: Decoding file-resources...
I: Decoding values */* XMLs...
I: Baksmaling classes.dex...
I: Copying assets and libs...
I: Copying unknown files...
I: Copying original files...
```

## Step 3
Now that I had the "source code" of this APK, I looked over the `AndroidManifest.xml` to see where the app starts.

```xml
<activity android:name="com.example.secondapp.MainActivity">
    <intent-filter>
        <action android:name="android.intent.action.MAIN"/>
        <category android:name="android.intent.category.LAUNCHER"/>
     </intent-filter>
</activity>
```

It looked like the app starting point was `com.example.secondapp.MainActivity`.

So I wanted to see this `MainActivity`.

## Step 4
Looking at `MainActivity.smali` I found the string `Success! CTFlearn{` and `_is_not_secure!}`.

I was just missing the middle part.

When I looked even more in the file, 2 interesting lines came up:
- `invoke-static {v0}, Lorg/apache/commons/codec/digest/DigestUtils;->md5Hex(Ljava/lang/String;)Ljava$` 
- `const-string v1, "b74dec4f39d35b6a2e6c48e637c8aedb"`

This app is somehow using MD5 and I had a const string. So I tried to [decode it using MD5](https://md5decrypt.net/)

And got `Spring2019`. I had the flag!

## Solution
The flag is `CTFlearn{Spring2019_is_not_secure!}`
