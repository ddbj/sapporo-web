# sapporo-web

This repository has been forked from [GitHub - sapporo-wes/sapporo-web](https://github.com/sapporo-wes/sapporo-web).
See [GitHub - sapporo-wes/sapporo-web](https://github.com/sapporo-wes/sapporo-web).

Deployed URL:

- `sapporo-service`: https://ddbj.nig.ac.jp/ga4gh/wes/v1/service-info
- `sapporo-web`: https://ddbj.nig.ac.jp/wes/

## Branch 管理

- `main` が default branch。
- https://github.com/sapporo-wes/sapporo-web を upstream として、rebase する
  - PR UI では、rebase 出来なかった

```bash
$ git clone https://github.com/ddbj/sapporo-web.git
$ cd sapporo-web
$ git remote add upstream https://github.com/sapporo-wes/sapporo-web.git
$ git fetch upstream
$ git rebase upstream/main
...
$ git push origin main # or use force push
```

- この repository に対する commit は、適宜 squash する。

```bash
$ git log upstream/main --oneline | head -1
f7f4825 Update version to 1.3.2
$ git rebase --i f7f4825
```

## Deploy メモ

### 運用ユーザ

`sapporo-admin` user で deploy する。

```bash
$ sudo -i -u sapporo-admin
```

### Sapporo-web

docker-compose を使用して、deploy する。

```bash
$ pwd
/home/sapporo-admin
$ git clone --depth 1 https://github.com/ddbj/sapporo-web.git
$ cd sapporo-web

$ docker-compose up -d --build
```

## License

[Apache-2.0](https://www.apache.org/licenses/LICENSE-2.0).
See the [LICENSE](https://github.com/ddbj/sapporo-web/blob/main/LICENSE).
