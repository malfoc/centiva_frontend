FROM node:latest

WORKDIR /app

COPY . /app

RUN npm install -g @vue/cli
# RUN npm install
# RUN npm install -g livereload
# RUN npm run build

EXPOSE 8080

# CMD ["npm", "run", "serve"]
ENTRYPOINT ["tail", "-f", "/dev/null"]