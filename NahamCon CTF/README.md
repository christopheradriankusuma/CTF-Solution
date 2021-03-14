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
