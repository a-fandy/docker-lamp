FROM mysql:8.0

ADD init-development.sql /docker-entrypoint-initdb.d

ENV TZ=Asia/Jakarta
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone