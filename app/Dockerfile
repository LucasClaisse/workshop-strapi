FROM node

WORKDIR /app

COPY . .

EXPOSE 1337

RUN npm install strapi -g
RUN npm install
CMD ["strapi", "develop"]
