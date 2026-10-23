# 1._Crear el diagrama y cablear acorde a la topologia.
![diagrama de topologia 1](/imgs/1-diagrama.png)
> creando la topologia

# 2._Crear la tabla de direccionamiento
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


# 3._Asignar nombre a los dispositivos con tus iniciales al final

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

# 4._Realizar las tareas de configuracion básica de sw y router (contraseñas), y mensaje del dia.


## sw-core-lmlr

```text
enable
configure terminal
hostname sw-core-lmlr
enable secret Cisco123
service password-encryption

line console 0
 password Consola123
 login
 exit

line vty 0 4
 password Remoto123
 login
 exit

banner motd # ACCESO SOLO A PERSONAL AUTORIZADO #

end
copy running-config startup-config
```

## sw-lab1-lmlr

```text
enable
configure terminal
hostname sw-lab1-lmlr
enable secret Cisco123
service password-encryption

line console 0
 password Consola123
 login
 exit

line vty 0 4
 password Remoto123
 login
 exit

banner motd # ACCESO SOLO A PERSONAL AUTORIZADO #

end
copy running-config startup-config
```
## sw-lab-2 lmlr

```text
enable
configure terminal
hostname sw-lab2-lmlr
enable secret Cisco123
service password-encryption

line console 0
 password Consola123
 login
 exit

line vty 0 4
 password Remoto123
 login
 exit

banner motd # ACCESO SOLO A PERSONAL AUTORIZADO #

end
copy running-config startup-config
```





## configuracion router

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

# 5._Crear las VLANs


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
```cisco
Switch>enable
Switch#configure terminal
Switch(config)#vlan 999
Switch(config-vlan)#name Blackhole
Switch(config-vlan)#exit
```
# 6._Asignar los puertos a las VLANS
## sw-core-lmlr
``` interface fa0/9
 switchport mode access
 switchport access vlan 99
 no shutdown
 exit
```
## sw-lab1-lmlr
interface range fa0/1-3
 switchport mode access
 switchport access vlan 10
 no shutdown
 exit

interface range fa0/4-6
 switchport mode access
 switchport access vlan 20
 no shutdown
 exit

interface fa0/7
 switchport mode access
 switchport access vlan 30
 no shutdown
 exit
```
> se hace eso con los sw1 y sw2

````

# 7._Verificación de la Configuración de VLANs — TechCorp

## Objetivo
Verificar que las VLAN estén configuradas correctamente en los switches y comprobar el estado de los puertos y enlaces troncales de la red.

## 1. VLAN configuradas

| VLAN | Nombre | Función |
|---|---|---|
| 10 | ADMINISTRACION | Equipos de administración |
| 20 | LABORATORIOS | Equipos de laboratorio |
| 30 | DIRECCION | Equipos de dirección |
| 99 | GESTION | Administración de switches |
| 111 | NATIVA | VLAN nativa de los enlaces troncales |
| 999 | BLACKHOLE | Puertos no utilizados |

## 2. Comandos para verificar las VLAN

### Ver las VLAN creadas
```cisco
show vlan brief
```

### Verificar los enlaces troncales
```cisco
show interfaces trunk
```

### Verificar el estado de los puertos
```cisco
show interfaces status
```

### Verificar la configuración de un puerto específico
```cisco
show interfaces fastEthernet 0/10 switchport
```

### Revisar la configuración actual del switch
```cisco
show running-config
```

## 3. Verificar las interfaces del router

```cisco
show ip interface brief
```

Este comando permite revisar las interfaces, las direcciones IP y su estado.

## 4. Asignación de puertos en SW-LAB1-LMLR

| Puertos | VLAN | Función |
|---|---|---|
| Fa0/1 - Fa0/3 | 10 | Administración |
| Fa0/4 - Fa0/6 | 20 | Laboratorios |
| Fa0/7 | 30 | Dirección |
| Fa0/8 - Fa0/24 | 999 | Puertos reservados o no utilizados |
| Gig0/1 - Gig0/2 | 999 | Puertos reservados o no utilizados |


## 5. Resultado esperado

- Las VLAN aparecen con estado `active`.
- Los equipos están conectados a la VLAN correspondiente.
- Los enlaces troncales permiten las VLAN necesarias.
- La VLAN nativa de los enlaces troncales es la VLAN 111.
- Las interfaces del router están activas y tienen las direcciones IP correspondientes.

````

# 8._Habilitar los enlaces troncales.


## 1. Configuración del switch principal (SW-Core-LMLR)

```cisco
enable
configure terminal

interface fastEthernet 0/10
 switchport mode trunk
 switchport trunk native vlan 111
 switchport trunk allowed vlan 10,20,30,99,111
 no shutdown
exit

interface fastEthernet 0/11
 switchport mode trunk
 switchport trunk native vlan 111
 switchport trunk allowed vlan 10,20,30,99,111
 no shutdown
exit

end
copy running-config startup-config
```

## 2. Configuración del switch de laboratorios 1 (SW-LAB1-LMLR)

```cisco
enable
configure terminal

interface fastEthernet 0/10
 switchport mode trunk
 switchport trunk native vlan 111
 switchport trunk allowed vlan 10,20,30,99,111
 no shutdown
exit

end
copy running-config startup-config
```

## 3. Configuración del switch de laboratorios 2 (SW-LAB2-LMLR)

```cisco
enable
configure terminal

interface fastEthernet 0/11
 switchport mode trunk
 switchport trunk native vlan 111
 switchport trunk allowed vlan 10,20,30,99,111
 no shutdown
exit

end
copy running-config startup-config
```

## 4. Verificar los enlaces troncales

Ejecutar en cada switch:

```cisco
show interfaces trunk
```

También se puede revisar el estado de los puertos:

```cisco
show interfaces status
```


# 9._Verificación de Enlaces Troncales — TechCorp



## 1. Verificar los enlaces troncales

Ejecutar el siguiente comando en cada switch:

```cisco
show interfaces trunk
```

Este comando muestra los puertos en modo troncal, la VLAN nativa y las VLAN permitidas.

## 2. Verificar la configuración de un puerto

```cisco
show interfaces fastEthernet 0/10 switchport
```

Este comando permite revisar el modo del puerto y su configuración de VLAN.

## 3. Verificar las VLAN permitidas

```cisco
show interfaces trunk
```

Comprobar que estén permitidas las siguientes VLAN:

- VLAN 10: ADMINISTRACION
- VLAN 20: LABORATORIOS
- VLAN 30: DIRECCION
- VLAN 99: GESTION
- VLAN 111: NATIVA

## 4. Verificar el estado de los puertos

```cisco
show interfaces status
```

El puerto debe estar conectado si tiene un cable funcional conectado al otro dispositivo.

## 5. Resultado esperado

- Los puertos troncales deben aparecer en estado `trunking`.
- La VLAN nativa debe ser la VLAN 111.
- Las VLAN permitidas deben ser 10, 20, 30, 99 y 111.
- Los enlaces deben estar conectados correctamente en ambos extremos.



< La verificación de los enlaces troncales permite comprobar que los switches puedan transportar el tráfico de las diferentes VLAN a través de sus conexiones. Esto ayuda a detectar errores de configuración y mantener la comunicación de la red TechCorp.


# 9._ Guardar la Configuración 


## 1. Guardar la configuración en los switches

Ejecutar en cada switch: SW-Core-LMLR, SW-LAB1-LMLR y SW-LAB2-LMLR.

```cisco
enable
copy running-config startup-config
```

Cuando aparezca el mensaje:

```text
Destination filename [startup-config]?
```

Presionar **Enter** para confirmar.

## 2. Guardar la configuración en el router

Ejecutar en el router R1-Core-LMLR:

```cisco
enable
copy running-config startup-config
```

Presionar **Enter** para confirmar el nombre del archivo de destino si el equipo lo solicita.

## 3. Verificar que la configuración se guardó

Para revisar la configuración activa:

```cisco
show running-config
```

Para revisar la configuración guardada:

```cisco
show startup-config
```


# 10._ Configuración de Subinterfaces en el Router — TechCorp


## 1. Configuración del router R1-Core-LMLR

```cisco
enable
configure terminal

interface gigabitEthernet 0/0
 no shutdown
exit

interface gigabitEthernet 0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.254 255.255.255.0
exit

interface gigabitEthernet 0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.254 255.255.255.0
exit

interface gigabitEthernet 0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.254 255.255.255.0
exit

interface gigabitEthernet 0/0.99
 encapsulation dot1Q 99
 ip address 192.168.99.254 255.255.255.0
exit

interface gigabitEthernet 0/0.111
 encapsulation dot1Q 111 native
 ip address 192.168.111.254 255.255.255.0
exit

end
copy running-config startup-config
```

## 2. Direcciones IP de las subinterfaces

| Subinterfaz | VLAN | Dirección IP | Máscara |
|---|---:|---|---|
| G0/0.10 | 10 | 192.168.10.254 | 255.255.255.0 |
| G0/0.20 | 20 | 192.168.20.254 | 255.255.255.0 |
| G0/0.30 | 30 | 192.168.30.254 | 255.255.255.0 |
| G0/0.99 | 99 | 192.168.99.254 | 255.255.255.0 |
| G0/0.111 | 111 | 192.168.111.254 | 255.255.255.0 |

## 3. Verificar la configuración

Para revisar el estado de las interfaces:

```cisco
show ip interface brief
```

Para revisar las subinterfaces y sus direcciones:

```cisco
show running-config
```


# 11._Asignación de Direccionamiento IP y Encapsulamiento Dot1Q

## 1. Configuración del router R1-Core-LMLR

```cisco
enable
configure terminal

interface gigabitEthernet 0/0
 no shutdown
exit

interface gigabitEthernet 0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.254 255.255.255.0
exit

interface gigabitEthernet 0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.254 255.255.255.0
exit

interface gigabitEthernet 0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.254 255.255.255.0
exit

interface gigabitEthernet 0/0.99
 encapsulation dot1Q 99
 ip address 192.168.99.254 255.255.255.0
exit

interface gigabitEthernet 0/0.111
 encapsulation dot1Q 111 native
 ip address 192.168.111.254 255.255.255.0
exit

end
copy running-config startup-config
```

## 2. Tabla de direccionamiento IP

| VLAN | Nombre | Red | Gateway | Máscara |
|---|---|---|---|---|
| 10 | ADMINISTRACION | 192.168.10.0/24 | 192.168.10.254 | 255.255.255.0 |
| 20 | LABORATORIOS | 192.168.20.0/24 | 192.168.20.254 | 255.255.255.0 |
| 30 | DIRECCION | 192.168.30.0/24 | 192.168.30.254 | 255.255.255.0 |
| 99 | GESTION | 192.168.99.0/24 | 192.168.99.254 | 255.255.255.0 |
| 111 | NATIVA | 192.168.111.0/24 | 192.168.111.254 | 255.255.255.0 |

## 3. ¿Qué es el encapsulamiento Dot1Q?

El encapsulamiento Dot1Q utiliza el estándar IEEE 802.1Q para identificar a qué VLAN pertenece cada trama que pasa por un enlace troncal.

Ejemplo:

```cisco
encapsulation dot1Q 10
```

Este comando identifica el tráfico de la VLAN 10 en la subinterfaz correspondiente.

Para la VLAN nativa se utiliza:

```cisco
encapsulation dot1Q 111 native
```

## 4. Verificación de la configuración

Para comprobar que las interfaces estén activas:

```cisco
show ip interface brief
```

Para revisar las subinterfaces y el encapsulamiento configurado:

```cisco
show running-config
```


#12._ Verificación de Conectividad con Ping

## 1. Verificar la conexión con el gateway

Desde una PC de la VLAN 10, abrir **Desktop > Command Prompt** y ejecutar:

```cmd
ping 192.168.10.254
```

Desde una PC de la VLAN 20:

```cmd
ping 192.168.20.254
```

Desde una PC de la VLAN 30:

```cmd
ping 192.168.30.254
```

Desde una PC de la VLAN 99:

```cmd
ping 192.168.99.254
```

## 2. Verificar la comunicación entre computadoras

Desde una PC de la VLAN 10, probar la conexión con una PC de la VLAN 20:

```cmd
ping 192.168.20.11
```

Para comprobar la comunicación con una PC de la VLAN 30:

```cmd
ping 192.168.30.11
```

> Las direcciones de destino deben coincidir con las direcciones IP reales configuradas en las computadoras.

## 3. Verificar la configuración IP de una PC

En la ventana **Desktop > Command Prompt**, ejecutar:

```cmd
ipconfig
```

Comprobar que la PC tenga:
- Una dirección IP perteneciente a su VLAN.
- La máscara de subred `255.255.255.0`.
- El gateway predeterminado correspondiente a su VLAN.
 ```` 
## 4. Resultados esperados

| Prueba | Resultado esperado |
|---|---|
| PC VLAN 10 → 192.168.10.254 | Respuesta exitosa |
| PC VLAN 20 → 192.168.20.254 | Respuesta exitosa |
| PC VLAN 30 → 192.168.30.254 | Respuesta exitosa |
| PC VLAN 99 → 192.168.99.254 | Respuesta exitosa |
| PC VLAN 10 → PC VLAN 20 | Respuesta exitosa si ambas están configuradas correctamente |
 ```` 
## 5. ¿Qué hacer si falla el Ping?

1. Verificar la dirección IP, la máscara y el gateway de la PC con `ipconfig`.
2. Comprobar que el puerto del switch esté asignado a la VLAN correcta con `show vlan brief`.
3. Revisar los enlaces troncales con `show interfaces trunk`.
4. Verificar las subinterfaces del router con `show ip interface brief`.
5. Comprobar que los cables estén conectados correctamente.

 ```` 
## Evidencia de verificación de conectividad con Ping
![Verificación de conectividad con Ping](imgs/verificacion%20de%20ping.png)





## Archivo de Packet Tracer

<a href="proyecto.pkt" download>📥 Descargar proyecto de Packet Tracer</a>


### ¿Cuál fue el mayor reto técnico que enfrentaste en esta unidad?
Para mí, lo más difícil fue **hacer el enrutamiento entre las VLANs con el router (Router-on-a-Stick)**. Al principio me costó trabajo entender cómo conectar todo y configurar bien las subinterfaces del router para que comunicaran a las diferentes computadoras. También se me complicó la parte de la documentación en GitHub, porque por culpa de unos espacios y unos acentos al revés que dejé abiertos, **no se querían cargar ni las imágenes de evidencia ni el enlace para descargar mi archivo de Packet Tracer**.

---

### Bitácora de Errores

| Sección | Lo que me pasó y cómo lo arreglé |
| :--- | :--- |
| **Error 1** | **No me daba Ping entre diferentes VLANs porque olvidé el comando de encapsulación.**<br>Creé las subinterfaces en el router pero se me pasó ponerles el comando `encapsulation dot1Q`, así que el router no sabía a qué VLAN pertenecía cada red y el tráfico no pasaba. |
| **Solución 1** | Entré a la configuración de cada subinterfaz en el router, le puse el comando `encapsulation dot1Q` seguido del número de su VLAN, levanté las interfaces y ya funcionó el Ping entre las PCs. |
| **Error 2** | **El enlace de Packet Tracer y la imagen del Ping salían como texto normal en GitHub.**<br>Cuando subí mi proyecto a GitHub, el link para descargar el archivo `.pkt` y la imagen de los resultados se veían feos, como texto plano con corchetes. Esto pasó porque dejé un bloque de código abierto con tres acentos (` ``` `) y porque el nombre de mi imagen tenía espacios en blanco. |
| **Solución 2** | Entré a editar el archivo `README.md`, busqué dónde faltaba cerrar los acentos y los puse bien. Después cambié los enlaces de Markdown normales por etiquetas de HTML (`<a>` y `<img>`) para que GitHub no se confundiera con los espacios y el link de descarga se volviera azul. |

