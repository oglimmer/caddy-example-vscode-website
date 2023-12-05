FROM node as build

COPY my-app /opt/app

WORKDIR /opt/app

RUN npm ci && npm run build

FROM node

WORKDIR /opt/app

COPY --from=build /opt/app/build/ ./build/
COPY --from=build /opt/app/package.json .
COPY --from=build /opt/app/package-lock.json .

RUN npm ci --omit dev

EXPOSE 3000

CMD ["node", "build"]