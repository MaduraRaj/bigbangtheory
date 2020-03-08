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
