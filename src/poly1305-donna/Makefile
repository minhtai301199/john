
CC = gcc
CXX = @CXX@
AS = gcc
LD = gcc
CPP = gcc
CPPFLAGS =  -I/usr/local/include -DCL_SILENCE_DEPRECATION
CFLAGS = -m64 -g -O2 -I/usr/local/include -DARCH_LITTLE_ENDIAN=1 -DPREFER_FLOCK -Wall -fno-omit-frame-pointer --param allow-store-data-races=0 -Wno-deprecated-declarations -Wformat-extra-args -Wunused-but-set-variable -std=gnu89 -Wdate-time -D_POSIX_SOURCE -D_GNU_SOURCE -D_XOPEN_SOURCE=600 -Wno-unused-function
ASFLAGS = -m64  -DARCH_LITTLE_ENDIAN=1 -c 
LDFLAGS = -m64  -L/usr/local/lib -L/lib64
AR = ar
FIND = /usr/bin/find
RM = /bin/rm -f

IN = poly1305-donna.o

all: poly1305-donna.a
default: poly1305-donna.a

poly1305-donna.o: poly1305-donna.c
	$(CC) -DHAVE_CONFIG_H $(CFLAGS) $(CPPFLAGS) -c poly1305-donna.c -o poly1305-donna.o

.PHONY: subdirs $(SUBDIRS)

subdirs: $(SUBDIRS)

$(SUBDIRS):
	$(MAKE) -C $@ all

poly1305-donna.a: $(SUBDIRS) poly1305-donna.o
	$(AR) -rs $@ $(IN)

clean:
	$(FIND) . -name \*.a -exec $(RM) {} \;
	$(FIND) . -name \*.o -exec $(RM) {} \;

distclean: clean
	$(RM) Makefile
