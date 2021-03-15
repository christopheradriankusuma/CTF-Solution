# NahamCon CTF
link: [NahamCon CTF](https://ctf.nahamcon.com/challenges)

# WARMUPS
## Read The Rules
Please follow the rules for this CTF!

Connect here:
[Read The Rules](https://ctf.nahamcon.com/rules)

POC:

Inspect element.

flag: `flag{90bc54705794a62015369fd8e86e557b}`

## Car Keys
We found this note on someone's key chain! It reads... ygqa{6y980e0101e8qq361977eqe06508q3rt}? There was another key that was engraved with the word QWERTY, too...

POC:

Tampak seperti Caesar Cipher tapi memiliki kunci. 

flag: `flag{6f980c0101c8aa361977cac06508a3de}`

## Pollex
Some people seem to have trouble reading this, understandably so. Sorry. The flag ends in these characters: 8fe36bc00}<br>
Attachments: [pollex](https://ctf.nahamcon.com/files/47768d1e408e27e0a2a6afd01ed2e489/pollex?token=eyJ1c2VyX2lkIjoyNzg2LCJ0ZWFtX2lkIjpudWxsLCJmaWxlX2lkIjoxOX0.YE9XBg.RiLErua2n0vxAxUwGhmz_O8Fkt4)

POC:

Saat dilihat filenya, ternyata itu file gambar. Saat dibuka, hanya ada gambar tangan dengan background hitam. Tetapi saat dilihat thumbnailnya (di folder), ada tulisan putih di bagian bawah gambar yang tidak muncul saat gambar dibuka.

flag: `flag{65c34a1ec121a286600ddd48fe36bc00}`

## Shoelaces
Do you double-knot your shoelaces? You gotta keep'em tied!<br>
Attachments: [shoelaces.jpg](https://ctf.nahamcon.com/files/b8fdce4df8ac178c21e5867a18f19ec0/shoelaces.jpg?token=eyJ1c2VyX2lkIjoyNzg2LCJ0ZWFtX2lkIjpudWxsLCJmaWxlX2lkIjoyNX0.YE9YMg.YowY8bnjOAbPadg1oEu9Vq5CrZA)

POC:

Percobaan pertama dan berhasil `strings shoelaces.jpg | grep flag`

flag: `flag{137288e960a3ae9b148e8a7db16a69b0}`

## esab64
Was it a car or a cat I saw?<br>
Attachments: [esab64](https://ctf.nahamcon.com/files/9e1ff93915a5e07e8de9e79eb808c597/esab64?token=eyJ1c2VyX2lkIjoyNzg2LCJ0ZWFtX2lkIjpudWxsLCJmaWxlX2lkIjoxMn0.YE9YMg.7Cyh_A6W2Cm6hALGqOb161vQskI)

POC:

Dilihat dari nama challengenya mirip base64 tapi terbalik dan deskripsinya juga bisa dibaca terbalik, sepertinya teks pada file juga terbalik dan dienkripsi dengan base64. Saat didekripsi, hasilnya juga terbalik

```python
import base64
print(base64.b64decode("mxWYntnZiVjMxEjY0kDOhZWZ4cjYxIGZwQmY2ATMxEzNlFjNl13X"[::-1])[::-1].decode())

# output
# flag{fb5211b498afe87b1bd0db601117e16e}_
```
Abaikan _ di akhir
flag: `flag{fb5211b498afe87b1bd0db601117e16e}`

## Eighth Circle
Abandon all hope, ye who enter here...<br>
Attachments: [eighth_circle](https://ctf.nahamcon.com/files/6e0912abf579ae0172a3e662e5f3916d/eighth_circle?token=eyJ1c2VyX2lkIjoyNzg2LCJ0ZWFtX2lkIjpudWxsLCJmaWxlX2lkIjoxMH0.YE9aig.w3iqGWxvy-WVWg5VYuUVMxTzmCg)

POC:

Saat searching google, saya menemukan bahwa eighth circle memiliki nama `Malbolge` yang juga kebetulan nama salah satu bahasa pemrograman. Saya menggunakan [Malbolge - interpreter online](http://malbolge.doleczek.pl/)

flag: `flag{bf201f669b8c4adf8b91f09165ec8c5c}`

# FORENSIC
## Parseltongue
Hisssss, can you ssssee ssssome sssssecretssss? [file](https://ctf.nahamcon.com/files/966d964ed630170b0b54557122e439e6/parseltongue?token=eyJ1c2VyX2lkIjoyNzg2LCJ0ZWFtX2lkIjpudWxsLCJmaWxlX2lkIjoxOH0.YE2jvg.h-uhopm3teLIeCh-usLZU0q9OSc)

POC:

Diberikan suatu file. Saat saya mencoba menjalankan `strings parseltongue`, saya menemukan banyak kata yang biasa saya temukan dalam file python. Saya menduga itu merupakan file python yang telah dicompile ke .pyc.
```
mv parseltongue parseltongue.pyc
pip install uncompyle6
uncompyle6 -o . parseltongue.pyc
```
Akan muncul file baru bernama `parseltongue.py`, saya print semua variabel yang ada dan ditemukan flagnya pada variabel `zzz`

flag: `flag{eabd9a04bdd1ea626f2cfbb0ea5c5feb}`

# MISCELLANOUS
## Alphabet Soup
A, B, C, and V, G, L, Y... wait a second, that's not how the song goes! [alphabet_soup.cs](https://ctf.nahamcon.com/files/b01bb6aff74442a46dc846b94e517264/alphabet_soup.cs?token=eyJ1c2VyX2lkIjoyNzg2LCJ0ZWFtX2lkIjpudWxsLCJmaWxlX2lkIjoyfQ.YE2k6Q._HxKsfShmSkppeJ2KBwjJU2DZlc)

POC:

Diberikan file C#. Karena saya tidak bisa menjalankannya, saya ubah ke python. Dari satu-satunya fungsi yang ada dan 2 parameter yang disediakan, saya jalankan dan mendapat teks yang panjang, saya simpan dengan nama `alphabet`. Lalu `strings alphabet | grep flag`.

flag: `flag{b6cfb6656ea0ac92849a06ead582456c}`

# NAHAMCON
## HTB Village
Come join the party at the [HTB Village](https://discord.gg/Na9mxe7YGW), and track down a flag!<br>
POC:<br>
Deskripsi channel htb-village di discord<br>
flag: `flag{437f3e5ecdd39a29d695e2e31603f5b4}`

## INE Career Corner
Come join the party at the [INE Career Corner](https://discord.gg/eQ4jGmkCaf), and track down a flag!<br>
POC:<br>
Deskripsi channel ine-career-corner di discord<br>
flag: `flag{e713de181584836c9499811f13cb0e62}`

## IoT Village
Come join the party at the [IoT Village](https://discord.gg/pjzuF3zNtX), and track down a flag!<br>
POC:<br>
Deskripsi channel iot-village di discord<br>
flag: `flag{1ff473816ef21857cc62f838e8a33fc7}`

## Live Recon Village
Come join the party at the [Live Recon Village](https://discord.gg/fTPYrHK8HX), and track down a flag!<br>
POC:<br>
Deskripsi channel live-recon-village di discord<br>
flag: `flag{2795da9d0d2055d259a3fb4d6b78629c}`

## Red Team Village
Come join the party at the [Red Team Village](https://discord.gg/vaDYxKsknW), and track down a flag!<br>
POC:<br>
Deskripsi channel red-team-village di discord<br>
flag: `flag{fd59547d85953cac9dd5f378daed2157}`

## UHC-BR
Come join the party at the [UHC-BR](https://discord.gg/C6wvwE8RMX), and track down a flag!<br>
POC:<br>
Deskripsi channel uhc-br di discord<br>
flag: `flag{120c45c7b99d8cba1567441f5bef599e}`

## The Mission
Enter the flag you find on [The Mission](https://ctf.nahamcon.com/mission) page to open the gates and unlock challenges for The Mission. Please note, your participation in "The Mission" serves as permission for us to share your e-mail address with our sponsors, for potential career opportunities and private invitations to vulnerability disclosure and bug bounty programs.

After solving this challenge, you may need to refresh the page to see the newly unlocked challenges.<br>
POC:<br>
Melihat source code<br>
flag: `flag{48e117a1464c3202714dc9a350533a59}`

## #NahamCon2021
#NahamCon2021 #awesome #cool #winning! Did you know that the hashtag has another much cooler name, called the "octothorp?"

Perform some online reconnaissance to track down a flag for #NahamCon2021!<br>
POC:<br>
Searching google dengan query `"#NahamCon2021" "flag"`, muncul di hasil pencarian teratas dari twitter.
flag: `flag{e36bc5a67dd2fe5f33b62123f78fbcef}`

## Merch Store
Check out our [Merch Store](https://nahamcon.com/merch)! A portion of the proceeds go to support Women in CyberSecurity @WiCySorg!

Perform some online reconnaissance to track down a flag on the merch store!<br>
POC:<br>
Melihat source code<br>
flag: `flag{fafc10617631126361c693a2a3fce5a7}`
