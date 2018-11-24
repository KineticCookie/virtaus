FROM nginx:1.15-alpine

ADD config/default.conf.template /etc/nginx/conf.d/default.conf.template

ENV BACKEND_HOST=localhost
ENV FRONTEND_HOST=localhost

EXPOSE 9091

CMD envsubst '${BACKEND_HOST} ${FRONTEND_HOST}' < /etc/nginx/conf.d/default.conf.template > /etc/nginx/conf.d/default.conf \
 && cat /etc/nginx/conf.d/default.conf \
&& exec nginx -g 'daemon off;'
