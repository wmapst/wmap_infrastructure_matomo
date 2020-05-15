# wmap_infrastructure_matomo
Dockerを使ったMATOMO(piwik)のDockerComposeです。

## 公式
https://github.com/matomo-org/docker/blob/master/.examples/nginx/docker-compose.yml

## 使い方
```
git clone https://github.com/wmapst/wmap_infrastructure_matomo.git
cd ./docker-compose
vi .env # .env.sample.xxxxx を参考にしてください。
docker-compose up -d
```

## envファイル
このdocker-composeファイルを利用する場合、以下のファイルが必要になります。  
docker-compose.ymlファイルと同階層に設置してください。  

.env

```
# ローカル環境サンプル(.env.sample.local)
DB_NAME=wordpress
DB_USER=wp_user
DB_USER_PASS=wp_passwd
DB_ROOT_PASS=root_passwd
HOST_DOMAIN=localhost
PRODUCTION_STAGE=local
```
```
# ステージング環境サンプル(.env.sample.staging)
DB_NAME=wordpress
DB_USER=wp_user
DB_USER_PASS=wp_passwd
DB_ROOT_PASS=root_passwd
HOST_DOMAIN=st-www.sample-wmapst.net
PRODUCTION_STAGE=staging
```
```
# 本番環境サンプル(.env.sample.production)
DB_NAME=wordpress
DB_USER=wp_user
DB_USER_PASS=wp_passwd
DB_ROOT_PASS=root_passwd
HOST_DOMAIN=www.sample-wmapst.net
PRODUCTION_STAGE=production
```
