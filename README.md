# chimera

##Come compilare le librerie bluetooth

1. Scaricare e l'android NDK e scompattarlo da qualsiasi parte, il path che conduce al contenuto della cartella (qualcosa tipo `/user/xxx/android-ndk-r10d/`) sarà usato nei prossimi step.

2. Collegare il telefono in debug via usb ed eseguire da terminale il comando `adb pull /system/lib/libbluetooth.so`

3. Copiare il file libbluetooth.so scaricato (viene salvato nella directory dove viene lanciato il comando al punto 2) in `android-ndk-xx/platforms/android-4/arch-arm/usr/lib`

4. Nel file `jni/Application.mk` modificare il parametro `APP_PROJECT_PATH` in maniera tale che punti alla directory dove è presente la cartella `jni`. In altre parole, la parte finale del path è sempre `/androhid-read-only`, si deve modificare la parte iniziale sostituendo `~/androhid` con la directory radice del repository git (ex: `/home/vladimiro/programmazione/chimera/android-read-only`). Successivamente aprire un terminale e digitare il comando `git update-index --assume-unchanged androhid-read-only/jni/Application.mk` per fare in modo che git ignori le modifiche locali al file.

5. Seguire le istruzioni:

Now you must get the header files for the bluetooth and cutils includes. You can download them from the following two repositories from the CyanogenMod project:

https://github.com/CyanogenMod/android_external_bluetooth_bluez
https://github.com/CyanogenMod/android_system_core

Then copy the directory lib/bluetooth from the Android BlueZ code and the directory include/cutils from the Android System Core code to the following directory inside the Android NDK:

>platforms/android-4/arch-arm/usr/include/



