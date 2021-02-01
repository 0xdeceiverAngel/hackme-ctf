# hackme
## misc
### 1 flag
flag:`FLAG{This is flag's format}`
### 2 corgi can fly
用stegsolve看 裡面有一張qrcode 
> java -jar .\Stegsolve.jar
flag:`FLAG{Corgi is cutest aniaml on the earth >////////<}`
### 3 television
用strings看
flag:`FLAG{PuRe_R@ND0M_DaTa_Fr0M/D3V/UR@ND0M}`
### 4 meow
binwalk開 發現裡面有夾zip
foremost 分離出來
```
.
├── audit.txt
├── png
│   ├── 00000000.png
└── zip
    └── 00000094.zip

```
發現`00000094.zip`裡的png的crc32是`cdad52bd`，跟`00000000.png`的crc32一樣
利用明文攻擊 先把`00000000.png`壓成`plane.zip`
> ./pkcrack -C ../output/zip/00000094.zip -c meow/t39.1997-6/p296x100/10173502_279586372215628_1950740854_n.png -P ../output/png/plain.zip -p 00000000.png -d res.zip -a
```
-C:要破解的目标文件(含路径)
-c:破解文件中的明文文件的名字(其路径不包括系统路径,从zip文件一层开始)
-P:压缩后的明文文件
-p:压缩的明文文件中明文文件的名字(也就是readme.txt在readme.zip中的位置)
```
flag:`FLAG{pkcrack is your frien. MEOW, MEOW, MEOW~}`
### 5 where is flag
> cat flag|grep -oE "FLAG{[a-zA-Z0-9_]*}"
flag:`FLAG{VizQLeu9M3aybJBA3f1AgFROGyuTLXZ2oeRbKf1Agf1AgFLAG9hBTI}`

### 8 pusheen.txt
給你一堆貓貓，黑貓當成1、白貓當成0，binay to string
flag:`FLAG{Pusheen OIOOOIIOOIOOIIOOOIOOOgOOIOIOOOIII Cute}`
### 9 big
- 爆破用regex找flag
- 或是用改hex拿掉重複的，然後改file header的crc32或是foot 看xz的文件應該是這樣沒錯(?)(我沒弄)
flag:`FLAG{Really long file}`
### 10 otaku
### 11 buzzing
### 12 drvtry vpfr
給你神奇的字，其實就是鍵盤打字時往旁邊的按鍵按
flag:`FLAG{Shift My Keyboard And Typing Something}`
### 13 bzbz
找bilibli外洩的原始碼
https://github.com/fitlivingmm/bilibili/blob/master/go-common/app/admin/ep/melloi/cmd/convey-test.toml
裡面有帳密、登入就好
flag:`FLAG{Let's learn golang from bilibili}`