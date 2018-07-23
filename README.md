# Drush

[A command line shell for Drupal](https://www.drush.org) in a Docker. Built on top of [PHP Cli Alpine](https://hub.docker.com/_/php/).

~ 160Mb

## Installes Packages
* php-cli
* composer
* drush
* mysql-client
* rsync
* openssh-client

## Usage

### Build
```
docker build --rm -t thelebster/drush 7.1
```

### Run
```
docker run --rm -it thelebster/drush drush status
```

For example you could mount a volume with an drush aliases, like `~/.drush`. Make an sql dump:
```
docker run --rm -it \
-v "$HOME"/.ssh/ssh-key:/root/.ssh/ssh-key:ro \
-v "$HOME"/.drush:/root/.drush \
thelebster/drush \
drush @sitename.live sql-dump --gzip --structure-tables-list=ctools_object_cache,ctools_css_cache,cache,cache_field,cache_form,cache_filter,cache_menu,cache_page,cache_views,cache_views_data,history,sessions,watchdog > /var/backups/bkp_`date +"%m_%d_%Y-%H:%M"`.sql.gz
```
