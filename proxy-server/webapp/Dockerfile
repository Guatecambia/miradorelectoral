# build stage
FROM jekyll/builder:latest as build-stage
WORKDIR /tmp
COPY . .
RUN JEKYLL_ENV=production jekyll build

# production stage
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /tmp/_site /usr/share/nginx/html
CMD ["nginx"]
EXPOSE 80 443
