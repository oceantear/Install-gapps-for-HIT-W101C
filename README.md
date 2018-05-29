# Install-gapps-for-HIT-W101C


## 1.Download Open GAPPS.
    from https://opengapps.org/   
    platform: ARM   
    Android : 5.1   
    Variant : pico  
  
## 2.New some folders
    mkdir ~/opengapps   
    mkdir ~/opengapps/pkg   
    mkdir ~/opengapps/tmp   
    mkdir ~/opengapps/sys   
  
## 3.Extract download file
    unzip /[path_to]/[name_of_opengapps_archive].zip -d ~/opengapps/pkg   
## 4.Unzip files
    find . -name '*?.tar.[g|l|x]z?*' -o -name '*?.tar?*' -exec tar -xvf {} -C ~/opengapps/tmp/ \;   
## 5.Create script file mygapps.sh   
    #!/bin/bash   
    for dir in ~/opengapps/tmp/*/   
      do   
        pkg=${dir%*/}   
        dpi=$(ls -1 $pkg | head -1)      

        echo "Preparing $pkg/$dpi"   
        rsync -aq $pkg/$dpi/ ~/opengapps/sys/   
      done   
## 6.Change script file permission
    chmod 777 myapps.sh
## 7.Execute script file
    ./myapps.sh
## 8.Remove some apks
    Calculator   
    Email   
    Exchange2   
    SpeechRecorder   
## 9.Push apk into system folder
    adb push ~/opengapps/sys/. /system/.
## 10.Use adb push some files into folder /system/lib  
    libgmscore.so
    libleveldbjni.so
    libconscrypt_gmscore_jni.so
    libAppDataSearch.so
  
  
