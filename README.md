## Linux komutlar
```
sudo passwd root    # sifre degistirme
┌──(kali㉿kali)-[~]
└─$ setxkbmap tr    ## klavyeyi türkçe yaptık.
┌──(kali㉿kali)-[~]
└─$ sudo passwd kali    ## kali kullanıcısının parolasını değiştiren kod
┌──(kali㉿kali)-[~]
└─$ sudo dpkg-reconfigure locales   ## sistem dilini değiştiren komut. system restart gerekli.
┌──(kali㉿kali)-[~]
└─$ sudo dpkg-reconfigure keyboard-configuration    ## klavyeyi değiştirebileceğimiz komut.
```

### kali usb live mode persistence

[Source](https://www.kali.org/docs/usb/kali-linux-live-usb-persistence/)
```
sudo fdisk -l   ## komutu ile sisteme bağlı bulunan tüm aygıtlar listelenir. Persistence yapacağımız diski seçiyoruz.
sudo bash   ## bu komut ile root yetkisi kazanıyoruz
mkfs.ext3 -L persistence /dev/sdc2  ## bu komut ile persistence diskimizi ayarlıyoruz
e2label /dev/sdc2 persistence   ## bu komut ile persistence diskimizi belirtiyoruz
## oluşturulan kalıcı disk bölümünü sisteme bağlamak gerekli
mkdir -p /mnt/usb   ## diskin bağlanacağı dosya konumunu oluşturuyoruz
mount /dev/sdc2 /mnt/usb    ## disk bölümünü bağlamak için. /dev/sdc2=bağlanacak diskin bölümü    /mnt/usb=bağlanacak dikin konumu
echo "/union/" > /mnt/usb/persistence.conf
umount /dev/sdc2    ## sistemi yeniden başlat

```