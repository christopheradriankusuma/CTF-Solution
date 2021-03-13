# UT CTF
link: [UT CTF](https://utctf.live/challenges)

## CRYPTO
# Small P Problems
```
My buddies Whitfield and Martin were trying to share a secret key between themselves, and I was able to eavesdrop on their conversation. I bet I could probably figure out their shared secret with a little math...

p = 69691
g = 1001

A = 17016
B = 47643
Note: submit either the shared secret or the shared secret wrapped in utflag{}

by balex
```
POC:

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
flag: utctf{53919}

# BEGINNER
## Magic Bytes
[file](https://utctf.live/files/3054ebb30380d6306f5c0dcd865fba03/out.txt?token=eyJ1c2VyX2lkIjo1MDQsInRlYW1faWQiOjE2NiwiZmlsZV9pZCI6NDB9.YEw6zA.rkXzBKFVt9kHmTzI0pk5rJ5YOBI)

POC:

Saat dibaca bytes nya, ternyata itu merupakan file PNG. Diubah extensionnya jadi PNG dan dibuka.

flag: utflag{file_extensions_mean_nothing}
