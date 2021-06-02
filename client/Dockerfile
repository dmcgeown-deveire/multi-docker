FROM node:alpine
# set the working directory
WORKDIR '/app'
# copy the package.json for the npm install
COPY ./package*.json ./
RUN npm install
# copy all project files
COPY ./ ./
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build/ /usr/share/nginx/html