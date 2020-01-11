#
# DREAM MIDI 1.0 media player
# (c)2003 reaper2k2 (c)2019 Ian micheal
#   

TARGET = DREAMMIDI.elf
OBJS =  main.o 





all: rm-elf $(TARGET)

include $(KOS_BASE)/Makefile.rules

KOS_CFLAGS += -ml -m4-single-only -pipe

clean:
	-rm -f $(TARGET) $(OBJS) romdisk.*

rm-elf:
	-rm -f $(TARGET) romdisk.*

$(TARGET): $(OBJS) romdisk.o
	$(KOS_CC) $(KOS_CFLAGS) $(KOS_LDFLAGS) -o $(TARGET) $(KOS_START) \
		$(OBJS) romdisk.o $(OBJEXTRA) -L$(KOS_BASE)/lib -lSDL -lSDL_ttf -lfreetype -lm -lSDL_image -lpng -ljpeg -lSDL_mixer -lSDL -loggvorbisplay -ltremor -lk++ -lz -lm -lkallisti -lc  $(KOS_LIBS)

romdisk.img:
	$(KOS_GENROMFS) -f romdisk.img -d romdisk -v

romdisk.o: romdisk.img
	$(KOS_BASE)/utils/bin2o/bin2o romdisk.img romdisk romdisk.o

run: $(TARGET)
	$(KOS_LOADER) $(TARGET)


