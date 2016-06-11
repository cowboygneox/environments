FROM java:8
RUN mkdir /install
WORKDIR /install
RUN wget https://downloads.typesafe.com/typesafe-activator/1.3.10/typesafe-activator-1.3.10-minimal.zip
RUN unzip typesafe-activator-1.3.10-minimal.zip
WORKDIR activator-1.3.10-minimal/bin

RUN ./activator new play-scala-app play-scala
WORKDIR play-scala-app
RUN bin/activator test

WORKDIR /install/activator-1.3.10-minimal/bin

RUN ./activator new play-java-app play-java
WORKDIR play-java-app
RUN bin/activator test

WORKDIR /

RUN rm -r /install/activator-1.3.10-minimal/bin/play-scala-app
RUN rm -r /install/activator-1.3.10-minimal/bin/play-java-app

ENV PATH /install/activator-1.3.10-minimal/bin:$PATH

CMD ["activator", "test"]
