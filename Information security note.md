# 20210425資安深耕營上課筆記
## Python環境
安裝Python：https://www.python.org/downloads/

指令下載安裝：
```python
sudo apt install python3
```

## 使用Python
在Python直譯器上打入
```python
python3
```
將程式寫成一個檔案 再使用Python
```python
python3 script.py
```
## 寫程式的開端
```python
print("Hello, World!")
```
簡單的語法
```python
x = 2                   //設x變數的數值為2

if x == 2:              //判斷x變數的數值是否為2
    print("x is 2.")    //成立的話輸出
```
縮排(indent)

使用tab或空格鍵
官方縮排為4個空格

## 變數與型態
變數命名不能是數字開頭及包含運算子
```python
a, b = 89, 21
print(a,b)

a, b = "ha", "lapo"
print(a,b)
```
數字分為整數(int)及浮點數(float)
```python
mynumber = 7             //整數(int)型態
print(mynumber)

numberfloat = 7.0       //浮點數(float)型態
print(numberfloat)

numberfloat = float(7)  //將整數(int)轉為浮點數(float)
print(numberfloat)
```
數字相關函數
```python
bin(4)                  //轉成二進位表示法
oct(6)                  //轉成八進位表示法 
hex(32)                 //轉成十六進位表示法
int('9')                //將字串轉為數字
int('9', 8)             //八進制
```
字串(string)就像是顯現出來的圖案
```python
istring = 'hello'       //字串外要加上''或""
print(istring)
```
字串相關函式
```python
str(5599)               //可用來建立字串或將數值轉換成字串
chr(0x64)               //可取得指定的ASCII字元碼的字元
ord('o')                //在ASCII中的值
len('hello')            //字串的長度
```

字串與位元的轉換
```python
istring = "你好"
print(istring)
ibytes = istring.encode("utf8")         //將字串編碼
print(ibytes)
istring = ibytes.decode("utf8")         //將位元組解碼
print(istring)
```
列表(list)
```python
ilist = []                             //建立一個空的列表

ilist.append(1)                        //使用append增加列表中的元素
ilist.append(2.8)                      //可在列表中增加的元素 除了整數 也可以使用浮點數及字串
ilist.append("haha")

print(ilist[0])                        //印出字串中的第一個元素
print(ilist[1]) 
print(ilist[2]) 
for x in ilist:
    print(x)
```
字典(dict)

一個鍵(key)配上一個值(value)
```python
phonenumber = {}
phonenumber["John"] = 938477566
phonenumber["Jack"] = 938377264
print(phonenumber)

phonenumber = {"John" : 938477566,"Jack" : 938377264}
for name, number in phonenumber.items():
    print(f"Phone number of {name} is {number}")
```
集合(set)
```python
a = set(["1", "2", "3"])
b = set(["2", "5"])

print(a.intersection(b))                //使用交集
print(a.union(b))                       //使用聯集
print(a.difference(b))                  //使用差集
print(a.symmetric_difference(b))
```
## 基本運算子
算數運算子

加 +
減 -
乘 *
除 / (浮點數除法)
除 // (整數除法)
取餘數 %
冪次 **
```python
number = 1 + 2 * 3 / 4.0        //使用加號、乘號、除號進行運算
print(number)

remainder = 11 % 3              //取餘數
print(remainder)

squared = 7 ** 2                //取幾次方
print(squared)
```
比較運算子

大於 >
小於 <
等於 ==
大於等於 >=
小於等於 <=
不等於 !=

邏輯運算子

且 and
或 or
異或 ^
非 not

字串運算子

加 +
乘 *
```python
helloworld = "hello" + " " + "world"
print(helloworld)

lotsofhellos = "woow" * 10
print(lotsofhellos)
```
列表運算子

加 +
乘 *
```python
even_numbers = [2,4,6,8]
odd_numbers = [1,3,5,7]
all_numbers = odd_numbers + even_numbers        //輸出列表中的偶數及奇數
print(all_numbers)

print([1,2,3] * 3)
```
## 基本字串操作
字串的長度使用len
```python
istring = "Hello hello!"
print(len(istring))                             //輸出字串的長度
```
字串的位置使用index
```python
istring = "Hello world!"
print(istring.index("o"))                       //尋找字串的位置
```
字串計數使用count
```python
istring = "Hello hello!"
print(istring.count("l"))                       //計算l出現的次數
```
子字串的應用
[start ; stop ; step]

子字串包含start stop終點位置不包含 step為每一次的間隔

```python
istring = "Hello world!"

print(istring[3:7])                             //取字串中index為3到6的元素 沒有設定step代表初始值為1
print(istring[3:7:2])                           //取字串中index為3到6的元素 每兩個取一次
print(istring[::-1])                            //從最後輸出
```



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
