
docker-compose.yml

```
 networks:
   rustdesk-net:
     external: false
 services:
   rustdesk:
     ports:
       - 21114:21114
       - 21115:21115
       - 21116:21116
       - 21116:21116/udp
       - 21117:21117
       - 21118:21118
       - 21119:21119
     image: lejianwen/rustdesk-api:full-s6
     environment:
       - RELAY=<server[:21117]>
       - ENCRYPTED_ONLY=1
       - TZ=Asia/Shanghai
       - RUSTDESK_API_RUSTDESK_ID_SERVER=<server[:21116]> #21116
       - RUSTDESK_API_RUSTDESK_RELAY_SERVER=<server[:21117]> #21117
       - RUSTDESK_API_RUSTDESK_API_SERVER=http://<server[:21114]> #21114
     volumes:
       - /data/rustdesk/server:/data  #将server的key挂载出来
       - /data/rustdesk/server:/app/conf/data #挂载key文件到api容器，可以不用使用 RUSTDESK_API_RUSTDESK_KEY
       - /data/rustdesk/api:/app/data #将数据库挂载
     networks:
       - rustdesk-net
     restart: unless-stopped
```