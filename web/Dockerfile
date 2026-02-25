FROM node:18 AS base
CMD [ "bash" ]

# Build
FROM base AS build
COPY . /workspace
WORKDIR /workspace
ARG  REACT_APP_API_SERVER
RUN npm ci
RUN npm run test && npm run build

# prod
FROM nginx:latest AS production
COPY --from=build /workspace/build /var/ww
COPY nginx.conf /etc/nginx/conf.d/default.conf