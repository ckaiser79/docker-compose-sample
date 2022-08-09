FROM quay.io/wildfly/wildfly

#COPY rundeck-adapter.war /root/rundeck-adapter.war
RUN mkdir /opt/jboss/jboss-setup
COPY logging.cfg /opt/jboss/jboss-setup/logging.cfg

RUN /opt/jboss/wildfly/bin/add-user.sh --user admin --password admin --realm "ManagementRealm" --silent
# && \
#    cd /opt/jboss/wildfly/bin/ && \
#    ./jboss-cli.sh --file=/opt/jboss/jboss-setup/logging.cfg

CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
