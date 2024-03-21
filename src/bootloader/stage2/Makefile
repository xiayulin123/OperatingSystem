BUILD_DIR?=build/
ASM?=nasm
CC16?=/usr/bin/watcom/binl64/wcc
LD16?=/usr/bin/watcom/binl64/wlink

SOUCES_C=$(wildcard *.c)
SOUCES_ASM=$(wildcard *.asm)
OBJECTS_C=$(patsubst %.c, $(BUILD_DIR)/stage2/%.obj, $(SOUCES_C))
OBJECTS_ASM=$(patsubst %.asm, $(BUILD_DIR)/stage2/%.obj, $(SOUCES_C))

.PHONY: all clean stage2

all: stage2

stage2: $(BUILD_DIR)/stage2.bin

$(BUILD_DIR)/stage2.bin:
	$(ASM) main.asm -f bin -o $(BUILD_DIR)/stage2.bin

clean:
	rm -f $(BUILD_DIR)/stage2.bin