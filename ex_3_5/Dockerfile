FROM node:alpine as build-stage

RUN adduser -D app

RUN mkdir -p frontend
RUN chown app /frontend

WORKDIR /frontend
COPY frontend ./

RUN apk update && apk add bash && \
	apk add --no-cache curl && \
	npm install && npm install -g serve && npm install -g webpack webpack-cli
	#apk del curl
	#apt-get purge -y --auto-remove curl && \
	#rm -rf /var/lib/apt/lists/*

USER app


FROM node:alpine
COPY --from=build-stage /frontend/ /dist

ENV API_URL=http://localhost:8000
EXPOSE 5000



RUN npm install --global serve
CMD ["serve"]