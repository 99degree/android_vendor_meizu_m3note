# android_vendor_meizu_m3note
Binary file for M3 note and various tools for unbrick the phone

Flyme 6.3.5.0A

Files are in below release:
https://github.com/99degree/android_vendor_meizu_m3note/releases/tag/20210412

Below are rom dump files for unbrick:
 boot.img                     cache.img
custom.img                   devinfo.img                  expdb                        file_contexts.bin
frp.img                      keystore                     lk.bin                       logo.bin
md1arm7.img                  md1dsp.img                   md1rom.img                   md3rom.img
metadata                     MT6755_Android_scatter.txt   nvdata.img                   oemkeystore
para.img                     ppl                          preloader_mz6755_66_n.bin    proinfo
protect1                     protext2                     recovery.img                 rstinfo
scatter.txt                  seccfg                       sero.img                     system.img
trustzone.bin                type.txt                     userdata.img

Recovery img is regenerated by flyme first boot.

To reflash the phone, first read  https://github.com/MTK-bypass/bypass_utility then clone both bypass-utility and exploits_collection.
then put exploits_collection/* into bypass-utility. Follow bypass-utility to install libusb-win32, grant mtk vcom driver with libusb-win32 filter driver. In python3 env, install pip3 and all needed tool stated in bypass-utility. Then first run python main.py in cmd prompt. 

Below are prompt of DA auth bypass when later on restart the phone.
c:\d_drive\bypass_utility>python main.py
[2021-04-12 21:46:43.788916] Waiting for device
[2021-04-12 21:48:35.708846] Found port = COM7

[2021-04-12 21:48:36.243498] Device hw code: 0x326
[2021-04-12 21:48:36.243498] Device hw sub code: 0x8a00
[2021-04-12 21:48:36.248616] Device hw version: 0xcb00
[2021-04-12 21:48:36.248616] Device sw version: 0x1
[2021-04-12 21:48:36.248616] Device secure boot: True
[2021-04-12 21:48:36.248616] Device serial link authorization: True
[2021-04-12 21:48:36.253123] Device download agent authorization: True


[2021-04-12 21:48:36.253123] Found device in preloader mode, trying to crash...

[2021-04-12 21:48:36.258150] status is 2001

[2021-04-12 21:48:36.258150] Waiting for device
[2021-04-12 21:48:37.296433] Found port = COM6

[2021-04-12 21:48:37.378726] Device hw code: 0x326
[2021-04-12 21:48:37.378726] Device hw sub code: 0x8a00
[2021-04-12 21:48:37.385301] Device hw version: 0xcb00
[2021-04-12 21:48:37.390372] Device sw version: 0x1
[2021-04-12 21:48:37.399088] Device secure boot: True
[2021-04-12 21:48:37.407177] Device serial link authorization: True
[2021-04-12 21:48:37.410721] Device download agent authorization: True

[2021-04-12 21:48:37.415766] Disabling watchdog timer
[2021-04-12 21:48:37.419354] Disabling protection
[2021-04-12 21:48:37.530897] Protection disabled

c:\d_drive\bypass_utility>

Such that the phone is DA auth disabled. Run SPFlash (suggested SP_Flash_Tool_v5.2052_Win) then setup download page for auth file, da, scatter file etc. Make sure to set preloader file correctly, otherwise cant continus flashing.

Done!

For newer vendor/treble support, a phone manufactor had done the MT6755 soc for treble. Below is the link for MTK-SPFlash:
http://leagooftp.com.my/S%20series/S9/P7M2FA.LGE.HB.O1.HJ.P5PA.0718.V3.04.zip

it does contain unstriped kernel, dtb, overlay, and vendor binary enough for porting.
https://github.com/99degree/android_kernel_m3note have a working-in-progress v3.18 kernel for m3 note that able to enter twrp.

