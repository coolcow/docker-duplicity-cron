# ghcr.io/coolcow/duplicity-cron

This image extends [ghcr.io/coolcow/duplicity](https://github.com/coolcow/docker-duplicity) with cron support for scheduled backups.

---

## About

For a full description, features, configuration options, and usage examples for Duplicity, see the [docker-duplicity README](https://github.com/coolcow/docker-duplicity#readme).

This image only adds cron support for running scheduled backups inside the container.

---

## Usage

Mount your crontab file and set the `CROND_CRONTAB` environment variable:

```sh
docker run --rm \
  -e PUID=$(id -u) \
  -e PGID=$(id -g) \
  -e CROND_CRONTAB=/crontab \
  -v /path/to/data:/data \
  -v /path/to/backup:/backup \
  -v /path/to/crontab:/crontab:ro \
  ghcr.io/coolcow/duplicity-cron
```

Example crontab entry (in `/path/to/crontab`):

```
0 2 * * * duplicity /data file:///backup
```

---

## Environment Variables

See [docker-duplicity Environment Variables](https://github.com/coolcow/docker-duplicity#environment-variables) for all options. This image adds:

| Variable         | Default   | Description                           |
|------------------|-----------|---------------------------------------|
| `CROND_CRONTAB`  | /crontab  | Path to crontab file in the container |

---

## License

GPL-3.0. See [LICENSE.txt](LICENSE.txt) for details.