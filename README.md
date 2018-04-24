README

Link to State Machine Learner
https://github.com/wesleyvanderlee/AppSecurity/tree/master/code/bsc-modify

Link to Andro Server (needed for login):
https://github.com/dineshshetty/Android-InsecureBankv2/tree/master/AndroLabServer

Link to tools used in video:
dex2jar: https://github.com/pxb1988/dex2jar/releases
JD-GUI: http://jd.benow.ca/
Apktool: https://ibotpeaches.github.io/Apktool/

The original apk (only server is fixed) and the reverse engineered apk are in the apk folder

Fixes to the Learner:
Comment out the following lines from ResultProcessor.java:
this.algs.add(new ImproperPlatformUsage());
this.algs.add(new DeadEnds());
this.algs.add(new AuthenticationBypass());
	
If you are a Windows user, you will probably have to create the alphabet folders yourself.
You need to create 3 folders. 
	-window_dumps/ inside alphabet/ , 
	-[your-alphabet-name]/ inside window_dumps/ 
	-graphs/ inside bsc-modify/.
	
Additionaly, you can turn on Cache:
In QueryCache.java change:

boolean HARDQUERYCACHEREAD = false;
boolean HARDQUERYCACHEWRITE = false;

to true. 

Replace the line driver.getKeyboard().sendKeys(Keys.RETURN); with driver.hideKeyboard(); 
in the enterText method of AndroidInstrumentator and remove the "! " string that gets prepended to the input. (Credit to Tom Catshoek)
	
Credentials for insecurebankv2.apk:

user: dinesh
pass: Dinesh@123$

user: jack
pass: Jack@123$

How to install the Apk on an Emulator:
create an AVD using Android Studio or use "create avd -n name -k "sdk_id" [-c {path|size}] [-f] [-p path]"  
list AVDs with "path/to/android_sdk/tools/bin/avdmanager.exe" list avd . 
start emulator with "path/to/android_sdk/emulator/emulator.exe" -avd NAMEOFAVD. 
install apk with "path/to/android_sdk/platform-tools/adb.exe" install apkname.apk

to generate a key store:
"path/to/jdk/bin/keytool.exe" -genkey -keystore KEYSTORENAME.keystore -validity AMOUNTINYEARS -alias ALIASNAME

to sign apk:
"path/to/jdk/bin/jarsigner.exe" -keystore KEYSTORENAME apkname.apk ALIASNAME

The labels in the graph are pretty long. To shorten them, use shortlabels.py:
shortlabels.py inputname outputname

The graph contains a lot of edges with NOTFOUND. To remove them, use the following bash command:
sed '/1-NOTFOUND/d' inputfile| sed -e 's/\<0-OK\>//g' > outputfile

How to use dex2jar:
Mac: sh d2j-dex2jar.sh -f ~/path/to/apk_to_decompile.apk
Windows: d2j-dex2jar.bat -f ~/path/to/apk_to_decompile.apk
jar will be in 	dex2jar folder apk_name-dex2jar.jar

How to use Apktool:
Convert apk to smali: apktool d apkname.apk
convert smali back to apk: apktool b apkname(folder)  //The file will be in apknamefolder/dist



