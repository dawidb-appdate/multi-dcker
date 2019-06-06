FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
#this generates build foder with build files
RUN npm run build 

#/app/build has all the executables

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
#copy all assets from build folder to nginx folder
COPY --from=builder /app/build /usr/share/nginx/html 

