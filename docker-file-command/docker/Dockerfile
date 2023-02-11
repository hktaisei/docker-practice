# ベースイメージ
FROM centos:7

# ラベル（バージョン、ベンダ名や作者）
LABEL version: '1.0'\
      com.example.mail: 'a@a.com'

# コマンド実行(ビルド時)
RUN yum install -y httpd

# コマンド実行(run実行時)
# イメージを実行するときに、オプションがなければ自動的に実行するコマンド
# centosだとデフォルトでCMD ["/bin/bash"]が書かれている
# CMD ["/bin/bash"]

# コマンド実行(run時に絶対実行)
# CMDは、ENTRYPOINTの引数になる
# CMDがない場合は、run引数になる
ENTRYPOINT ["ping", "-c", "3"]

# ENTRYPOINTの引数になるCMD※引数無しで起動した場合
CMD ["localhost"]

# 公開ポート番号
EXPOSE 22 80

# 環境変数
ENV DB_HOST= \
    DB_PORT= \
    DB_USER= \
    DB_PASSWD= \
    DB_DATABASE=

# Dockerfile内のみ使える変数
ARG test='test'
RUN echo $test

# ファイルをイメージにコピーできる
# ファイル名→ファイル名、ディレクトリ名→ディレクトリ名の場合は上書きされる
COPY ./config/config.txt /etc/config

# 圧縮ファイル(.tar.gzなど)を展開してコピーする
# またURLを指定してコピーすることもできる
ADD ./config/config.txt /etc/config
# ADD https://example.com

# 永続ボリュームを割り当てる。※名前はつけられない
VOLUME ./data

# プロセスの実行ユーザを指定する。
USER root

# 実行シェルを指定します。
SHELL ["/bin/bash"]

# コマンドを実行するディレクトリを指定する。
WORKDIR /

# その他
# ONBUILD RUN ~~ : ベースイメージとして利用されてビルドされたときに実行される
# STOPSIGNAL : docker stopしたときに実行される
# HEALTHCHECK : コンテナの稼働チェックを定期的にチェックします。






