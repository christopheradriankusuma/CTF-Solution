# Da Vinci CTF
link: [Da Vinci CTF](https://dvc.tf/)

# WEB
## Obfuscation

My password is my secret. You will never find it...

http://challs.dvc.tf:5555/

To validate this chall, please enter the secret code as the flag.

Solution:
Saat membuka web akan menampilkan form sederhana untuk meminta input. Lalu saya coba buka source code halaman, ada script seperti ini
```
var _0x562c=['179dYsldU','502577NKwytj','49301uPrsBV','%64%76%43%54%46%7b%31%74%5f%69%73%5f%6e%30%74%5f%34%5f%73%65%63%72%33%74%5f%34%6e%79%6d%30%72%33%7d','41567Xaicqe','getElementById','2IMuDQu','secret','result','111HrUPrb','238340OvJqoS','1XVHayx','innerHTML','OOO\x20NO\x20you\x20have\x20found\x20my\x20secret\x20!','353385nZcsex','value','1UUUnkm','110191GWccce'];var _0x5ae8=function(_0x34f242,_0x4f6807){_0x34f242=_0x34f242-0x175;var _0x562c5a=_0x562c[_0x34f242];return _0x562c5a;};(function(_0x10ab78,_0x2dad39){var _0x48e1e3=_0x5ae8;while(!![]){try{var _0x2dbbea=parseInt(_0x48e1e3(0x180))+-parseInt(_0x48e1e3(0x181))*parseInt(_0x48e1e3(0x178))+parseInt(_0x48e1e3(0x17d))*parseInt(_0x48e1e3(0x183))+-parseInt(_0x48e1e3(0x177))+parseInt(_0x48e1e3(0x17b))+-parseInt(_0x48e1e3(0x176))*parseInt(_0x48e1e3(0x17f))+-parseInt(_0x48e1e3(0x185))*parseInt(_0x48e1e3(0x17e));if(_0x2dbbea===_0x2dad39)break;else _0x10ab78['push'](_0x10ab78['shift']());}catch(_0x4df530){_0x10ab78['push'](_0x10ab78['shift']());}}}(_0x562c,0x5a3e5));function testSecret(){var _0x56a5a8=_0x5ae8,_0x3ee8ed=_0x56a5a8(0x182),_0x14130d=document[_0x56a5a8(0x184)](_0x56a5a8(0x186))[_0x56a5a8(0x17c)];_0x14130d==unescape(_0x3ee8ed)?document[_0x56a5a8(0x184)](_0x56a5a8(0x175))[_0x56a5a8(0x179)]=_0x56a5a8(0x17a):document[_0x56a5a8(0x184)](_0x56a5a8(0x175))[_0x56a5a8(0x179)]='HEHE\x20my\x20secret\x20is\x20well\x20kept\x20!';}
```
ada 1 string yang menarik
`%64%76%43%54%46%7b%31%74%5f%69%73%5f%6e%30%74%5f%34%5f%73%65%63%72%33%74%5f%34%6e%79%6d%30%72%33%7d`
diubah menjadi char
```
d = "%64%76%43%54%46%7b%31%74%5f%69%73%5f%6e%30%74%5f%34%5f%73%65%63%72%33%74%5f%34%6e%79%6d%30%72%33%7d"
print("".join(map(lambda x: chr(int(x, 16)), d.split("%")[1:])))

# output
# dvCTF{1t_is_n0t_4_secr3t_4nym0r3}
```

# CRYPTO
## Substitution

Rm xibkgltizksb, z hfyhgrgfgrlm xrksvi rh z nvgslw lu vmxibkgrmt rm dsrxs fmrgh lu kozrmgvcg ziv ivkozxvw drgs xrksvigvcg, zxxliwrmt gl z urcvw hbhgvn; gsv "fmrgh" nzb yv hrmtov ovggvih (gsv nlhg xlnnlm), kzrih lu ovggvih, girkovgh lu ovggvih, nrcgfivh lu gsv zylev, zmw hl uligs. Gsv ivxvrevi wvxrksvih gsv gvcg yb kviulinrmt gsv rmevihv hfyhgrgfgrlm.

Hfyhgrgfgrlm xrksvih xzm yv xlnkzivw drgs gizmhklhrgrlm xrksvih. Rm z gizmhklhrgrlm xrksvi, gsv fmrgh lu gsv kozrmgvcg ziv ivziizmtvw rm z wruuvivmg zmw fhfzoob jfrgv xlnkovc liwvi, yfg gsv fmrgh gsvnhvoevh ziv ovug fmxszmtvw. Yb xlmgizhg, rm z hfyhgrgfgrlm xrksvi, gsv fmrgh lu gsv kozrmgvcg ziv ivgzrmvw rm gsv hznv hvjfvmxv rm gsv xrksvigvcg, yfg gsv fmrgh gsvnhvoevh ziv zogvivw.

Gsviv ziv z mfnyvi lu wruuvivmg gbkvh lu hfyhgrgfgrlm xrksvi. Ru gsv xrksvi lkvizgvh lm hrmtov ovggvih, rg rh gvinvw z hrnkov hfyhgrgfgrlm xrksvi; z xrksvi gszg lkvizgvh lm ozitvi tilfkh lu ovggvih rh gvinvw klobtizksrx. Z nlmlzokszyvgrx xrksvi fhvh urcvw hfyhgrgfgrlm levi gsv vmgriv nvhhztv, dsvivzh z klobzokszyvgrx xrksvi fhvh z mfnyvi lu hfyhgrgfgrlmh zg wruuvivmg klhrgrlmh rm gsv nvhhztv, dsviv z fmrg uiln gsv kozrmgvcg rh nzkkvw gl lmv lu hvevizo klhhryrorgrvh rm gsv xrksvigvcg zmw erxv evihz.
weXGU{xi1kg3w_x1ks3i}

Solution:
Saya menggunakan [substitution cipher](https://www.dcode.fr/monoalphabetic-substitution) dan mendapatkan `...DVCTF{CR1PT3D_C1PH3R}`. Tinggal ubah casenya menjadi `dvCTF{cr1pt3d_c1ph3r}`
