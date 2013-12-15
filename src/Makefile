#IMGFS_CFLAGS=-DLOG

imgfs : bbfs.o log.o
	gcc -g -o imgfs bbfs.o log.o `pkg-config fuse --libs`

bbfs.o : bbfs.c log.h params.h
	gcc -g -Wall `pkg-config fuse --cflags` -c bbfs.c ${IMGFS_CFLAGS}

log.o : log.c log.h params.h
	gcc -g -Wall `pkg-config fuse --cflags` -c log.c ${IMGFS_CFLAGS}

clean:
	rm -f imgfs *.o

dist:
	rm -rf imgfs/
	mkdir imgfs/
	cp ../*.html imgfs/
	mkdir imgfs/example/
	mkdir imgfs/example/mountdir/
	mkdir imgfs/example/rootdir/
	echo "a bogus file" > imgfs/example/rootdir/bogus.txt
	mkdir imgfs/src
	cp Makefile COPYING COPYING.LIB *.c *.h imgfs/src/
	tar cvzf ../../imgfs.tgz imgfs/
	rm -rf imgfs/
