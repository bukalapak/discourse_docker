# NAME:     discourse/base
# VERSION:  release
FROM christoperhanstech/discourse-base

ENV PG_MAJOR 10
ENV RUBY_ALLOCATOR /usr/lib/libjemalloc.so.1
ENV COMPRESS_BROTLI 1

#LABEL maintainer="Christoper Hans \"https://github.com/ChrHan\""

# Discourse specific bits
RUN useradd discourse -s /bin/bash -m -U &&\
    mkdir -p /var/www &&\
    cd /var/www &&\
    git clone https://github.com/bukalapak/discourse.git &&\
    cd discourse &&\
    git remote set-branches --add origin tests-passed &&\
    chown -R discourse:discourse /var/www/discourse &&\
    cd /var/www/discourse &&\
    sudo -u discourse bundle install --deployment \
         --without test --without development &&\
    find /var/www/discourse/vendor/bundle -name tmp -type d -exec rm -rf {} +
