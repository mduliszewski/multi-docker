FROM node:alpine
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
# the previous block was ended because the 'FROM' command appeard (one block can have 1 FROM command)

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html
# default nginx command runs nginx for us so we dont have to specify any RUN command