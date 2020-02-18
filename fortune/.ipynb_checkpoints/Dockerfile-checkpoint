FROM node:latest
ENV APP_PORT=3000 APP_ROOT=/app

WORKDIR $APP_ROOT

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views

RUN npm install

HEALTHCHECK --interval=10s --timeout=5s --retries=3 \
    CMD curl -s -f http://localhost:$APP_PORT/health > /dev/null || exit 1

EXPOSE $APP_PORT

ENTRYPOINT ["node", "main.js"]

