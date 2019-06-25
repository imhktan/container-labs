FROM node:latest
# docker build
# define my environment variable
ENV APP_PORT=5000  APP_DIR=/fortune
# create APP_DIR, and cd inside
#RUN git clone https://github.com/chu/myapp.git
WORKDIR ${APP_DIR}

# copy files to APP_DIR (double dot > go up one dir)
ADD main.js .
ADD package.json .
# directories must have a target name
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
#CND [""]
#CMD ['3000']