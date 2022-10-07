FROM openjdk:11.0.16-slim
RUN mkdir -p /opt/arqui_software/logs
VOLUME /opt/arqui_software/logs
ARG DEPENDENCY=target/dependency
COPY ${DEPENDENCY}/BOOT-INF/lib /app/lib
COPY ${DEPENDENCY}/META-INF /app/META-INF
COPY ${DEPENDENCY}/BOOT-INF/classes /app
COPY wait-for-it.sh /wait-for-it.sh
RUN chmod +x /wait-for-it.sh
ENV HOST $HOST
ENV PORT $PORT
ENV DATABASE $DATABASE
ENV USER $USER
ENV PASSWORD $PASSWORD
ENTRYPOINT ["/wait-for-it.sh", "mysql:3306","--",\
            "java", \
            "-cp",                 \
            "app:app/lib/*",                 \
            "com/example/todo/TodoApplication"]

