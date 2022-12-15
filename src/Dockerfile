FROM node:current-alpine3.17 as dependencies

ARG value1=not-set
ENV ACCESS_TOKEN_SECRET=$value1

ARG value2=not-set
ENV REFRESH_TOKEN_SECRET=$value2


ARG REFRESH_TOKEN_SECRET=not-set

WORKDIR /app
COPY . .
RUN yarn install --frozen-lockfile
RUN yarn install
RUN apk --no-cache add curl
#RUN curl -sfL https://install.goreleaser.com/github.com/tj/node-prune.sh | /bin/sh -s -- -b /usr/local/bin
# run node prune to prune dependencies. It Helped me to save ~38 MB. 
#RUN /usr/local/bin/node-prune
EXPOSE 3000
CMD ["yarn", "start"]
