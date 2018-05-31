FROM node:alpine
LABEL name="bot-server" version="1.0.0"
ENV PORT=3978
EXPOSE 3978
ENTRYPOINT node .
ADD . /bot/
WORKDIR /bot/
RUN npm install
