#FROM node:22-bookworm-slim
#WORKDIR /app
#COPY package.json package-lock.json ./
#RUN npm ci
#COPY . .
#EXPOSE 4200
#ENTRYPOINT ["npm", "start", "--", "--host", "0.0.0.0", "--port", "4200"]



## VERIOSNE PROF. Menapace

# --> build stage

#FROM node:22-bookworm-slim AS build
#WORKDIR /app
#COPY . .
#RUN npm install
#RUN ./node_modules/.bin/ng build
#EXPOSE 4200

# --> runtime stage

#FROM nginx:1.25.2-alpine
#COPY --from=build /app/dist/frontend /usr/share/nginx/html  

#EXPOSE 80



## VERSIONE Con clone del repo

# Stage 1: Build Angular
FROM node:22-bookworm-slim AS build

RUN apt-get update \
    && apt-get install -y --no-install-recommends git ca-certificates \
    && update-ca-certificates \
    && rm -rf /var/lib/apt/lists/*


WORKDIR /app

RUN git clone https://github.com/mmenapace/SomeBankingApp.git .

WORKDIR /app/frontend

RUN npm install

RUN ./node_modules/.bin/ng build
#RUN find /app/frontend/dist -maxdepth 4 -type f -name index.html -print

FROM nginx:1.25.2-alpine

COPY --from=build /app/frontend/dist/SomeBankingFrontend/browser/ /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


# avvio frontend: docker run -d --name banking-frontend -p 4200:80 banking-frontend:1.0