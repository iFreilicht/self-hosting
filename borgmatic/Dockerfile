FROM b3vis/borgmatic
ARG MYSQL_USER
ARG MYSQL_PASSWORD

# Put username and password into a config file that will be read when the database is dumped
RUN echo -e "[client]\n" \
            "user=$MYSQL_USER\n" \
            "password=$MYSQL_PASSWORD\n" \
    > /root/.my.cnf