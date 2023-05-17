FROM bitnami/mysql:5.7
COPY seed.sql /docker-entrypoint-initdb.d/ 
ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=trainees
