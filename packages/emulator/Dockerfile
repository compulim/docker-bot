FROM node:alpine AS builder
LABEL name="docker-bot-emulator" version="1.0.0"
# ENV PORT=5000
EXPOSE 5000
RUN apk update && apk upgrade && apk add git
RUN npm install -g lerna@2.11
WORKDIR /emulator/
RUN git clone https://github.com/Microsoft/BotFramework-Emulator.git /emulator
RUN git checkout 3b671eeca53f236eb4c5c721df69937ee9db2573 
RUN npm install
RUN lerna bootstrap --hoist
RUN lerna run build --scope=@bfemulator/emulator-core --scope=@bfemulator/emulator-cli
ENTRYPOINT node /emulator/packages/emulator/cli/lib -u http://bot-server:3978/api/messages/ -s http://bot-emulator:5000
