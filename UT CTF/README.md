# UT CTF
link: [UT CTF](https://utctf.live/challenges)

# BEGINNER
## Sanity Check
Solution:

Ada di discord UTCTF 2021 bagian announcement. Flag: `utflag{welcome_to_utctf}`

## Run-ELF
Solution:

Diberikan file `run` untuk dijalankan.
```
chmod +x run
./run
```
flag: `utflag{run_run_binary_9312854}`

## Stringy Things
Solution:

Diberikan file `calc`, diminta mencari string.
```
strings calc | grep utflag
```
flag: `utflag{strings_is_op}`

## HTML
Solution:

Mencari flag di website. Saya coba melihat source codenya dan menemukan flagnya. flag: `utflag{you_found_me_0123959}`

## Magic Bytes
Solution:

Saat dibaca bytes nya, ternyata itu merupakan file PNG. Diubah extensionnya jadi PNG dan dibuka.

flag: `utflag{file_extensions_mean_nothing}`

## Sizzling Bacon
Diberikan string `sSsSSsSSssSSsSsSsSssSSSSSSSssS{SSSsSsSSSsSsSSSsSSsSSssssssSSSSSSSsSSSSSSSSsSSsssSSssSsSSSsSSsSSSSssssSSsssSSsSSsSSSs}`

Solution:

String yang diberikan dienkripsi dengan baconian cipher. Dengan `s=1` dan `S=0`, lalu didekripsi
```python
s = "sSsSSsSSssSSsSsSsSssSSSSSSSssS{SSSsSsSSSsSsSSSsSSsSSssssssSSSSSSSsSSSSSSSSsSSsssSSssSsSSSsSSsSSSSssssSSsssSSsSSsSSSs}"
s = s.replace("s", "1")
s = s.replace("S", "0")
s = s[:-1].split("{")
for b in s:
     print("".join(l[int(b[i:i+5], 2)] for i in range(0, len(b), 5)))
    
# output
# utflag
# crispybaconcipher
```
flag: `utflag{crispybaconcipher}`

## Cipher Gauntlet
Diberikan file berisi angka 0 dan 1 yang dienkripsi dengan beberapa enkripsi berbeda.

Solution:

```python
with open("secret.txt", "r") as f:
  data = f.read().split()

# ASCII
print("".join(map(lambda x: chr(int(x,2)), data)))

# output
# Uh-oh, looks like we have another block of text, with some sort of special encoding. Can you figure out what this encoding is? (hint: if you look carefully, you'll notice that there only characters present are A-Z, a-z, 0-9, and sometimes / and +. See if you can find an encoding that looks like this one.)\nTmV3IGNoYWxsZW5nZSEgQ2FuIHlvdSBmaWd1cmUgb3V0IHdoYXQncyBnb2luZyBvbiBoZXJlPyBJdCBsb29rcyBsaWtlIHRoZSBsZXR0ZXJzIGFyZSBzaGlmdGVkIGJ5IHNvbWUgY29uc3RhbnQuIChoaW50OiB5b3UgbWlnaHQgd2FudCB0byBzdGFydCBsb29raW5nIHVwIFJvbWFuIHBlb3BsZSkuCm15eHFia2Rldmtkc3l4YyEgaXllIHJrZm8gcHN4c2Nyb24gZHJvIGxvcXN4eG9iIG1iaXpkeXFia3pyaSBtcmt2dm94cW8uIHJvYm8gc2MgayBwdmtxIHB5YiBrdnYgaXllYiBya2JuIG9wcHliZGM6IGVkcHZrcXt4eWdfaXllYm9fenZraXN4cV9nc2RyX21iaXpkeX0uIGl5ZSBnc3Z2IHBzeG4gZHJrZCBrIHZ5ZCB5cCBtYml6ZHlxYmt6cmkgc2MgbGVzdm5zeHEgeXBwIGRyc2MgY3liZCB5cCBsa2NzbSB1eHlndm9ucW8sIGt4biBzZCBib2t2dmkgc2MgeHlkIGN5IGxrbiBrcGRvYiBrdnYuIHJ5em8gaXllIG94dHlpb24gZHJvIG1ya3Z2b3hxbyE=

# BASE64
import base64
print(base64.b64decode("TmV3IGNoYWxsZW5nZSEgQ2FuIHlvdSBmaWd1cmUgb3V0IHdoYXQncyBnb2luZyBvbiBoZXJlPyBJdCBsb29rcyBsaWtlIHRoZSBsZXR0ZXJzIGFyZSBzaGlmdGVkIGJ5IHNvbWUgY29uc3RhbnQuIChoaW50OiB5b3UgbWlnaHQgd2FudCB0byBzdGFydCBsb29raW5nIHVwIFJvbWFuIHBlb3BsZSkuCm15eHFia2Rldmtkc3l4YyEgaXllIHJrZm8gcHN4c2Nyb24gZHJvIGxvcXN4eG9iIG1iaXpkeXFia3pyaSBtcmt2dm94cW8uIHJvYm8gc2MgayBwdmtxIHB5YiBrdnYgaXllYiBya2JuIG9wcHliZGM6IGVkcHZrcXt4eWdfaXllYm9fenZraXN4cV9nc2RyX21iaXpkeX0uIGl5ZSBnc3Z2IHBzeG4gZHJrZCBrIHZ5ZCB5cCBtYml6ZHlxYmt6cmkgc2MgbGVzdm5zeHEgeXBwIGRyc2MgY3liZCB5cCBsa2NzbSB1eHlndm9ucW8sIGt4biBzZCBib2t2dmkgc2MgeHlkIGN5IGxrbiBrcGRvYiBrdnYuIHJ5em8gaXllIG94dHlpb24gZHJvIG1ya3Z2b3hxbyE="))

# output
# New challenge! Can you figure out what's going on here? It looks like the letters are shifted by some constant. (hint: you might want to start looking up Roman people).\nmyxqbkdevkdsyxc! iye rkfo psxscron dro loqsxxob mbizdyqbkzri mrkvvoxqo. robo sc k pvkq pyb kvv iyeb rkbn oppybdc: edpvkq{xyg_iyebo_zvkisxq_gsdr_mbizdy}. iye gsvv psxn drkd k vyd yp mbizdyqbkzri sc lesvnsxq ypp drsc cybd yp lkcsm uxygvonqo, kxn sd bokvvi sc xyd cy lkn kpdob kvv. ryzo iye oxtyion dro mrkvvoxqo!

# CAESAR
from string import ascii_lowercase as l
for i in range(26):
  print("New challenge! Can you figure out what's going on here? It looks like the letters are shifted by some constant. (hint: you might want to start looking up Roman people).\nmyxqbkdevkdsyxc! iye rkfo psxscron dro loqsxxob mbizdyqbkzri mrkvvoxqo. robo sc k pvkq pyb kvv iyeb rkbn oppybdc: edpvkq{xyg_iyebo_zvkisxq_gsdr_mbizdy}. iye gsvv psxn drkd k vyd yp mbizdyqbkzri sc lesvnsxq ypp drsc cybd yp lkcsm uxygvonqo, kxn sd bokvvi sc xyd cy lkn kpdob kvv. ryzo iye oxtyion dro mrkvvoxqo!".translate(str.maketrans(l[i:]+l[:i], l)))
  
# output
# ...
# congratulations! you have finished the beginner cryptography challenge. here is a flag for all your hard efforts: utflag{now_youre_playing_with_crypto}. you will find that a lot of cryptography is building off this sort of basic knowledge, and it really is not so bad after all. hope you enjoyed the challenge!
# ...
```

flag: `utflag{now_youre_playing_with_crypto}`

## Half-time Survey
Solution:

Isi form dan `utflag{thank_you_278672}`

# WEB
## Source it!
Diberikan [website](http://web1.utctf.live:8778)

Solution:

Saya mencoba melihat source code untuk mencoba mencari cara validasi formnya. Pada head, saya menemukan script yang memvalidasi `username = admin` dan `password = 1bea3a3d4bc3be1149a75b33fb8d82bc`. Password dienkripsi menggunakan MD5.

```
sudo hashcat -a 0 -m 0 $(echo 1bea3a3d4bc3be1149a75b33fb8d82bc) /usr/share/wordlists/rockyou.txt
```

flag: `utflag{b33n_th3r3_s0uRc3d_th4t}`

# CRYPTO
## Small P Problems
```
My buddies Whitfield and Martin were trying to share a secret key between themselves, and I was able to eavesdrop on their conversation. I bet I could probably figure out their shared secret with a little math...

p = 69691
g = 1001

A = 17016
B = 47643
Note: submit either the shared secret or the shared secret wrapped in utflag{}

by balex
```
Solution:

Whitfield **Diffie** and Martin **Hellman**. Pertukaran kunci menggunakan algoritma Diffie-Hellman. Diketahui p, g, A, B, dan melihat ukuran p yang cukup kecil, dapat dengan mudah dicari nilai a dan b, lalu menghitung secret
```python
p = 69691
g = 1001
A = 17016
B = 47643

a = 1
while True:
  if pow(g,a,p) == A:
    print(a)
    break
  a += 1

b = 1
while True:
  if pow(g,b,p) == B:
    print(b)
    break
  b += 1
  
print(pow(A,b,p))

# Output
# a = 12552
# b = 7919
# s = 53919
 
```
flag: `utflag{53919}`
