# initramfs compress

find -P . | grep -Ev ".git|README.md" |cpio -o -H newc|gzip > ./initramfs.cpio.gz

# replace kernel initramfs
cp ./initramfs.cpio KERNEL/SOURCES/
