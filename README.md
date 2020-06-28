# keycloak-ha

Dockerfile for keycloak ha

## Use MySQL
### Run keycloak1
```
docker run -d --name keycloak1 --restart=always \
    -p 8080:8080 \
    -p 8443:8443 \
    -p 8009:8009 \
    -p 9990:9990 \
    -p 7600:7600 \
    -p 57600:57600 \
    -e KEYCLOAK_USER=admin \
    -e KEYCLOAK_PASSWORD=admin \
    -e DB_VENDOR=mysql \
    -e DB_ADDR=localhost \
    -e DB_PORT=3306 \
    -e DB_DATABASE=keycloak \
    -e DB_USER=keycloak \
    -e DB_PASSWORD=password \
    -e JGROUPS_DISCOVERY_PROTOCOL=JDBC_PING \
    -e JGROUPS_DISCOVERY_EXTERNAL_IP=172.31.72.101 \
    -e PROXY_ADDRESS_FORWARDING=true \
    -e KEYCLOAK_FRONTEND_URL=https://your-domain/auth \
    vigoz/keycloak-ha:10.0.2
```

### Run keycloak2
```
docker run -d --name keycloak2 --restart=always \
    -p 8080:8080 \
    -p 8443:8443 \
    -p 8009:8009 \
    -p 9990:9990 \
    -p 7600:7600 \
    -p 57600:57600 \
    -e KEYCLOAK_USER=admin \
    -e KEYCLOAK_PASSWORD=admin \
    -e DB_VENDOR=mysql \
    -e DB_ADDR=localhost \
    -e DB_PORT=3306 \
    -e DB_DATABASE=keycloak \
    -e DB_USER=keycloak \
    -e DB_PASSWORD=password \
    -e JGROUPS_DISCOVERY_PROTOCOL=JDBC_PING \
    -e JGROUPS_DISCOVERY_EXTERNAL_IP=172.31.72.102 \
    -e PROXY_ADDRESS_FORWARDING=true \
    -e KEYCLOAK_FRONTEND_URL=https://your-domain/auth \
    vigoz/keycloak-ha:10.0.2
```

## Use PostgreSQL
### Run keycloak1
```
docker run -d --name keycloak1 --restart=always \
    -p 8080:8080 \
    -p 8443:8443 \
    -p 8009:8009 \
    -p 9990:9990 \
    -p 7600:7600 \
    -p 57600:57600 \
    -e KEYCLOAK_USER=admin \
    -e KEYCLOAK_PASSWORD=admin \
    -e DB_VENDOR=postgres \
    -e DB_ADDR=localhost \
    -e DB_PORT=5432 \
    -e DB_DATABASE=keycloak \
    -e DB_SCHEMA=public \
    -e DB_USER=keycloak \
    -e DB_PASSWORD=password \
    -e JGROUPS_DISCOVERY_PROTOCOL=JDBC_PING \
    -e JGROUPS_DISCOVERY_EXTERNAL_IP=172.31.72.101 \
    -e PROXY_ADDRESS_FORWARDING=true \
    -e KEYCLOAK_FRONTEND_URL=https://your-domain/auth \
    vigoz/keycloak-ha:10.0.2-postgres
```

### Run keycloak2
```
docker run -d --name keycloak2 --restart=always \
    -p 8080:8080 \
    -p 8443:8443 \
    -p 8009:8009 \
    -p 9990:9990 \
    -p 7600:7600 \
    -p 57600:57600 \
    -e KEYCLOAK_USER=admin \
    -e KEYCLOAK_PASSWORD=admin \
    -e DB_VENDOR=postgres \
    -e DB_ADDR=localhost \
    -e DB_PORT=5432 \
    -e DB_DATABASE=keycloak \
    -e DB_SCHEMA=public \
    -e DB_USER=keycloak \
    -e DB_PASSWORD=password \
    -e JGROUPS_DISCOVERY_PROTOCOL=JDBC_PING \
    -e JGROUPS_DISCOVERY_EXTERNAL_IP=172.31.72.102 \
    -e PROXY_ADDRESS_FORWARDING=true \
    -e KEYCLOAK_FRONTEND_URL=https://your-domain/auth \
    vigoz/keycloak:10.0.2-postgres
```