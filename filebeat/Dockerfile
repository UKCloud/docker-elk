FROM bobbydvo/ukc_nginx:latest

COPY docker-entrypoint.sh /docker-entrypoint.sh
COPY binary/filebeat /filebeat
COPY filebeat.yml /filebeat.yml
RUN rm /var/log/nginx/access.log
RUN rm /var/log/nginx/error.log
RUN touch /var/log/nginx/access.log
RUN touch /var/log/nginx/error.log
RUN chown nginx:nginx /var/log/nginx/access.log
RUN chown nginx:nginx /var/log/nginx/error.log

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["/filebeat", "-e", "-d", "*", "/filebeat.yml"]