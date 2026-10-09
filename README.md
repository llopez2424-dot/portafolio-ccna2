# Crear el diagrama y cablear acorde a la topologia.
![diagrama de topologia 1](/imgs/1-diagrama.png)
> creando la topologia

# Crear la tabla de direccionamiento


| Dispositivo / Host | Interfaz / Puerto | VLAN | Segmento Base | Dirección IP | Máscara de Subred | Gateway por Defecto |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **R1-Core** | G0/0/0.10 | 10 (Administracion) | 192.168.10.0/24 | **192.168.10.254** | 255.255.255.0 | No aplica |
| **R1-Core** | G0/0/0.20 | 20 (Laboratorio) | 192.168.20.0/24 | **192.168.20.254** | 255.255.255.0 | No aplica |
| **R1-Core** | G0/0/0.30 | 30 (Director) | 192.168.30.0/24 | **192.168.30.254** | 255.255.255.0 | No aplica |
| **R1-Core** | G0/0/0.99 | 99 (Gestión) | 192.168.99.0/24 | **192.168.99.254** | 255.255.255.0 | No aplica |
| **R1-Core** | G0/0/0.111 | 111 (Nativa) | 192.168.111.0/24 | **192.168.111.254** | 255.255.255.0 | No aplica |
| **SW-Core** | SVI (Vlan 99) | 99 (Gestión) | 192.168.99.0/24 | **192.168.99.1** | 255.255.255.0 | 192.168.99.254 |
| **SW-Lab1** | SVI (Vlan 99) | 99 (Gestión) | 192.168.99.0/24 | **192.168.99.2** | 255.255.255.0 | 192.168.99.254 |
| **SW-Lab2** | SVI (Vlan 99) | 99 (Gestión) | 192.168.99.0/24 | **192.168.99.3** | 255.255.255.0 | 192.168.99.254 |
| **PC Gestión** | Tarjeta de Red | 99 (Gestión) | 192.168.99.0/24 | **192.168.99.10** | 255.255.255.0 | 192.168.99.254 |
| **PC Admin A1-A3** | Tarjeta de Red | 10 (Administracion) | 192.168.10.0/24 | **192.168.10.1 a 192.168.10.3** | 255.255.255.0 | 192.168.10.254 |
| **PC Alumnos A1-A3** | Tarjeta de Red | 20 (Laboratorio) | 192.168.20.0/24 | **192.168.20.1 a 192.168.20.3** | 255.255.255.0 | 192.168.20.254 |
| **PC Dirección A** | Tarjeta de Red | 30 (Direccion) | 192.168.30.0/24 | **192.168.30.1** | 255.255.255.0 | 192.168.30.254 |
| **PC Admin B1-B3** | Tarjeta de Red | 10 (Administrcion) | 192.168.10.0/24 | **192.168.10.4 a 192.168.10.6** | 255.255.255.0 | 192.168.10.254 |
| **PC Alumnos B1-B3** | Tarjeta de Red | 20 (Laboratorio) | 192.168.20.0/24 | **192.168.20.4 a 192.168.20.6** | 255.255.255.0 | 192.168.20.254 |
| **PC Dirección B** | Tarjeta de Red | 30 (Direccion) | 192.168.30.0/24 | **192.168.30.2** | 255.255.255.0 | 192.168.30.254 |


```shell
sw1-dd>enable
sw1-dd>configure terminal

```
