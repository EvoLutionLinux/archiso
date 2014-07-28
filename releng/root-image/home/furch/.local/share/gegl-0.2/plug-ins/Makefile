# This is a generic makefile for GEGL operations. Just add .c files,
# rename mentions of the filename and opname to the new name, and it should 
# compile. Operations in this dir should be loaded by GEGL by default
# If the operation being written depends on extra libraries, you'd better
# add a dedicated target with the extra bits linked in.


CFLAGS  += `pkg-config gegl --cflags`  -I. -fPIC
LDFLAGS += `pkg-config gegl --libs` -shared
SHREXT=.so
CFILES = $(wildcard ./*.c)
SOBJS  = $(subst ./,,$(CFILES:.c=$(SHREXT)))
all: $(SOBJS)
%$(SHREXT): %.c $(GEGLHEADERS)
	@echo $@; $(CC) $(CFLAGS) $(LDFLAGS) -o $@ $< $(LDADD)
clean:
	rm -f *$(SHREXT) $(OFILES)
