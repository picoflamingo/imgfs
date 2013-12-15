imgfs
=====

imgfs. Simple FUSE filesystem to automatically rename file names

imgfs is a simple hack of the excellent Big Brother File System form 
Joseph J. Pfeiffer, Jr., Ph.D. that you can find here:

http://www.cs.nmsu.edu/~pfeiffer/fuse-tutorial/

For the time being, imgfs is a simple modification of the truncate syscall so, whenever a file is being truncated to 0 bytes, a copy of it (tagged with current UNIX time) is made before the file is actually truncated.

This way, you will never overwrite a file by mistake.

Hopefully in the future this will be extended with additional, image specific functions. 

I'm basically using this with firefox so it might not work with other tools. Check before you use it or you might lost some data.

USAGE
=====
Just create a mount point (secure_dir) for you existing directory and execute:

imgfs ./original_dir ./secure_dir

From this point on, all the contents of original_dir will appear in secure_dir and when a file is overwritten on secure_dir a backup copy of the existing file will be automatically created.

COMPILATION
===========
By default the logging capability of bbfs is disabled in imgfs. To enable it (useful for debugging), just uncomment the IMG_CFLAGS variable in the Makefile

For detailed instruction on how to build and all the information about the insights of bbfs (and therefore imgfs), please refer to the original and great tutorial in the link below:

http://www.cs.nmsu.edu/~pfeiffer/fuse-tutorial/