# step1: init filesystem
mkdir -p {dev,proc,run,sysroot,sys}

# step2: initramfs compress

find -P . | grep -Ev ".git|README.md" |cpio -o -H newc|gzip > ./initramfs.cpio.gz

# step3: replace kernel initramfs
cp ./initramfs.cpio KERNEL/SOURCES/
