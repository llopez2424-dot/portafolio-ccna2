# Crear el diagrama y cablear acorde a la topologia.
![diagrama de topologia 1](/imgs/1-diagrama.png)
> creando la topologia

# Crear la tabla de direccionamiento
### Tabla A: Dispositivos Intermedios (Routers y Switches)

| Dispositivo / Interfaz | VLAN | Segmento de Red Base | Dirección IP a Calcular / Configurar | Máscara de Subred | Gateway por Defecto |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R1-Core (G0/0/0.10)** | 10 | 192.168.10.0/24 | **192.168.10.254** | 255.255.255.0 | No aplica |
| **R1-Core (G0/0/0.20)** | 20 | 192.168.20.0/24 | **192.168.20.254** | 255.255.255.0 | No aplica |
| **R1-Core (G0/0/0.30)** | 30 | 192.168.30.0/24 | **192.168.30.254** | 255.255.255.0 | No aplica |
| **R1-Core (G0/0/0.99)** | 99 | 192.168.99.0/24 | **192.168.99.254** | 255.255.255.0 | No aplica |
| **R1-Core (G0/0/0.111)** | 111 | 192.168.111.0/24 | **192.168.111.254** | 255.255.255.0 | No aplica |
| **SW-Core (SVI VLAN 99)** | 99 | 192.168.99.0/24 | **192.168.99.1** | 255.255.255.0 | 192.168.99.254 |
| **SW-Lab1 (SVI VLAN 99)** | 99 | 192.168.99.0/24 | **192.168.99.2** | 255.255.255.0 | 192.168.99.254 |
| **SW-Lab2 (SVI VLAN 99)** | 99 | 192.168.99.0/24 | **192.168.99.3** | 255.255.255.0 | 192.168.99.254 |

### Tabla B: Dispositivos Finales (PCs de Usuario y Gestión)

| Dispositivo Final | Puerto del Switch | VLAN | Dirección IP (Formato CIDR) | Gateway por Defecto |
| :--- | :--- | :--- | :--- | :--- |
| **PC-Gestion** | SW-Core -> Fa0/9 | 99 | **192.168.99.10/24** | 192.168.99.254 |
| **PC-Admin-A1** | SW-Lab1 -> Fa0/1 | 10 | **192.168.10.1/24** | 192.168.10.254 |
| **PC-Admin-A2** | SW-Lab1 -> Fa0/2 | 10 | **192.168.10.2/24** | 192.168.10.254 |
| **PC-Admin-A3** | SW-Lab1 -> Fa0/3 | 10 | **192.168.10.3/24** | 192.168.10.254 |
| **PC-Alumnos-A1** | SW-Lab1 -> Fa0/4 | 20 | **192.168.20.1/24** | 192.168.20.254 |
| **PC-Alumnos-A2** | SW-Lab1 -> Fa0/5 | 20 | **192.168.20.2/24** | 192.168.20.254 |
| **PC-Alumnos-A3** | SW-Lab1 -> Fa0/6 | 20 | **192.168.20.3/24** | 192.168.20.254 |
| **PC-Direccion-A** | SW-Lab1 -> Fa0/7 | 30 | **192.168.30.1/24** | 192.168.30.254 |
| **PC-Admin-B1** | SW-Lab2 -> Fa0/1 | 10 | **192.168.10.4/24** | 192.168.10.254 |
| **PC-Admin-B2** | SW-Lab2 -> Fa0/2 | 10 | **192.168.10.5/24** | 192.168.10.254 |
| **PC-Admin-B3** | SW-Lab2 -> Fa0/3 | 10 | **192.168.10.6/24** | 192.168.10.254 |
| **PC-Alumnos-B1** | SW-Lab2 -> Fa0/4 | 20 | **192.168.20.4/24** | 192.168.20.254 |
| **PC-Alumnos-B2** | SW-Lab2 -> Fa0/5 | 20 | **192.168.20.5/24** | 192.168.20.254 |
| **PC-Alumnos-B3** | SW-Lab2 -> Fa0/6 | 20 | **192.168.20.6/24** | 192.168.20.254 |
| **PC-Direccion-B** | SW-Lab2 -> Fa0/7 | 30 | **192.168.30.2/24** | 192.168.30.254 |



```shell
sw1-dd>enable
sw1-dd>configure terminal

```
