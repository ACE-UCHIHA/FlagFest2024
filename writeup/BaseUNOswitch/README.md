In the baseUNOswitch challenge we get two files and txt file named cipher.txt which contains the cipher and a JPG file name [baseUNO_hint.jpg]()

![Alt Text](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Markdown-mark.svg/1200px-Markdown-mark.svg.png "Hover Info")

In the cipher.txt file gives us the cipher which looks file this:  
```
-:7'#:<'-6:8)?<8.!;()8:2.:08);"4,>2'#=:4+68$!>24/*:4'8:;&>?1AAAA
```

okey now let's focus on the given hints.

In the challenge description it says " ***Do you know how all base encodings works?*** "
and the JPG was hinting to switch or replace 5 with 32 or switch or replace 32 with 5.


hmmm... then let's see how base encodings works.

First let's see base32 shall we?

1.  It takes every single letter of the word.
2. Then it converts it into binary (8-bit)
3. Then the binary is regrouped with every binary having length of 5 bits.
4. Then the binary is converted into decimal.
5. Then the decimal is converted into another character according to base32 index/conversion  table.



okey I now let's leave other base encodings for a while and see base85 now

1. t takes every single letter of the word.
2. Then it converts it into binary (8-bit)
3. Then the binary is regrouped with every binary having length of 32-bit/4-byte.
4. Then the binary is converted into decimal.
5. Then the decimal is converted into another character according to base85 index/conversion  table.



Okey so did you see meaning of the hint that was in the JPG ?

yes! It it means in the 4th step of the base32 or base85 we the bit size was changed or switched.

Like the binary in the base32 was regrouped with every binary having length of 32-bit/4-byte.

Okey so what happended because of the bit change?

The encoding is still base32 but with a condition that all the characters will be according to base85.

If we see base85 index/conversion  table it uses **_!-u_** while base32 uses **_A-Z2-7=_** 

So we in order to decode this cipher we have to use **_!-u_** with base32 or use **_A-Z2-7=_** with base85

Using **_!-u_** with **_from base32_** in **_cyberchef_** with decode the cipher and give the you the flag.

![Alt Text](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Markdown-mark.svg/1200px-Markdown-mark.svg.png "Hover Info")