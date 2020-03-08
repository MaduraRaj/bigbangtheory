Level 1
Making file executable
```
chmod +x sheldon1
```
Execute the file
```
./sheldon1
```
Open with gdb
```
gdb sheldon1
info function
disassemble main
<pahase_1>
disassemble phase_1
	Dump of assembler code for function phase_1:
	   0x08048b20 <+0>:	push   ebp
	   0x08048b21 <+1>:	mov    ebp,esp
	   0x08048b23 <+3>:	sub    esp,0x8
	   0x08048b26 <+6>:	mov    eax,DWORD PTR [ebp+0x8]
	   0x08048b29 <+9>:	add    esp,0xfffffff8
	   0x08048b2c <+12>:	push   0x80497c0
	   0x08048b31 <+17>:	push   eax
	   0x08048b32 <+18>:	call   0x8049030 <strings_not_equal>
	   0x08048b37 <+23>:	add    esp,0x10
	   0x08048b3a <+26>:	test   eax,eax
	   0x08048b3c <+28>:	je     0x8048b43 <phase_1+35>
	   0x08048b3e <+30>:	call   0x80494fc <explode_bomb>
	   0x08048b43 <+35>:	mov    esp,ebp
	   0x08048b45 <+37>:	pop    ebp
	   0x08048b46 <+38>:	ret    
	End of assembler dump.

	(gdb) x/s 0x80497c0

	0x80497c0:	"Public speaking is very easy."
	(gdb) run
	Starting program: /root/Desktop/OHTSF/Lec/sheldon1 
	Welcome to my fiendish little bomb. You have 6 phases with
	which to blow yourself up. Have a nice day!
	Public speaking is very easy.
```
Level 2
```
Disassembling Phase_2
```
(gdb) disassemble phase_2
Dump of assembler code for function phase_2:
   0x08048b48 <+0>:	push   ebp
   0x08048b49 <+1>:	mov    ebp,esp
   0x08048b4b <+3>:	sub    esp,0x20
   0x08048b4e <+6>:	push   esi
   0x08048b4f <+7>:	push   ebx
   0x08048b50 <+8>:	mov    edx,DWORD PTR [ebp+0x8]
   0x08048b53 <+11>:	add    esp,0xfffffff8
   0x08048b56 <+14>:	lea    eax,[ebp-0x18]
   0x08048b59 <+17>:	push   eax
   0x08048b5a <+18>:	push   edx
   0x08048b5b <+19>:	call   0x8048fd8 <read_six_numbers>
   0x08048b60 <+24>:	add    esp,0x10
   0x08048b63 <+27>:	cmp    DWORD PTR [ebp-0x18],0x1 //comparing
   0x08048b67 <+31>:	je     0x8048b6e <phase_2+38>
   0x08048b69 <+33>:	call   0x80494fc <explode_bomb>
   0x08048b6e <+38>:	mov    ebx,0x1
   0x08048b73 <+43>:	lea    esi,[ebp-0x18]
   0x08048b76 <+46>:	lea    eax,[ebx+0x1]
   0x08048b79 <+49>:	imul   eax,DWORD PTR [esi+ebx*4-0x4]
   0x08048b7e <+54>:	cmp    DWORD PTR [esi+ebx*4],eax  //comparing
   0x08048b81 <+57>:	je     0x8048b88 <phase_2+64>
   0x08048b83 <+59>:	call   0x80494fc <explode_bomb>
   0x08048b88 <+64>:	inc    ebx
   0x08048b89 <+65>:	cmp    ebx,0x5  //comparing
   0x08048b8c <+68>:	jle    0x8048b76 <phase_2+46>
   0x08048b8e <+70>:	lea    esp,[ebp-0x28]
   0x08048b91 <+73>:	pop    ebx
   0x08048b92 <+74>:	pop    esi
   0x08048b93 <+75>:	mov    esp,ebp
   0x08048b95 <+77>:	pop    ebp
   0x08048b96 <+78>:	ret    
```   
dissassembling <read_six_numbers function
```
   (gdb) disassemble read_six_numbers 
   Dump of assembler code for function read_six_numbers:
      0x08048fd8 <+0>:	push   ebp
      0x08048fd9 <+1>:	mov    ebp,esp
      0x08048fdb <+3>:	sub    esp,0x8
      0x08048fde <+6>:	mov    ecx,DWORD PTR [ebp+0x8]
      0x08048fe1 <+9>:	mov    edx,DWORD PTR [ebp+0xc]
      0x08048fe4 <+12>:	lea    eax,[edx+0x14]
      0x08048fe7 <+15>:	push   eax
      0x08048fe8 <+16>:	lea    eax,[edx+0x10]
      0x08048feb <+19>:	push   eax
      0x08048fec <+20>:	lea    eax,[edx+0xc]
      0x08048fef <+23>:	push   eax
      0x08048ff0 <+24>:	lea    eax,[edx+0x8]
      0x08048ff3 <+27>:	push   eax
      0x08048ff4 <+28>:	lea    eax,[edx+0x4]
      0x08048ff7 <+31>:	push   eax
      0x08048ff8 <+32>:	push   edx
      0x08048ff9 <+33>:	push   0x8049b1b
      0x08048ffe <+38>:	push   ecx
      0x08048fff <+39>:	call   0x8048860 <sscanf@plt>
      0x08049004 <+44>:	add    esp,0x20
      0x08049007 <+47>:	cmp    eax,0x5
      0x0804900a <+50>:	jg     0x8049011 <read_six_numbers+57>
      0x0804900c <+52>:	call   0x80494fc <explode_bomb>
      0x08049011 <+57>:	mov    esp,ebp
      0x08049013 <+59>:	pop    ebp
      0x08049014 <+60>:	ret    
   End of assembler dump.
```
Getting the type of values that we have to inset
```
(gdb) x/s 0x8049b1b
0x8049b1b:	"%d %d %d %d %d %d"
(gdb) 


