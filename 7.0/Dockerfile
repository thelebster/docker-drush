FROM php:7.0.31-cli-alpine

MAINTAINER Anton Lebedev <mailbox@lebster.me>

RUN apk add --no-cache mysql-client openssh-client rsync \
  && curl -sS https://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer \
  && composer global require drush/drush:8.* \
  && rm -f /usr/local/bin/drush \
  && ln -s ~/.composer/vendor/bin/drush /usr/local/bin/drush \
  && drush core-status -y

CMD ["drush", "core-cli"]
