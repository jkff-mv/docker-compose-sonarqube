# SonarQube over HTTPS on Docker Compose
[![sonarqube version](https://img.shields.io/badge/SonarQube-8.2-blue)](https://www.sonarqube.org/)
[![license](https://img.shields.io/badge/license-MIT%20License-lightgrey.svg)](https://github.com/jkff-mv/cloud-build-badge/blob/master/LICENSE)

## Overview
HTTPSで通信できるSonarQubeを立ち上げるためのDocker Composeの設定です。  

## What is SonarQube?
[SonarQube](https://www.sonarqube.org/) はオープンソースのコード品質管理ツールです。  
コードの重複を検出したり、複雑度を計測したり、バグや脆弱性の存在を指摘してくれます。  

## Requirement
動作要件です。  
事前に下記の作業を実施ください。  

* ホストにDockerとDocker Composeをインストールする（必要に応じてカーネルも調整する）。  
* ドメインを取得し、DNSの設定を行う。  
* ホストに対して外部からアクセスできるようにする（80番と443番ポートを開放する）。  

## Usage

### Setup
ホストのドメイン名や [Let's Encrypt](https://letsencrypt.org/) の利用に必要なメールアドレスを `.env` に設定します。  

```
SONARQUBE_DOMAIN=your.sonarqube.domain.jp
LETSENCRYPT_EMAIL=your.email.address@gmail.com
```

### Start up SonarQube!
プロジェクトのルートに移動し下記コマンドを実行します。  

```
$ docker-compose up -d
```

`https://your.sonarqube.domain.jp/` からSonarQubeにアクセスできます。 :whale::sparkles::sparkles:  
なお、デフォルトのユーザIDとパスワードは `admin/admin` です。  

## Note

### Customize Nginx
リバースプロキシとして [Nginx](https://nginx.org/en/) を使用しています。  
設定の調整が必要な場合は `nginx/custom.conf` を編集してください。  

### Upgrade SonarQube
[公式ドキュメント](https://docs.sonarqube.org/latest/setup/upgrading/) の指示に従ってください。  

## Reference
下記のイメージを使用しています。  

* [sonarqube](https://hub.docker.com/_/sonarqube)  
* [postgres](https://hub.docker.com/_/postgres)  
* [jwilder/nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy)  
* [jrcs/letsencrypt-nginx-proxy-companion](https://hub.docker.com/r/jrcs/letsencrypt-nginx-proxy-companion)  
