# NahamCon CTF
link: [NahamCon CTF](https://ctf.nahamcon.com/challenges)

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
