# Makefile for RISC-V cross-compilation

# Compiler options
CC_X86 := gcc
CC_RISCV := riscv64-buildroot-linux-gnu-gcc
CFLAGS := -Wall -Wextra
LIB := -lssl -lcrypto
# Source files
SRCS := elf_sign.c

# Object files
OBJS := $(SRCS:.c=.o)

# Target executable
TARGET := elf_sign

# Default target
all: $(TARGET)

# Build for x86
x86: CC := $(CC_X86)
x86: $(TARGET)

# Build for RISC-V
riscv: CC := $(CC_RISCV)
riscv: $(TARGET)

# Rule to build object files
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@ $(LIB)

# Rule to build the target executable
$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) $^ -o $@ $(LIB)

# Clean rule
clean:
	rm -f $(OBJS) $(TARGET)

