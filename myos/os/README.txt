1) Open cygwin folder and double click on Cygwin Batch File
2) Go to the folder where you save the file myos/os.
3) Copy all the below commands 

nasm -f elf32 kernel.asm -o kasm.o
i586-elf-gcc -m32 -c kernel.c -o kc.o -ffreestanding
i586-elf-gcc -m32 -c include/system.c -o obj/system.o -ffreestanding
i586-elf-gcc -m32 -c include/isr.c -o obj/isr.o -ffreestanding
i586-elf-gcc -m32 -c include/idt.c -o obj/idt.o -ffreestanding
i586-elf-gcc -m32 -c include/util.c -o obj/util.o -ffreestanding
i586-elf-gcc -m32 -c include/string.c -o obj/string.o -ffreestanding
i586-elf-gcc -m32 -c include/screen.c -o obj/screen.o -ffreestanding
i586-elf-gcc -m32 -c include/kb.c -o obj/kb.o -ffreestanding
i586-elf-ld -m elf_i386 -T link.ld -o usr/bin/boot/kernel.bin kasm.o kc.o obj/isr.o obj/system.o obj/string.o obj/screen.o obj/kb.o obj/idt.o obj/util.o
qemu-system-i386 -kernel usr/bin/boot/kernel.bin

4) Using qemu emulator as a Virtual box the kernel start.
