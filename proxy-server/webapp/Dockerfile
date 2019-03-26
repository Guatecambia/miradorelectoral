# build stage
FROM jekyll/jekyll:latest as build-stage
WORKDIR /app
COPY . .
RUN JEKYLL_ENV=production jekyll build

# production stage
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/_site /usr/share/nginx/html
CMD ["nginx"]
EXPOSE 80 443
