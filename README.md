# step1: initramfs compress

find -P . | grep -Ev ".git|README.md" |cpio -o -H newc|gzip > ./initramfs.cpio.gz

# step2: replace kernel initramfs
cp ./initramfs.cpio KERNEL/SOURCES/

# how to debug initramfs

# using qemu-kvm -kernel bzImage -initrd initramfs.cpio.gz, also we can
# wrap strace binary to trace to error info.
