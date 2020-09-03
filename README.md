# pukiwiki-compose

pukiwikiをBuildするための準備

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
