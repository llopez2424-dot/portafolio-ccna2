Sí. Copia **todo lo que está dentro de este bloque** y pégalo directamente en tu `README.md`:

```
# ✨ Ejemplo de Entrega (Modelo para el Alumno)

**Proyecto de Redes e Interconexión VLANs**

[🏠 Inicio](/ccna2-proyecto/) | [📋 Instrucciones Generales](/ccna2-proyecto/instrucciones.html) | [🏢 Problema: “TechCorp”](/ccna2-proyecto/problema.html) | [✨ Ejemplo de Entrega](/ccna2-proyecto/ejemplo-entrega.html) | [📊 Criterios de Evaluación](/ccna2-proyecto/criterios-evaluacion.html) | [✅ Lista de Cotejo](/ccna2-proyecto/lista-cotejo.html)

---

# Ejemplo de entrega de la primera sesión

> Recuerda que son varias sesiones de trabajo.

### 📋 Sigue un plan de Configuración de Red en orden por objetivos:

- [x] Crear el diagrama y cablear acorde a la topología.
- [ ] Crear la tabla de direccionamiento.
- [ ] Asignar nombre a los dispositivos con tus iniciales al final. Ejemplo: `R1-Core-ELO`.
- [ ] Realizar las tareas de configuración básica de switches y routers (contraseñas), y mensaje del día.
- [ ] Crear las VLANs.
- [ ] Asignar los puertos a las VLANs.
- [ ] Verificar la configuración de las VLANs.
- [ ] Habilitar los enlaces troncales.
- [ ] Verificar la configuración de los enlaces troncales.
- [ ] Guardar la configuración.
- [ ] Configurar las subinterfaces en el router.
- [ ] Asignar direccionamiento IP y encapsulamiento Dot1Q.
- [x] Verificar conectividad con `Ping`.

---

## 🖥️ Topología

![Ejemplo de entrega](/ccna2-proyecto/imgs/1-topologia.png)

> Agrega las imágenes. Puedes guiarte con esta estructura para armar tu `README.md`.
>
> **Recomiendo crear una carpeta llamada `imgs` y colocar ahí las imágenes.**

Ejemplo:
```

!Imagen de topología

```

---

## 📋 Crea tabla de direccionamiento

### Tabla A: Dispositivos Intermedios (Routers y Switches) — EJEMPLO
```

| Dispositivo / Interfaz | VLAN | Segmento de Red Base | Dirección IP a Calcular / Configurar | Máscara de Subred | Gateway por Defecto |
| --- | --- | --- | --- | --- | --- |
| **R1-Core-ELO** (`G0/0/0.10`) | 10 | `192.168.10.0/24` | **Última IP utilizable del segmento** | `255.255.255.0` | _No aplica_ |
| **R1-Core-ELO** (`G0/0/0.20`) | 20 | `192.168.20.0/24` | **Última IP utilizable del segmento** | `255.255.255.0` | _No aplica_ |

### Tabla B: Dispositivos Finales (PCs de Usuario y Gestión) — EJEMPLO

| Dispositivo Final | Puerto del Switch | VLAN | Dirección IP (Formato CIDR) | Gateway por Defecto |
| --- | --- | --- | --- | --- |
| **PC-Administrativos-1** | `SW-Lab2-ELO -> Fa0/1` | 10 | `192.168.10.15/24` | Última IP utilizable del segmento |
| **PC-Alumnos-2** | `SW-Lab1-ELO -> Fa0/2` | 10 | `192.168.10.42/24` | Última IP utilizable del segmento |

---

## 📥 Archivo de Packet Tracer

- Descargar mi topología Etapa 1 (.pkt)

---

## 💻 Comandos de configuración

Escribe los comandos que estás ejecutando para la configuración en tu archivo `README.md`:

```
R1-Core-ELO(config)#interface GigabitEthernet0/0/0.10
```

---

## 📸 Evidencias CLI

```
SW-Piso1# show vlan brief
10   Administracion                   active    Fa0/1, Fa0/2
20   Ventas                           active    Fa0/3, Fa0/4
```

A continuación se presenta la configuración de la interfaz en **R1-Core**:

```
interface GigabitEthernet0/0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.254 255.255.255.0
```

---

## 📌 Proyecto

**Proyecto de Redes e Interconexión VLANs — TechCorp**

🏠 Inicio | 📋 Instrucciones Generales | 🏢 Problema: “TechCorp” | ✨ Ejemplo de Entrega | 📊 Criterios de Evaluación | ✅ Lista de Cotejo

**Proyecto mantenido por****elzro****.**

_Hosted on GitHub Pages — Theme by__mattgraham__._

```

```

Elemento	Sintaxis
Encabezados	
# H1
## H2
## H3
Negrita	
**texto en negrita**
__texto en negrita__
Cursiva	
*texto en cursiva*
_texto en cursiva_
Citas	
> cita
Listas ordenadas	
1. Primer elemento
1. Segundo elemento
Listas no ordenadas	
* Primer elemento
* Segundo elemento
 
+ Primer elemento
+ Segundo elemento
 
- Primer elemento
- Segundo elemento
Código	
`código`
Línea horizontal	
---
Enlaces	
[anchor](https://enlace.tld "título")
Imágenes	
![Alt](/ruta/imagen.png)

Elemento	Sintaxis
Tablas	
| Color | Código |
| ----------- | ----------- |
| Rojo | #FF0000 |
| Azul | #0000FF |
Bloques de código avanzados	
```
{
  "Nombre": "Edu",
  "Peso": "72Kg"
}
```
Resaltado de sintaxis	
```json
{
  "Nombre": "Edu",
  "Peso": "72Kg"
}
```
Notas al pie	
Texto con referencia. [^1]
 
[^1]: Nota de la referencia
IDs de cabecera	
## Encabezado {#id-personalizado}
Listas de definiciones	
Término
: definición
Texto tachado	
~~Texto tachado~~
Listas de tareas	
- [x] Primera tarea
- [ ] Segunda tarea
- [ ] Tercera tarea
Emojis (copiar y pegar)	
😄
Emojis (shortcodes)	
:smile:
Enlaces automáticos	
https://www.neoguias.com
Deshabilitar enlaces automáticos	
`https://www.neoguias.com`

# Crear el diagrama y cablear acorde a la topologia.
![diagrama de topologia 1](/imgs/1-diagrama.png)
> creando la topologia

# Crear la tabla de direccionamiento
Claro, aquí tienes la tabla en **Markdown lista para copiar**:


| Dispositivo / Interfaz | VLAN | Segmento de Red Base | Dirección IP a Calcular / Configurar | Máscara de Subred | Gateway por Defecto |
|---|---:|---|---|---|---|
| R1-Core-ELO (G0/0/0.10) | 10 | 192.168.10.0/24 | 192.168.10.254 | 255.255.255.0 | No aplica |

