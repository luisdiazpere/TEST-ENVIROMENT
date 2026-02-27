# SPL CONFIG 



 NET CONFIG 
```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: no
      addresses:
        - 10.10.110.6/24
      gateway4: 10.10.110.2
      nameservers:
        addresses:
          - 10.10.110.5
```
La ip configurade de manera estatica para evitar conflictos al momento de ingestar los datos, con el gateway aputando al firewall y el DNS proveido por el win server


UFW CONFIG


```yaml
Status: active

To                         Action      From
--                         ------      ----
514                        ALLOW       Anywhere
8000                       ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
514/udp                    ALLOW       Anywhere
9997                       ALLOW       Anywhere
514/tcp                    ALLOW       Anywhere
514 (v6)                   ALLOW       Anywhere (v6)
8000 (v6)                  ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
514/udp (v6)               ALLOW       Anywhere (v6)
9997 (v6)                  ALLOW       Anywhere (v6)
514/tcp (v6)               ALLOW       Anywhere (v6)

```

| Puerto| Motivo |
|-------|--------------|
| 514| Logs OPNsense|
| 8000| Web GUI de splunk |
| 22 | Conexion ssh  |
| 9997 | Logs de Win server  |



# SPLUNK 

La instalacion de splunk de este lab se hizo con la documentacion y videos del mismo splunk.

Instalacion en linux: https://www.youtube.com/watch?v=IvpUvqYq4cE

