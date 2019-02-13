# nginx com arquivos estáticos
```
FROM nginx
COPY static-videos /usr/share/nginx/html
```
# azul/zulu-openjdk-alpine:8 com jar Spring Boot
```
FROM azul/zulu-openjdk-alpine:8

RUN export JAVA_OPTS="-server -d64 -Xms512m -Xmx512m -XX:MetaspaceSize=512m -XX:MaxMetaspaceSize=512m -Xmn128m" && \
export JAVA_OPTS="$JAVA_OPTS -XX:SurvivorRatio=4 -XX:+UseConcMarkSweepGC -XX:+CMSParallelRemarkEnabled" && \
export JAVA_OPTS="$JAVA_OPTS -XX:+UseCMSInitiatingOccupancyOnly -XX:CMSInitiatingOccupancyFraction=10" && \
export JAVA_OPTS="$JAVA_OPTS -XX:+ScavengeBeforeFullGC -XX:+CMSScavengeBeforeRemark" && \
export JAVA_OPTS="$JAVA_OPTS -Djava.security.egd=file:/dev/./urandom" && \
export JAVA_OPTS="$JAVA_OPTS -Duser.language=pt -Duser.country=BR -Duser.timezone=America/Sao_Paulo"

# ADD painel-publicacao-web.jar /app.jar
ADD target/gs-spring-boot-0.1.0.jar /app.jar

EXPOSE 8080

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar /app.jar" ]
```
