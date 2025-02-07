FROM node:14-alpine AS development
WORKDIR /opt/app
COPY *.json ./
RUN npm install
COPY . .
RUN npm run build api

FROM node:14-alpine AS production
WORKDIR /opt/app
COPY *.json ./
RUN npm install --only=production
COPY --from=development /opt/app/dist/apps/api ./dist
CMD [ "node", "dist/main.js" ]

