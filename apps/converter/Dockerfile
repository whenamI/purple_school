FROM node:13 as build
WORKDIR /opt/app
ADD *.json ./
RUN npm install --legacy-peer-deps
ADD . .
RUN npm run build converter

FROM node:13
WORKDIR /opt/app
ADD package.json ./
RUN npm install --only=prod --legacy-peer-deps
COPY --from=build /opt/app/dist/apps/converter ./dist
CMD ["node", "./dist/main.js"]