FROM java:7
MAINTAINER Manuel de la Peña <manuel.delapenya@liferay.com>

RUN apt-get update

ENV LIFERAY_HOME /usr/local/liferay-portal-7.0-ce-b7

RUN mkdir -p "$LIFERAY_HOME"

ENV CATALINA_HOME $LIFERAY_HOME/tomcat-8.0.30

ENV PATH $CATALINA_HOME/bin:$PATH

ENV LIFERAY_TOMCAT_URL https://sourceforge.net/projects/lportal/files/Liferay%20Portal/7.0.0%20B7/liferay-portal-tomcat-7.0-ce-b7-20160210093853489.zip/download

WORKDIR /usr/local

RUN set -x \
			&& curl -fSL "$LIFERAY_TOMCAT_URL" -o liferay-portal-tomcat-7.0-ce-b7-20160210093853489.zip \
			&& unzip liferay-portal-tomcat-7.0-ce-b7-20160210093853489.zip \
			&& rm liferay-portal-tomcat-7.0-ce-b7-20160210093853489.zip

ADD ./configs/setenv.sh $CATALINA_HOME/bin/setenv.sh

EXPOSE 8080/tcp
EXPOSE 11311/tcp

CMD ["catalina.sh", "run"]