<a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.herokuapp.com?font=Pixelify+Sans&size=25&pause=1000&color=0CF730&center=true&random=false&width=435&lines=Official+writeup+of+baseUNOswitch" alt="Typing SVG" /></a>

In the baseUNOswitch challenge we get two files a txt file named cipher.txt which contains the cipher and a JPG file name [baseUNO_hint.jpg](https://github.com/ACE-UCHIHA/FlagFest2024/blob/main/writeup/BaseUNOswitch/images/baseUNO_hint.jpg)

![abseUNOswitch hint](https://github.com/ACE-UCHIHA/FlagFest2024/blob/main/writeup/BaseUNOswitch/images/baseUNO_hint.jpg "This was the provided hint")

The cipher.txt file gives us the cipher which looks file this:  
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



okey now let's leave other base encodings because we don't wanna waste time and see base85 now

1. It takes every single letter of the word.
2. Then it converts it into binary (8-bit)
3. Then the binary is regrouped with every binary having length of 32-bit/4-byte.
4. Then the binary is converted into decimal.
5. Then the decimal is converted into another character according to base85 index/conversion  table.



Okey so did you see the meaning of the hint that was in the JPG ?

yes! it means in the 4th step of the base32 or base85 the bit size was changed or switched.

Like the binary in the base32 was regrouped with every binary having length of 32-bit/4-byte.

Okey so what happended because of the bit change?

The encoding is still base32 but with a condition that all the characters will be according to base85.

If we see base85 index/conversion  table it uses ```!-u``` while base32 uses ```A-Z2-7=``` 

So we in order to decode this cipher we have to use ```!-u``` with base32 or use ```A-Z2-7=``` with base85

Using ```!-u``` with **_from base32_** in **_cyberchef_** will decode the cipher and give you the flag.

![decoding proof](https://github.com/ACE-UCHIHA/FlagFest2024/blob/main/writeup/BaseUNOswitch/images/baseUNOswitch_prove.png "basUNOswitch decoding proof from cyberchef")
