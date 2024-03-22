BUILD_DIR?=build/
ASM?=nasm
ASMFLAGS?=-f obj
CC16?=/usr/bin/watcom/binl64/wcc
CFLAGS16?=-4 -d3 -s -wx -ms -zl -zq
LD16?=/usr/bin/watcom/binl64/wlink

SOUCES_C=$(wildcard *.c)
SOUCES_ASM=$(wildcard *.asm)
OBJECTS_C=$(patsubst %.c, $(BUILD_DIR)/c/stage2/%.obj, $(SOUCES_C))
OBJECTS_ASM=$(patsubst %.asm, $(BUILD_DIR)/asm/stage2/%.obj, $(SOUCES_C))

.PHONY: all clean stage2

all: stage2

stage2: $(BUILD_DIR)/stage2.bin

$(BUILD_DIR)/stage2.bin: $(OBJECTS_ASM) $(OBJECTS_C)
	$(LD16) NAME $(BUILD_DIR)/stage2.bin FILE \{ $(OBJECTS_ASM) $(OBJECTS_C) \} OPTION MAP =$(BUILD_DIR)/stage2.map @linker.lnk

$(BUILD_DIR)/asm/stage2/%.obj: %.c always
	$(CC16) $(CFLAGS16) -fo=$@ $<

$(BUILD_DIR)/asm/stage2/%.obj: %.asm always
	$(ASM) $(ASMFLAGS) -o $@ $<

clean:
	rm -f $(BUILD_DIR)/stage2.bin