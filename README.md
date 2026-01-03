
## Preview:
```
λ ./apk-get telegram
1) Telegram X
2) Telegram
3) Telegram (Google Play version)
4) Plus Messenger
5) Telegram Beta
6) Shurgram

Select one from above: 2

Selected: Telegram
 - Scraping the file id..    OK
 - Scraping the file path..  OK
 - Downloading the APK
telegram.apk                   100%[==================================>]  70.64M  4.81MB/s    in 16s     
Do you want to install the apk? (y/n): n
```
## Usage
Example installation from termux shell
```bash
# Install curl if you don't have (android shell (toybox or busybox) generally alraedy have it)
pkg install curl
# Download the script
curl -L -o apk-get https://github.com/KebabLord/apk-get/raw/main/apk-get
# Give it execute permission
chmod +x apk-get
# Now you can run it with ./apk-get "application name"
```
### Automatic APK installation
There are two ways you can have APK installation enabled on the script.
If you already have root on your phone, this script will just automatically install the apk by android's package manager (pm). You don't have to do anything.

But if you don't have root, script uses `termux-api`'s `termux-open` feature. In order to utilize it you need to follow these steps:

 1. Install termux-api application
 2. Install termux-api package: `pkg install termux-api`
 3. Give both the termux and termux-api apps the "install unknown apps" permission
 4. Uncomment `#allow-external-apps = true` inside `~/.termux/termux.properties`

### Is XAPK installation supported?
At the moment, it's not implemented as it's much more complex to implement it on bash scripting level. And i don't have time for it.

### Can I run this script over adb shell?
Yes, but in order to be able to install the apks,  you have to run the script inside `/data/local/tmp` folder so that android's package manager (pm) can see the apk file.

### Where the APK files are downloaded at?
The same directory you executed the script from.

### Why using Uptodown as apk repository?
Because apkmirror has cloudflare protection making it impossible to scrape the download url, without using a webdriver (bloat). Uptodown on the other hand seems curl friendly with a proper user-agent.

Also Uptodown seems like a legitimate company located in Spain.<sup>[1](https://www.linkedin.com/company/uptodown/) [2](https://en.uptodown.com/about-us/our-company)</sup> So it seemed more legit than APKMirror to me.
I also compared the MD5 hashes of some random app APKs with the ones on APKMirror, and they are identical. Yet, I don't accept any responsibility, use at your own risk. 


