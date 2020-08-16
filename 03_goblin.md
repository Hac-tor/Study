## Q3. goblin _ 스트링 우회 기법
<img src="/photo/prob_03.PNG" width="100%" height="100%" alt="problem"></img>

#### 5thofnovmbr
```
풀이: 
?no=1을 하면 Hello guest가 출력된다. guest의 no는 1이다.
?no=1 or no=(admin의 no)를 하더라도 $result['id']의 값이 admin일지는 미지수이므로 ?no=0 or no=(admin의 no)를 입력해야한다.
admin의 no는 2이다.
```
```diff
+?no=1 or no=(admin의 no)를 하였을 때  $result['id']의 값이 무조건 전자인 guest가 되는데, 앞에 있어서 우선된다고 생각한다.
+no나 id는 (아마도)auto_increment 설정을 부여하는 경우가 많은 것 같다.
- 사실 웹해킹.kr에서 비슷한 문제가 있어서 바로 admin의 no를 알 수 있었다.
```
#### TOR-s
```
풀이: ?no=0 || id like 0x61646d696e
```
```diff
+ 스트링 우회 기법을 배웠다.
```
#### zero526
```
풀이: ?no=-1 union select (0x61646d696e)
```
```diff
+ 무작위 삽입으로 no=1을 입력하면 Hello guest가 출력되는것을 확인하여 guest에 해당하는 no가 1이라는것을 알았다
+ no에 1이 아닌 값을 입력해서 query문을 일단 거짓으로 만들고 union select로 admin을 16진수값으로 변환한 값을 추가로 입력해주어
  query문의 select id부분에서 추가로 입력한 값을 받아오게 만들어 해결했다
  ```
