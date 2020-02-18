FROM node:latest

ENV DB_HOST=nwdb DB_PORT=3306 DB_USER=root DB_PASSWORD=changeit
ENV APP_PORT=3000 APP_ROOT=/app

WORKDIR $APP_ROOT

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views
ADD config config

RUN npm install

HEALTHCHECK --interval=10s --timeout=5s --retries=3 \
    CMD curl -s -f http://localhost:$APP_PORT/health > /dev/null || exit 1

EXPOSE $APP_PORT

ENTRYPOINT ["node", "main.js"]