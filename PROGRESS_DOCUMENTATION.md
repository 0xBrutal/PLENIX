# Day 1 – Setting Up the OS Development Environment

## Tools Installed

We configured three essential tools for OS development:

- **NASM (Netwide Assembler):** An assembler used to convert Assembly language code into machine code.
- **Make:** A build automation tool used to automate compilation and other build tasks.
- **QEMU:** A virtual machine emulator used to run and test our operating system without requiring physical hardware.

## Files Made
1. **src/main.asm** Our core logic
2. **Makefile** Our building script

## `main.asm`

### BIOS Boot Process

We learned about the legacy BIOS boot process:

- When a computer boots using legacy BIOS, the BIOS loads the boot sector into memory at address `0x7C00` (conventionally).
- The boot sector must be exactly **512 bytes**.
- The last two bytes must contain the boot signature `0xAA55`.

```asm
dw 0xAA55
```

Because x86 uses little-endian byte ordering, this value is stored in memory as:

```text
55 AA
```

The BIOS checks this signature to determine whether the boot sector is valid.

### Assembly Execution

Unlike high-level languages such as Java or C++, basic Assembly code does not have a predefined `main()` function.

The CPU executes instructions sequentially, starting from the designated execution address.

### CPU Instructions

- **HLT (Halt):** Stops the CPU from executing further instructions until an interrupt or other applicable event occurs.

Example:

```asm
hlt
```

## `Makefile`

We learned the basic syntax of a Makefile:

```makefile
target: prerequisites
	command
```

- **Target:** The file or task we want to build.
- **Prerequisites:** Dependencies required by the target.
- **Command:** The command executed to produce the target.

## `Compiler`

Basic NASM command:

```bash
nasm main.asm -f bin -o main.bin
```

Explanation:

- `main.asm`: Input Assembly source file.
- `-f bin`: Generates a raw binary file without an object-file format.
- `-o main.bin`: Specifies the output filename.

## `Virtual`

We used QEMU to emulate a computer with a floppy disk image:

```bash
qemu-system-i386 -fda main.bin
```

- `qemu-system-i386`: Starts an emulated 32-bit x86 machine.
- `-fda`: Attaches the specified file as a floppy disk image.

## `Summary`

By the end of Day 1, we:

- Installed NASM, Make, and QEMU.
- Learned the basics of the legacy BIOS boot process.
- Understood the significance of memory address `0x7C00`.
- Learned about the `0xAA55` boot signature.
- Understood sequential Assembly execution and the `HLT` instruction.
- Learned basic Makefile syntax.
- Compiled Assembly code into a raw binary.
- Ran our initial OS image using QEMU.



# Day 2 – Printing Hello World