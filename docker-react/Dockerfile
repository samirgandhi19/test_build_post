FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

#each block can only have one FROM statement
# so a new FROM ends the previous
FROM nginx as run
EXPOSE 80
COPY --from=builder /app/build /usr/share/nginx/html