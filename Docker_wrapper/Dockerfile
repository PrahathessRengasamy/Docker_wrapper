# This docker file sets up the base container for other applications



FROM ruby:2.3.1
MAINTAINER parabuzzle@gmail.com

RUN gem install vault

COPY lib/vault_loader.rb /lib/vault_loader.rb
COPY bin/vaultenv /bin/vaultenv
COPY app_env /tmp/app_env
COPY bin/with_app_env /bin/with_app_env

RUN chmod +x /bin/vaultenv
RUN chmod +x /bin/with_app_env

ENV APP_ENV development
ENV VAULT_ADDR http://vault:8200

WORKDIR /webapp

ENTRYPOINT [ "with_app_env" ]

CMD [ "bash" ]
