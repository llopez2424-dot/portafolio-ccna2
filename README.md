# Crear el diagrama y cablear acorde a la topologia.
![diagrama de topologia 1](/imgs/1-diagrama.png)
> creando la topologia

# Crear la tabla de direccionamiento

| Dispositivo / Interfaz | VLAN | Segmento de Red Base | Dirección IP a Calcular / Configurar | Máscara de Subred | Gateway por Defecto |
|---|---:|---|---|---|---|
| R1-Core-ELO (G0/0/0.10) | 10 | 192.168.10.0/24 | 192.168.10.254 | 255.255.255.0 | No aplica |
| R1-Core-ELO (G0/0/0.10) | 20 | 192.168.10.0/24 | 192.168.10.254 | 255.255.255.0 | No aplica |
| R1-Core-ELO (G0/0/0.10) | 30 | 192.168.10.0/24 | 192.168.10.254 | 255.255.255.0 | No aplica |
| R1-Core-ELO (G0/0/0.10) | 10 | 192.168.10.0/24 | 192.168.10.254 | 255.255.255.0 | No aplica |



```shell
sw1-dd>enable
sw1-dd>configure terminal

```
