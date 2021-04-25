# 20210425資安深耕營解題筆記
## 第一堂base64編碼 - 20 pts
``` python
import base64
base64.b64encode(b"BreakallCTF{happyhackinghighhaaha}")
```
-->b'QnJlYWthbGxDVEZ7aGFwcHloYWNraW5naGlnaGhhYWhhfQ=='

## Base64 - 20 pts
``` python
import base64
base64.b64decode(b"QnJlYWtBTExDVEZ7NTN1c1pRM2hXVzI1ZGNoWjdkWGV9")
```
-->b'BreakALLCTF{53usZQ3hWW25dchZ7dXe}'

## Ascii - 20 pts
``` python
a = "66 114 101 97 107 65 76 76 67 84 70 123 65 109 118 48 117 68 121 101 114 118 80 116 109 86 114 57 83 83 83 75 125"
>>> a
'66 114 101 97 107 65 76 76 67 84 70 123 65 109 118 48 117 68 121 101 114 118 80 116 109 86 114 57 83 83 83 75 125'
>>> a.split()
['66', '114', '101', '97', '107', '65', '76', '76', '67', '84', '70', '123', '65', '109', '118', '48', '117', '68', '121', '101', '114', '118', '80', '116', '109', '86', '114', '57', '83', '83', '83', '75', '125']
>>> for i in a.split():
        print(chr(int(i)),end='')
``` 
-->BreakALLCTF{Amv0uDyervPtmVr9SSSK}

## Base32 - 20 pts
```python
o_data = b'IJZGKYLLIFGEYQ2UIZ5TS6BUHA2VMUZXO5UWS5CCLJMFKVLIJVSX2==='
>>> decode_data = base64.b32decode(o_data)
>>> print(decode_data)
```
-->b'BreakALLCTF{9x485VS7wiitBZXUUhMe}'

## Morse code - 20 pts
線上解碼
-->INFOSECFLAGISMORSING

## hello world - 50 pts
```python
from pwn import *           //引入模組

ip = "120.114.62.214"
port = 2405
r = remote(ip, port)
res = r.recv()		          //接收資料
print(res)

r.interactive()	            //將資料傳入遠端電腦
```

執行結果
```python
15:18 user@user-VirtualBox(10.0.2.15)[~] 
[XD] % gedit hello.py
15:19 user@user-VirtualBox(10.0.2.15)[~] 
[XD] % python3 hello.py
[+] Opening connection to 120.114.62.214 on port 2405: Done
b'===== Welcome to CTF =====\nYou successfully reach this problem\nCongratulation!!!\nWait for a few second, let me get you the flag\n\n'
[*] Switching to interactive mode
Here you go : CTF{Hel10WorLD123}
[*] Got EOF while reading in interactive
$ 
```

## 3rd - 50 pts
```python
from pwn import *

ip = "120.114.62.214"
port = 2400

r = remote(ip, port)
r.recvuntil("Now You Turn")               //從now you turn到:
r.recvuntil(" : ")
res = r.recvline()[:-1]                   //從最後讀取

res = list[map(int, res.split())]         //從res.split()裡抽元素變成數字並轉為陣列
res.sort()                                //轉為小到大的排序
print(res[-3])                            //取小到大陣列中的第三大的數字(從最後[-1]往前找3)
r.interactive()
```

執行結果
```python
15:21 user@user-VirtualBox(10.0.2.15)[~] 
[XD] % gedit 3rd.py
15:21 user@user-VirtualBox(10.0.2.15)[~] 
[XD] % python3 3rd.py  
[+] Opening connection to 120.114.62.214 on port 2400: Done
97122
[*] Switching to interactive mode
answer : $ 97122
CTF{yoUaReInth33RdpL4c3}
[*] Got EOF while reading in interactive
$ 
```
<另解> 算出答案之後直接回傳給sever
```python
from pwn import *

ip = "120.114.62.214"
port = 2400

r = remote(ip, port)
r.recvuntil("Now You Turn")
r.recvuntil(" : ")
res = r.recvline()[:-1]

res = list(map(int, res.split()))
res.sort()
r.recvuntil("answer:")
r.sendline(str(res[-3]))

r.interactive()	
```

## count - 50 pts
```python
from pwn import *

ip = "120.114.62.214"
port = 2403

r = remote(ip, port)

r.recvuntil("wave")
r.recvuntil("?")
for i in range(1,101,1):              //從1到100
    r.sendline(str(i))                //將數字轉為字串
   
r.interactive()
```
執行結果
```python
15:44 user@user-VirtualBox(10.0.2.15)[~] 
[XD] % gedit count.py  
15:45 user@user-VirtualBox(10.0.2.15)[~] 
[XD] % python3 count.py
[+] Opening connection to 120.114.62.214 on port 2403: Done
[*] Switching to interactive mode

----- wave 2/100 -----
I say 2 you say?
----- wave 3/100 -----
I say 3 you say?
----- wave 4/100 -----
I say 4 you say?
----- wave 5/100 -----
I say 5 you say?
----- wave 6/100 -----
I say 6 you say?
----- wave 7/100 -----
I say 7 you say?
----- wave 8/100 -----
I say 8 you say?
----- wave 9/100 -----
I say 9 you say?
.
.
.
.
.
```
