# 課堂活動紀錄
## 編碼101 : Ascii  :
```python
a = "66 114 101 97 107 65 76 76 67 84 70 123 65 109 118 48 117 68 121 101 114 118 80 116 109 86 114 57 83 83 83 75 125"
a.split()
##['66', '114', '101', '97', '107', '65', '76', '76', '67', '84', '70', '123', '65', '109', '118', '48', '117', '68', '121', '101', '114', '118', '80', '116', '109', '86', '114', '57', '83', '83', '83', '75', '125']
for i in a.split():     
     print(chr(int(i)),end='')        

##BreakALLCTF{Amv0uDyervPtmVr9SSSK}
```

## 列表操作(普通且直觀的方法)
```python
sentence = "the quick brown fox jumps over the lazy dog"
words = sentence.split()
word_lengths = []
for word in words:
       if word != "the":
           word_lengths.append(len(word))
 
print(words)
##['the', 'quick', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog']
print(word_lengths)
##[5, 5, 3, 5, 4, 4, 3]
```

## 列表生成 (list comprehensions)
```python
sentence = "the quick brown fox jumps over the lazy dog"
words = sentence.split()
word_lengths = [len(word) for word in words if word != "the"]
print(words)
##['the', 'quick', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog']
print(word_lengths)
##[5, 5, 3, 5, 4, 4, 3]
```
## Map
```python
my_pets = ['alfred', 'tabitha', 'william', 'arla']
uppered_pets = list(map(str.upper, my_pets))
print(uppered_pets)
##['ALFRED', 'TABITHA', 'WILLIAM', 'ARLA']
```

## Filter
```python
scores = [66, 90, 68, 59, 76, 60, 88, 74, 81, 65]
def is_A_student(score):
    return score > 75

over_75 = list(filter(is_A_student, scores))
print(over_75)
##[90, 76, 88, 81]
```

## Reduce
```python
from functools import reduce
numbers = [3, 4, 6, 9, 34, 12]
def custom_sum(first, second):
    return first + second

result = reduce(custom_sum, numbers)
print(result)
##68
```

## 編碼101 :第一堂base64編碼,Base64,Base32
```python
import base64
base64.b64encode(b"BreakallCTF{happyhackinghighhaaha}")
##b'QnJlYWthbGxDVEZ7aGFwcHloYWNraW5naGlnaGhhYWhhfQ=='
base64.b64decode(b"QnJlYWtBTExDVEZ7NTN1c1pRM2hXVzI1ZGNoWjdkWGV9")
##b'BreakALLCTF{53usZQ3hWW25dchZ7dXe}'
base32.b32decode(b"IJZGKYLLIFGEYQ2UIZ5TS6BUHA2VMUZXO5UWS5CCLJMFKVLIJVSX2===")
##b'BreakALLCTF{9x485VS7wiitBZXUUhMe}'
```

## 編碼101 :Morse code
解底下的題目:  
.. -. ..-. --- ... . -.-. ..-. .-.. .- --. .. ... -- --- .-. ... .. -. --.  
Ans :  
INFOSECFLAGISMORSING

## PPC_Ez : hello world

### 以下為Linux
14:28 user@user-VirtualBox(10.0.2.15)[~]   
[XD] % nc 120.114.62.214 2405  
===== Welcome to CTF =====  
You successfully reach this problem  
Congratulation!!!  
Wait for a few second, let me get you the flag  

Here you go : CTF{Hel10WorLD123}

## PPC_Ez : 3rd 

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
print(res[-3])

r.interactive()
```
### 以下為Linux
[XD] % python3 3rd.py  
[+] Opening connection to 120.114.62.214 on port 2400: Done  
99202  
[* ] Switching to interactive mode  
answer : $ 99202  
CTF{yoUaReInth33RdpL4c3}  
[* ] Got EOF while reading in interactive  
$  
## PPC_Ez : count
```python
from pwn import *
ip = "120.114.62.214" 
port = 2403
r = remote(ip, port)

for i in range(1,101):
	r.recvuntil("wave")
	r.recvuntil("?")
	r.sendline(str(i))

r.interactive()
```
### 以下為Linux
[XD] % python3 count.py  
[+] Opening connection to 120.114.62.214 on port 2403: Done  
[* ] Switching to interactive mode  

CTF{gOOD4tMatHYOUarE}  
[* ] Got EOF while reading in interactive  
$  






