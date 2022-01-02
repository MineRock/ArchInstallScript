Hello. This is a note-taking file for MineRocker's arch installer.

$ How to know if CPU is AMD or Intel? Why would you even want to do that?
> To install the microcode updates automatically, you need to know if the cpu is Intel or AMD. Here's how you do it.
cat /proc/cpuinfo | grep -m 1 vendor_id | awk '{print $3}'
This gives you either GenuineIntel or AuthenticAMD based on what CPU you have. Use this in an if and then install the microcode update accordingly.

$ How to know if system is BIOS or UEFI? Why would you even want to do that?
> When installing grub, there's different "target"s for type of system. UEFI has x86_64-efi. BIOS has i386-pc. Here's how you do it. 
// This command is on the Installation Guide for Arch Wiki.
-d "/sys/firmware/efi/efivars"
This tells you whether the efivars directory exists on the system. If it's UEFI, the folder will exist. If it's BIOS, folder will not exist. Use this in an if and then change GRUB target accordingly.

$ How to uncomment the locale in locale.gen?
> Since this is a personal script, I will be using en_US. You can change the code to your locale by checking it in /etc/locale.gen.
sed -i '/en_US.UTF-8 UTF-8/s/^#//g' locale.gen
This will uncomment the line.
