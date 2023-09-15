FROM mysql:8
RUN usermod -u 1000 mysql

# execute default strcture for becvar_site database
ADD ./structure.sql /docker-entrypoint-initdb.d