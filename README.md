# pukiwiki-compose

## 前提条件

- wikiコンテンツ自体は `/wiki` 配下に配置されている
- コンテナ(mail)のログ出力先は、`/var/log/mail` 配下に出力されるため、ディレクトリが作成済み
- コンテナ(wiki)のログ出力先は、`/var/log/wiki` 配下に出力させるため、ディレクトリが作成済み
- 上記不要な場合は、docker-compose.yml の volumes を削除すること
- パーミッションは以下を参照

```sh
ls -ld /wiki/ /var/log/mail/ /var/log/wiki/
  # drwxr-xr-x  2  101 adm    22 Sep  9 01:53 /var/log/mail/
  # drwxr-xr-x  2 root root   41 Sep  9 02:05 /var/log/wiki/
  # drwxr-xr-x 18   48   48 4096 Sep  7 07:27 /wiki/
```

## 事前準備

pukiwikiをダウンロード

```sh
curl -L http://prdownloads.sourceforge.jp/pukiwiki/12957/pukiwiki-1.4.7_notb.tar.gz \
     -o pukiwiki/pukiwiki-1.4.7_notb.tar.gz
```

*env.yml*

```yml
version: "3.5"
services:
  mail:
    environment:
      RELAYHOST: [<smtp-server>]:<port>
      MAIL_ADDRESS: <user>
      MAIL_PASSWORD: <password>
```

## 起動

```sh
docker-compose -f docker-compose.yml -f env.yml up -d
```
