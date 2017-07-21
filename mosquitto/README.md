## Mosquitto broker
### Description
This is custom mosquitto_v1.4.12 docker image based on alpine 3.5.

Mosquitto uses self signed certificates to use secure connection. All certificates and info are located in ``all_certs`` directory.
Also user/password authentication is used with TLS (Check custom conf.d/mosquitto_ssl.conf : `` allow_anonymous false `` `` password_file /mosquitto/passwd ``). Username and password: `` mosquitto:mosquitto `` are located in `` passwd `` file.



### Usage
Build docker image:
```
docker build -t mosquitto .
```

Run docker container in backgroud:
```
docker run -d -p8883:8883 mosquitto
```
or iteractive mode
```
docker run -it -p8883:8883 mosquitto
```
Connect broker on port 8883 using:
```
mosquitto_ca.crt
mosquitto_client.key
mosquitto_client.crt
username: mosquitto
password: mosquitto
```

### Customization
- Put all your custom config files into ``conf.d`` directory.
- Put your own generated certs into `` certs `` directory or use existing one.
- You can generate your own username and password using `` mosquitto_passwd `` utility.

#### mosquitto_passwd usage

``mosquitto_passwd`` is a tool for managing password files for mosquitto.

```
Usage: mosquitto_passwd [-c | -D] passwordfile username
       mosquitto_passwd -b passwordfile username password
       mosquitto_passwd -U passwordfile
 -b : run in batch mode to allow passing passwords on the command line.
 -c : create a new password file. This will overwrite existing files.
 -D : delete the username rather than adding/updating its password.
 -U : update a plain text password file to use hashed passwords.
```
See http://mosquitto.org/ for more information.
