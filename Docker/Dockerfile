FROM ibmcom/websphere-traditional:latest

USER root

RUN mkdir /demo && chown was /demo

USER was
RUN mkdir /demo/db2drivers
COPY db2drivers/db2jcc.jar /demo/db2drivers
COPY db2drivers/db2jcc_license_cu.jar /demo/db2drivers


COPY CustomerOrderServicesApp-0.1.0-SNAPSHOT.ear /demo/
#COPY transformationadvisor-2.1_Linux_Demo1.tgz.part* /demo/

WORKDIR "/demo"
#RUN cat transformationadvisor-2.1_Linux_Demo1.tgz.part? > transformationadvisor-2.1_Linux_Demo1.tgz
#RUN tar xvfz transformationadvisor-2.1_Linux_Demo1.tgz
#COPY customCmd.properties /demo/transformationadvisor-2.0.1/conf/

COPY PASSWORD /tmp/PASSWORD
ENV pwd=passw0rd
RUN echo $pwd

RUN wsadmin.sh -lang jython -f /demo/wsadmin.py -conntype NONE -username wsadmin -password passw0rd
