FROM postgres:9.4

RUN apt-get update && \
  apt-get -y install iputils-ping

ENV  PGPASSWORD=12345678

ADD init.sql /docker-entrypoint-initdb.d/

# Adjust PostgreSQL configuration so that remote connections to the
# database are possible.
RUN echo "host all  all    0.0.0.0/0  trust" >> /usr/share/postgresql/pg_hba.conf

# And add ``listen_addresses`` to ``/etc/postgresql/9.3/main/postgresql.conf``
RUN echo "listen_addresses='*'" >> /usr/share/postgresql/postgresql.conf.sample

CMD ["postgres"]

EXPOSE 5432
