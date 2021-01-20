FROM php:7.4-fpm-buster

SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]
# Linuxの場合デフォルト ["/bin/sh", "-c"] 
# -o オプションを設定するためのオプションです。
# -e シェルスクリプト内で何らかのエラーが発生した時点で、それ以降の処理を中断できます。
# -u 未定義の変数に対して読み込み等を行おうとした際にエラーとなります。
# -x 実行したコマンドを全て標準エラー出力に出してくれます。

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer
  # 環境変数 <key> に <value> という値を設定する。ENV を用いて設定された環境変数は、そのイメージから実行されたコンテナーであれば維持されます

COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer
      # --from でイメージを参照してそれを/usr/bin/composerから/usr/bin/composerへコピーしている？

RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql zip bcmath
  # apt-get update インストール可能なパッケージの「一覧」を更新
  # apt-get -y install xxx Laravelのインストールに必要なパッケージをインストール
  # apt-get clean && rm -rf /var/lib/apt/lists/* ここはパッケージインストールで使用したキャッシュファイルを削除
  # docker-php-ext-install intl pdo_mysql zip bcmath PHPの拡張ライブラリをインストールしています。

COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /work