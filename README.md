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


# Asignar nombre a los dispositivos con tus iniciales al final

```cisco
Switch>enable
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostname sw-core-lmlr
sw-core-lmlr(config)#end
sw-core-lmlr#
```
>cambie el nombre del switch central
```bash
S1#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)#hostname sw-lab1-lmlr
sw-lab1-lmlr(config)#end
sw-lab1-lmlr#
```
>cambie el nombre del switch uno

```bash
S2>enable
S2#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
S2(config)#hostname SW-LAB2-LMLR
SW-LAB2-LMLR(config)#END
SW-LAB2-LMLR#
```
>cambie el nombre del switch dos
```cisco
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname r1-core-lmlr
r1-core-lmlr(config)#end
r1-core-lmlr#
```
>cambie el nombre del router

# Realizar las tareas de configuracion básica de sw y router (contraseñas), y mensaje del dia.
```bash
acceso restringido - solo personal autorizado 

r1-core-lmlr>enable
Password: 
r1-core-lmlr#config
Configuring from terminal, memory, or network [terminal]? 
Enter configuration commands, one per line.  End with CNTL/Z.

# === CONFIGURACIÓN DE SEGURIDAD Y CONTRASENAS ===
r1-core-lmlr(config)#enable secret class
r1-core-lmlr(config)#service password-encryption
r1-core-lmlr(config)#banner motd % acceso restringido - solo personal autorizado %

# === CONFIGURACIÓN DE SUBINTERFACES ===
r1-core-lmlr(config)#interface g0/0.10
r1-core-lmlr(config-subif)# encapsulation dot1Q 10
r1-core-lmlr(config-subif)# ip address 192.168.10.254 255.255.255.0
r1-core-lmlr(config-subif)# exit
r1-core-lmlr(config)#
%LINK-3-UPDOWN: Interface GigabitEthernet0/0/0.10, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0.10, changed state to up

r1-core-lmlr(config)#interface g0/0.20
r1-core-lmlr(config-subif)# encapsulation dot1Q 20
r1-core-lmlr(config-subif)# ip address 192.168.20.254 255.255.255.0
r1-core-lmlr(config-subif)# exit
r1-core-lmlr(config)#
%LINK-3-UPDOWN: Interface GigabitEthernet0/0/0.20, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0.20, changed state to up

r1-core-lmlr(config)#interface g0/0.30
r1-core-lmlr(config-subif)# encapsulation dot1Q 30
r1-core-lmlr(config-subif)# ip address 192.168.30.254 255.255.255.0
r1-core-lmlr(config-subif)# exit
%LINK-3-UPDOWN: Interface GigabitEthernet0/0.30, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0.30, changed state to up

r1-core-lmlr(config)#interface go/0.99
                                ^
% Invalid input detected at '^' marker.
	
r1-core-lmlr(config)#interface g0/0.30
r1-core-lmlr(config-subif)# encapsulation dot1Q 30
r1-core-lmlr(config-subif)# ip address 192.168.30.254 255.255.255.0
r1-core-lmlr(config-subif)# exit
r1-core-lmlr(config)#interface g0/0.99
r1-core-lmlr(config-subif)# encapsulation dot1Q 99
r1-core-lmlr(config-subif)# ip address 192.168.99.254 255.255.255.0
r1-core-lmlr(config-subif)# exit
r1-core-lmlr(config)#interface g0/0.111
r1-core-lmlr(config-subif)# encapsulation dot1Q 111 native
r1-core-lmlr(config-subif)# ip address 192.168.111.254 255.255.255.0
r1-core-lmlr(config-subif)# exit
%LINK-3-UPDOWN: Interface GigabitEthernet0/0/0.99, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0.99, changed state to up

%LINK-3-UPDOWN: Interface GigabitEthernet0/0/0.111, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0.111, changed state to up
```

# Crear las VLANs


```cisco
Switch>enable
Switch#configure terminal
Switch(config)#vlan 10
Switch(config-vlan)#administrativos
Switch(config-vlan)#exit
```

```cisco
Switch>enable
Switch#configure terminal
Switch(config)#vlan 20
Switch(config-vlan)#name alumnos
Switch(config-vlan)#exit
```
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#vlan 30
Switch(config-vlan)#name direccion
Switch(config-vlan)#exit
```
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#vlan 99
Switch(config-vlan)#name gestion
Switch(config-vlan)#exit
```
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#vlan 111
Switch(config-vlan)#name nativa
Switch(config-vlan)#exit
```

