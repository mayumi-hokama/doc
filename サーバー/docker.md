# dockerについて
### インストール


### dockerコマンド

 - プロセス確認
```
docker ps
```
 - イメージ確認
```
docker images
```
 - commit
```
docker commit refcru_base refcru:2.6.7
```
 - 環境コピーして起動
```
ex)
docker run -d -p 49100:22 -p 49102:443 -p 49101:80 --name hokama refcru:base /etc/service.sh
```
