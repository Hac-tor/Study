## Q3. goblin _ 스트링 우회 기법
<img src="/photo/prob_03.PNG" width="100%" height="100%" alt="problem"></img>

#### 5thofnovmbr
```
풀이: 
?no=1을 하면 Hello guest가 출력된다. guest의 no는 1이다.
?no=1 or no=(admin의 no)를 하더라도 $result['id']의 값이 admin일지는 미지수이므로 ?no=0 or no=(admin의 no)를 입력해야한다. admin의 no는 2이다.
```
```diff
+?no=1 or no=(admin의 no)를 하였을 때  $result['id']의 값이 무조건 전자인 guest가 되는데, 앞에 있어서 우선되는 것 같다. 
+no나 id는 (아마도)auto_increment 설정을 부여하는 경우가 많은 것 같다.
- 사실 웹해킹.kr에서 비슷한 문제가 있어서 바로 admin의 no를 알 수 있었다.
```
