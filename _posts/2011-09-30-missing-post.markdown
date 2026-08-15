---
layout: post
title: "Missing post..."
excerpt: "All the links to the first guide in my last post seem to be broken... I include here for reference and will hopefully update and convert to a linux specific guide. I also remember having to bump up the validity time too. 29-09-2010&nbsp;…"
date: 2011-09-30 02:42:00 +0000
blogger_published_at: "2011-09-30T02:42:00.000-07:00"
categories: article
title-image: no_image.svg
source_url: "https://android-development-adventures.blogspot.com/2011/09/missing-post.html"
---

{% raw %}
<div dir="ltr" style="text-align: left;" trbidi="on">All the links to the first guide in my last post seem to be broken... I include here for reference and will hopefully update and convert to a linux specific guide. I also remember having to bump up the validity time too.<br />
<br />
<span class="postdate old">           <span class="date">29-09-2010&nbsp;<span class="time">21: 23</span></span></span><br />
<br />
<div class="username_container">         <div class="popupmenu memberaction" id="yui-gen18">  <a class="username online " href="http://www.androidworld.it/forum/members/ciso-2/" rel="nofollow" title="ciso ora è in linea"><strong><span style="color: red; font-weight: bold;">ciso</span></strong></a>   </div></div><span class="usertitle">     Amministratore    </span>                    <a class="postuseravatar" href="http://www.androidworld.it/forum/members/ciso-2/" rel="nofollow" title="ciso ora è in linea">     <img alt="L'avatar di ciso" src="http://www.androidworld.it/forum/avatars/ciso-2.gif?dateline=1275245828" title="L'avatar di ciso" /></a><a class="postuseravatar" href="http://www.androidworld.it/forum/members/ciso-2/" rel="nofollow" title="ciso ora è in linea">    </a><br />
[How To] Publish the app created with App Inventor in the Android Market<br />
<br />
&nbsp;&nbsp;&nbsp; Publish the app created with App Inventor in the Android Market<br />
<br />
&nbsp;&nbsp;&nbsp; We succeded and the guide should be final.<br />
<br />
&nbsp;&nbsp;&nbsp; What I'm about to describe is created to overcome the impossibility of publishing apps created with App Inventor in the Android Market<br />
<br />
&nbsp;&nbsp;&nbsp; What you need:<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.6 Java Development Kit and Runtime Environment 1.6 already installed on your PC<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Android SDK already installed and running<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Appinventor Extras<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; APKTool<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Auto-Sign 6.5<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; .... A lot of Patience<br />
<br />
&nbsp;&nbsp;&nbsp; 1) Creating the key<br />
<br />
&nbsp;&nbsp;&nbsp; This procedure is a one-off and we don't need to do those steps every time.<br />
<br />
&nbsp;&nbsp;&nbsp; So, thanks to the JAVA SDK we will create a private key, which will be used for publishing our applications<br />
<br />
&nbsp;&nbsp;&nbsp; From the Bin folder of the Java SDK we'll execute in a terminal:<br />
<br />
codice:<br />
keytool.exe -genkey -v -keystore my-release-key.keystore -alias aliasname -keyalg RSA -keysize 2048 -validity 10000<br />
<br />
The Market requires that applications need to publish the private key has a duration subsequent to October 22, 2033, so we'll use a validity of 10000 days (over 27 years!).<br />
<br />
2) Customize the Icon of the application<br />
<br />
Download the APK file on a local folder on your computer.<br />
<br />
We'll use AutoSigner for those steps: (thanks to Marcor Online info@marcoronline.tk for this part).<br />
Open the apk file with 7zip.<br />
Delete META-INF folder (which is the folder where the application contains the certificates, no longer valid after the change).<br />
The images are generally stored in the folder res\drawable, and in particular the icon of the program is called ya.png. Extract all the images you want with your favorite software (we use 7zip).<br />
Be careful not to change the size in pixels and not to change the name and extension.<br />
Once you have completed the changes you go to put the files again into the apk (using 7zip) by simply dragging and overwriting the original.<br />
Close 7zip and rename your program Launcher.apk.<br />
Extract the contents of the Auto-Sign v0.65.exe and copy the Launcher.apk file inside the folder Auto-Sign\update\app.<br />
Run the tool by the Auto-Sign v0.65.exe executable and iselect from the drop down menù Launcher.apk. (The name should been green. If not, you've made something wrong.)<br />
Now click on Autosign and in a few seconds you'll get a confirmation message.<br />
Inside the folder Auto-Sign\update\app will be a Launcher_signed.apk. You can delete the old file and keep only the signed one.<br />
<br />
3) Edit the APK to be compatible with the Market<br />
<br />
Decompile our apk<br />
<br />
codice:<br />
apktool -s pre-nomeapk.apk<br />
<br />
in the just created folder called pre-nomeapk, go editing the AndroidManifest.xml file.<br />
<br />
First we add the version of the application by adding the keyword "android: versionCode" and "android: versionName" in the keyword "package", just like this example:<br />
<br />
codice:<br />
&lt;? xml version = "1.0" encoding = "UTF-8"?&gt;<br />
&lt;manifest xmlns: android = "http://schemas.android.com/apk/res/android"<br />
package = "appinventor.xyz.xyz"<br />
android:versionCode = "1"<br />
android:versionName = "1.0"&gt;<br />
<br />
Specify the minimum version of Android is needed to run the application. Beware that the Market has a bug at the moment, and does not support applications compiled for Froyo android 2.2. Consider the following table:<br />
<br />
codice:<br />
API Level -&gt; Android Platform Version<br />
1 -&gt; 1.0<br />
2 -&gt; 1.1<br />
3 -&gt; 1.5<br />
4 -&gt; 1.6<br />
5 -&gt; 2.0<br />
6 -&gt; 2.0.1<br />
7 -&gt; 2.1<br />
8 -&gt; 2.2<br />
<br />
If your application needs Eclair we enter the following keyword:<br />
codice:<br />
&lt;uses-sdk android:minSdkVersion="7" /&gt;<br />
<br />
Finally fix the last things needed to make compatible the apk to the Market<br />
<br />
Remove the android:icon keyworld on this line:<br />
<br />
codice:<br />
&lt;activity android:label="123" android:icon="@drawable/ya" android:name=".Screen1"&gt;<br />
<br />
and add it in this line:<br />
<br />
codice:<br />
&lt;application android:label="XXXXX" android:debuggable="true"&gt;<br />
<br />
Also on the line relative to the "application", remove the key "android_: debuggable"<br />
<br />
In the end the AndroidManifest.xml will result like this:<br />
<br />
codice:<br />
&lt;? xml version = "1.0" encoding = "UTF-8"?&gt;<br />
&lt;manifest xmlns: android = "http://schemas.android.com/apk/res/android"<br />
package = "appinventor.xyz.xyz"<br />
android:versionCode = "1"<br />
android:versionName = "1.0"&gt;<br />
&lt;uses-sdk android:minSdkVersion="3" /&gt;<br />
......<br />
&lt;application android:label="XXXX" android:icon="@drawable/ya"&gt;<br />
&lt;activity android:label="123" android:name=".Screen1"&gt;<br />
....<br />
&lt;/activity&gt;<br />
&lt;/application&gt;<br />
&lt;/manifest&gt;<br />
<br />
Now compile the apk again:<br />
codice:<br />
<br />
apktool b pre-nomeapk<br />
<br />
With 7zip open the apk and remove the file in the META-INF folder like:<br />
<br />
codice:<br />
ANDROIDK.SF<br />
ANDROIDK.RSA<br />
<br />
<br />
<br />
<span class="postdate old"><span class="date"><span class="time">&nbsp;</span></span>         </span>    <span class="nodecontrols">           </span><br />
<br />
<span class="nodecontrols"><a class="postcounter" href="http://www.androidworld.it/forum/app-inventor-91/%5Bhow-%5D-publish-app-created-app-inventor-android-market-4597/#post26130" name="post26130"></a></span></div>
{% endraw %}
