# uefi_ether

Device configuration files for uefi-Droid.
For some reason I can't reproduce UEFI_boot.img to boot on my device although this configuration will allow lk.img to boot with fastboot access and display working. Also note that the fstab.multiboot is most likely wrong.




You'll want to do this as well to make sure you don't get build errors:

cd uefi/lkl
git checkout a063e1631db5e2b9b04f184c5e6d185c1cd645cb


For finalizeing device you may notice it hangs because of ether needing -i 0x2c3f for it's fastboot commmands.. A work around for this is running 

sudo -s

source build/envsetup.sh

create_device /path/to/boot.img

lunch

make -j1 lk

finalize_device device/nextbit/ether
