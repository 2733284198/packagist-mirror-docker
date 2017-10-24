# Composer Mirror Docker

## Usage

Schedule in case of restart or another problem, the first execution create a mirror:

```bash
* * * * * root docker run --name mirror -e URL='mymirror.com' webysther/composer-mirror
```

You can add more mirrors with additional URL's separated by comma:

```bash
-e DATA_MIRROR='https://packagist.jp,https://packagist.com.br'
```

Main mirror is used to get providers and fallback in case of error on data mirror, you can also change them:

```bash
-e MAIN_MIRROR='https://packagist.com.br'
```

## Customization of behavior

You can change `CMD` with you own `Dockerfile` or change schedule like this:

```bash
docker run --rm --name mirror -v /var/www/html:/public webysther/composer-mirror php bin/mirror create
```

## Don't use alpine version

Due performance optimizations alpine version is very slow at this moment, keep debian based version of composer.
