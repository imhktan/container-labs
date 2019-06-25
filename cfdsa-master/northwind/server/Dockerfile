#  base 
FROM node:latest
# define my environment variable
ENV  DB_HOST=nwdb DB_PORT=3306 \
     DB_USER=root DB_PASSWORD=changeit \
     APP_PORT=3000  APP_DIR=/app
# create APP_DIR, and cd inside
WORKDIR ${APP_DIR}

# copy files to APP_DIR (double dot > go up one dir)
ADD main.js .
ADD package.json .
# directories must have a target name
ADD config config
ADD public public
ADD views views

# install libraries from package.json
RUN npm install

## docker run
## expose is for documentation only
EXPOSE ${APP_PORT}
# \ is for break the line
HEALTHCHECK --interval=60s  --timeout=5s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT} || exit 1
# how should the image be executed (entry point is fixed CMD is optional)
ENTRYPOINT [ "node", "main.js" ] 