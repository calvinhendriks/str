README

Link to State Machine Learner
https://github.com/wesleyvanderlee/AppSecurity/tree/master/code/bsc-modify

Link to Andro Server (needed for login):
https://github.com/dineshshetty/Android-InsecureBankv2/tree/master/AndroLabServer

Link to Apk (modified preferences):

Link to Reversed Apk (backdoor login): 

Link to tools used in video:
dex2jar: https://github.com/pxb1988/dex2jar/releases
JD-GUI: http://jd.benow.ca/
Apktool: https://ibotpeaches.github.io/Apktool/

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
	
Credentials for insecurebankv2.apk

user: dinesh
pass: Dinesh@123$

user: jack
pass: Jack@123$


How to install a apk using adb
How to generate keystore

Shortlabels
sed '/1-NOTFOUND/d' inputfile| sed -e 's/\<0-OK\>//g' > outputfile


