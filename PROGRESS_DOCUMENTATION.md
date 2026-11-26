#DAY 1

we configured 3 things:
    1. nasm (a asm compiler)
    2. make (to automate bulding the result)
    3. qemu (a virtual machine)

main.asm =>
    we learned that a legacy based bios starts at "7C00" address, conventially
    and must end with "dw 0xAA55" which gives 55aa signature of our legace bios

    there is no entry point in asm it follows line by line

    * htl => a cpu halt instruction

make =>
    syntax:
        target: observe
            command
    
        nasm src -f bin -o dest

virtual =>
    qemu-system-i386 -fda src