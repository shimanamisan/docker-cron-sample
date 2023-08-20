FROM php:8.2.8-fpm

RUN apt-get update && \
  # cron と supervisor を追加
  apt-get -y install git cron supervisor libicu-dev libonig-dev libzip-dev unzip locales && \
  apt-get clean && \
  docker-php-ext-install intl pdo_mysql mbstring zip bcmath && \
  pecl install xdebug && \
  # Xdebug を有効化する
  docker-php-ext-enable xdebug

COPY ./php.ini /usr/local/etc/php/php.ini
# cronの設定内容が書かれたファイルをコンテナ内にコピーする
COPY ./cron/root /etc/cron.d/cron
# supervisordの設定ファイルをコピーする
COPY ./supervisord/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# 権限の変更
RUN chmod 0644 /etc/cron.d/* && \
    touch /var/log/cron.log && \
    # 作業用ユーザーの追加
    useradd -m -s /bin/bash user01 && \
    # Xebugで使用するログファイルの作成とファイルへのアクセス権限を付与する
    touch /var/log/xdebug.log && \
    chown user01:user01 /var/log/xdebug.log && \
    chmod 644 /var/log/xdebug.log

WORKDIR /workspaces

# supervisordを起動
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]