# Base image from which we are pulling from
FROM node:latest

# define some environment variables
ENV DB_HOST=localhost DB_PORT=3306 DB_USER=root DB_PASSWORD=changeit APP_PORT=3000 APP_ROOT=/app

#Create app directory and go inside the directory
WORKDIR ${APP_ROOT}

COPY . .

RUN npm install

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT ["node", "main.js"]