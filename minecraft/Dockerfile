FROM java
MAINTAINER Thomas Charlat "thomas.charlat@gmail.com"
RUN wget https://s3.amazonaws.com/Minecraft.Download/versions/1.9/minecraft_server.1.9.jar
VOLUME /src
WORKDIR /src
CMD java -Xmx1024M -Xms1024M -jar /minecraft_server.jar nogui
