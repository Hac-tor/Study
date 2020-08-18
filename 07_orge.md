## Q7. orge
<img src="/photo/prob_07.PNG" width="100%" height="100%" alt="problem"></img>

#### 5thofnovmbr
```
풀이:
and가 or보다 먼저인데 반대로 생각하고 있어서 헤맸다. 
```
> select id from prob_orge where id='guest' and pw=''||(참)n-- 
```
위처럼 쿼리문을 작성하면 and연산이 먼저 진행되어 id='guest' and pw=''은 거짓이 된다.
pw값이 거짓이기만 하면 id='guest'부분이 아무 효력을 가지지 못한다.
이를 이용해 pw의 길이를 알아낼 수 있다.
```
> select id from prob_orge where id='guest' and pw=''||length(pw)=숫자--
```
4번 orc 문제처럼 "Hello admin", "Hello guest"가 반환값에 있는지에 따라 길이를 알아낼 수 있다.
```
> [파이썬코드-길이](https://github.com/5thofnovmbr/etc/blob/master/los_orge_pw_length.py)
```
뒷 부분도 4번과 같다.
그런데 substr 함수를 전과 똑같이 했더니 작동이 되지 않았다.
substr(str FROM pos FOR len)형식을 썼었는데, 
substr(str, pos, len)으로 바꾸었더니 잘 된다. 
앞으로는 밑의 방식을 이용해야겠다.
guest의 pw를 알아내는 코드도 추가했다.
```
> [파이썬코드-문자](https://github.com/5thofnovmbr/etc/blob/master/los_orge_pw.py)
```diff
+ and가 먼저다~~
```
