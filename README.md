# custom-partiton

sudo cryptsetup --key-size 512 luksFormat /dev/sda3
sudo cryptsetup luksOpen /dev/sda3 crypted


sudo pvcreate  /dev/mapper/crypted
sudo vgcreate vg /dev/mapper/crypted
sudo lvcreate -L 15G vg -n root
sudo lvcreate -L 8176M vg -n swap
sudo lvcreate -l 100%FREE vg -n home
