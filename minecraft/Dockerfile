FROM java
MAINTAINER Thomas Charlat "thomas.charlat@gmail.com"

RUN wget https://s3.amazonaws.com/Minecraft.Download/versions/1.9.4/minecraft_server.1.9.4.jar

VOLUME /src
WORKDIR /src

CMD java -Xmx1024M -Xms1024M -d64 -jar /minecraft_server.1.9.4.jar nogui
