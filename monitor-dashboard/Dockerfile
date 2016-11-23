FROM java:8-jre

ENV VERTICLE_FILE target/monitor-dashboard-fat.jar

# Set the location of the verticles
ENV VERTICLE_HOME /opt/verticles

EXPOSE 9100

COPY $VERTICLE_FILE $VERTICLE_HOME/
COPY src/config/docker.json $VERTICLE_HOME/

WORKDIR $VERTICLE_HOME
ENTRYPOINT ["sh", "-c"]
CMD ["java -Dvertx.logger-delegate-factory-class-name=io.vertx.core.logging.SLF4JLogDelegateFactory -Dvertx.metrics.options.enabled=true -jar monitor-dashboard-fat.jar -Dvertx.disableDnsResolver=true -cluster -conf docker.json"]
