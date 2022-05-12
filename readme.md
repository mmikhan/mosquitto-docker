# Mosquitto on Docker Container
The `docker-compose.yml` file includes a basic installation of Mosquitto on a Docker container. Clone the repository and follow the given steps below:
1. Start container: `docker compose up -d`. Three new directories (`config`, `data`, `log`) will be created.
2. Get into the relevant container: `docker exec -it mqtt sh`.
3. Generate authentication file: `mosquitto_passwd -c /mosquitto/config/auth username`. Replace the `username` with your own.
4. Enter the password once prompt.
5. Create a configuration file: `touch config/mosquitto.conf` with the following configurations:
```
persistence true
persistence_location /mosquitto/data/
log_dest file /mosquitto/log/mosquitto.log
allow_anonymous false
password_file /mosquitto/config/pwfile
listener 1883
listener 9001
protocol websockets
```
6. Restart Docker container: `docker compose restart`
7. Test the connection using [MQTTX](https://mqttx.app/) or your preferred MQTT client.
8. Fill up the username, password, and use `localhost` as the Host with `mqtt://` prefix.
9. Create a new subscription on the client and send a message to the relevant topic to test.

> If you prefer a video guide, head to the [YouTube video](https://youtu.be/U8f95agyUJg) that I published for everyone.

## Resources
1. https://youtu.be/L26JY2NH-Ys
2. https://youtu.be/Bz2JYxbkmuY
3. https://hub.docker.com/_/eclipse-mosquitto
4. https://mosquitto.org/man/mosquitto-conf-5.html
5. https://github.com/eclipse/mosquitto
6. https://raw.githubusercontent.com/eclipse/mosquitto/master/mosquitto.conf
