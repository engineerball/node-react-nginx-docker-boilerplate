FROM public.ecr.aws/docker/library/node:alpine as builder
WORKDIR /app
COPY package*.json ./
RUN npm install --silent
COPY . ./
RUN npm run build

FROM public.ecr.aws/nginx/nginx:latest
EXPOSE 3000
COPY nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
