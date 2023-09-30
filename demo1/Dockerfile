FROM sudhirkr92/java-soapui-base
WORKDIR /opt/app
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline
COPY ./src ./src
RUN ./mvnw clean install
#COPY ./target/*.jar /opt/app/*.jar
CMD PWD
COPY ./target/*.jar /opt/app/*.jar
COPY ./soapui/AccountDetails.xml /opt/app/AccountDetails.xml
EXPOSE 8090 8088
CMD /opt/SoapUI-5.2.0/bin/mockservicerunner.sh -p 8088 /opt/app/AccountDetails.xml & java -jar /opt/app/*.jar
