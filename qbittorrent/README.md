run daemon :

```
docker run --name bittorrent -d \
-p 8080:8080 \
-v $PWD/config:/root/.config/qBittorrent \
-v $PWD/data:/root/.local/share/data/qBittorrent \
-v $PWD/Downloads:/root/Downloads \
local/qbittorrent qbittorrent-nox 
```
