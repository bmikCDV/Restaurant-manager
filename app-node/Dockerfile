FROM node:14.17.0
WORKDIR /app

COPY package*.json ./app
COPY yarn.lock ./app

RUN yarn
RUN yarn global add cross-env
RUN yarn global add nodemon

#RUN npx sequelize db:migrate

EXPOSE 3000

CMD [ "yarn", "test-api" ]
