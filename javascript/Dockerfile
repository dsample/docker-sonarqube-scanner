FROM openjdk:latest

RUN yum install -y curl unzip \
  && mkdir /sonar \
  && curl -sSL -o /scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.3.0.1492.zip \
  && unzip -qd /sonar/ /scanner.zip \
  && mv /sonar/*/* /sonar/ \
  && rm /scanner.zip \
  && yum erase -y unzip \
  && yum clean all \
  && useradd --user-group --create-home sonar

RUN  curl -sL https://rpm.nodesource.com/setup_12.x | bash - \
  && yum install -y --enablerepo=nodesource nodejs

WORKDIR /src
USER sonar
CMD /sonar/bin/sonar-scanner
