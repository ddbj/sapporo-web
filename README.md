# sapporo-web

This repository has been forked from [GitHub - sapporo-wes/sapporo-web](https://github.com/sapporo-wes/sapporo-web).
See [GitHub - sapporo-wes/sapporo-web](https://github.com/sapporo-wes/sapporo-web).

## Branch Management

Basically, the `main` branch is the mainstream of the ddbj production environment.
If you want to add a new feature, please branch off from `main` and send a PR to `main`.
Note that follow-ups to `sapporo-wes/sapporo-web` will be merged into `main` whenever there is a new release of `sapporo-wes/sapporo-web`.

## deploy memo

```bash
$ docker-compose -f docker-compose.dev.yml up -d --build
$ docker-compose -f docker-compose.dev.yml exec app yarn build
$ docker-compose -f docker-compose.dev.yml exec -d app yarn start
```

## License

[Apache-2.0](https://www.apache.org/licenses/LICENSE-2.0). See the [LICENSE](https://github.com/ddbj/sapporo-web/blob/main/LICENSE).
