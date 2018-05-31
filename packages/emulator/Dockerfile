FROM node:alpine AS builder
LABEL name="docker-bot-emulator" version="1.0.0"
# ENV PORT=5000
EXPOSE 5000
RUN apk update && apk upgrade && apk add git
RUN npm install -g lerna@2.11
WORKDIR /emulator/
RUN git clone https://github.com/Microsoft/BotFramework-Emulator.git /emulator
RUN npm install
RUN lerna bootstrap --hoist
RUN lerna run build --scope=@bfemulator/emulator-core --scope=@bfemulator/emulator-cli
ENTRYPOINT node /emulator/packages/emulator/cli/lib
