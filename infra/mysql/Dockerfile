FROM mysql:8.0

    #↓記述ミス　Exitになる
ENV MYSQL_DATABASE=laravel_local \
  MYSQL_USER=phper \
  MYSQL_PASSWORD=secret \
  #↓書き忘れ　Exitになる
  MYSQL_ROOT_PASSWORD=secret \
  TZ=Asia/Tokyo

COPY ./my.cnf /etc/mysql/conf.d/my.cnf
# my.cnf に書き込み権限が付いてるとMySQLの起動時にエラーが発生する。対策として、my.cnf ファイルコピー、読み取り専用に権限変更

RUN chmod 644 /etc/mysql/conf.d/my.cnf