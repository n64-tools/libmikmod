CFLAGS = -std=gnu99 -O2 -G0 -Wall -mtune=vr4300 -march=vr4300 -I$(N64_INST)/include -I$(N64_INST)/mips64-elf/include -I$(CURDIR)/../include/ -I$(CURDIR)/ 
CFLAGS += -DDRV_N64

ASFLAGS = -mtune=vr4300 -march=vr4300
N64PREFIX = $(N64_INST)/bin/mips64-elf-
INSTALLDIR = $(N64_INST)
CC = $(N64PREFIX)gcc
AS = $(N64PREFIX)as
LD = $(N64PREFIX)ld
AR = $(N64PREFIX)ar

all: createdir libmikmod.a

include files.in

libmikmod.a: $(OFILES)
	$(AR) -rcs -o libmikmod.a $(OFILES)

createdir:
	@mkdir -p $(CURDIR)/build/

install: libmikmod.a $(CURDIR)/../include/mikmod.h
	install -m 0644 libmikmod.a $(INSTALLDIR)/lib/libmikmod.a
	install -m 0644 $(CURDIR)/../include/mikmod.h $(INSTALLDIR)/include/mikmod.h

.PHONY: clean
clean:
	rm -f *.o *.a
	rm -f $(CURDIR)/build/*
