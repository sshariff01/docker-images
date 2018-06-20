FROM bitnami/rails

USER root

RUN yes | apt-get update

RUN yes | apt-get install vim wget libsqlite3-dev nodejs apt-transport-https libnss3 libxss1 libappindicator1 libindicator7

RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -

RUN sudo sh -c 'echo "deb https://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'

RUN yes | apt-get update \
    && yes | apt-get install google-chrome-stable

USER bitnami

