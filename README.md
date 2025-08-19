# Servidor Web ligero + Servicios REST — TALLER: Arquitectura de Aplicaciones Distribuidas

**Alumno:** Alexandra Moreno Latorre  
**Asignatura:** Arquitectura Empresarial  
**Docente:** Luis Daniel Benavides Navarro

Este repositorio contiene diferentes implementaciones de servidores en **Java** para estudiar los conceptos básicos de **comunicación cliente-servidor**, utilizando **sockets TCP** y **datagramas UDP**.  

Incluye:
- Un servidor **HTTP básico** que responde formularios y archivos estáticos.
- Un **Echo Server** y su respectivo cliente para probar comunicación TCP.
- Un servidor que calcula funciones trigonométricas según la instrucción del cliente.
- Un **servidor UDP de hora**, junto con un cliente que actualiza la hora cada 5 segundos, incluso cuando el servidor se apaga y se reinicia.

---
## 📑 Tabla de contenidos
1. [Descripción general](#-descripción-general)  
2. [Características](#-características)  
3. [Requisitos](#-requisitos)  
4. [Instalación](#-instalación)  
5. [Compilar y ejecutar](#-compilar-y-ejecutar)  
6. [Estructura del proyecto](#-estructura-del-proyecto)  
7. [Endpoints y uso](#-endpoints-y-uso)  
8. [Frontend (demo) — comunicación asíncrona](#-frontend-demo--comunicación-asíncrona)  
9. [Pruebas y evaluación realizadas](#-pruebas-y-evaluación-realizadas)  
10. [Arquitectura y decisiones de diseño](#-arquitectura-y-decisiones-de-diseño)  
11. [Limitaciones y mejoras futuras](#-limitaciones-y-mejoras-futuras)  
12. [Cómo subir a GitHub (comandos)](#-cómo-subir-a-github-comandos)  
13. [Licencia](#-licencia)  
14. [Contacto](#-contacto)  

---

## 📌 Descripción general
El proyecto implementa diferentes **servidores ligeros en Java** utilizando **Sockets**:

- **HTTP Server (35000/35003):** responde a peticiones GET/POST, sirve archivos HTML, CSS, JS e imágenes.  
- **Echo Server (35001):** devuelve lo mismo que recibe el cliente, ideal para pruebas iniciales.  
- **Function Server (35002):** evalúa funciones trigonométricas (`cos`, `sin`, `tan`), cambiando dinámicamente según comandos enviados (`fun:sin`).  
- **Time Server UDP (35004):** envía la hora actual cada vez que el cliente lo solicita. El cliente actualiza la hora cada 5 segundos y mantiene el último valor si el servidor cae, reanudando al restaurarse.  

El objetivo es reforzar el entendimiento de:
- TCP vs UDP.
- Flujo de datos orientado a conexión vs no orientado.
- Implementación de un servidor HTTP desde cero.  

---

## ⚙️ Características
- **HTTP Server:**
  - Respuestas con `Content-Type` correcto (`text/html`, `image/png`, etc.).
  - Manejo de errores (`404 Not Found`, `500 Internal Error`).
  - Compatible con formularios HTML y peticiones JS (`fetch`, `XMLHttpRequest`).

- **TCP:**
  - Echo server para pruebas básicas.
  - Servidor trigonométrico con cambio dinámico de función.

- **UDP:**
  - Cliente resiliente a caídas del servidor.
  - Actualización periódica de la hora (cada 5 segundos).

- **Código portable:** solo usa librerías estándar de Java.  

---

## 🖥️ Requisitos
- **Java JDK 11+** (recomendado JDK 17).  
- **Maven 3.6+** para compilar y ejecutar.  
- **NetBeans**

---

## Compilar y ejecutar
### Servidor HTTP (formularios y REST)
- mvn exec:java -Dexec.mainClass="co.edu.escuelaing.httpserver.HttpServer"
### Navegador: http://localhost:35000
### WebFileServer (archivos estáticos)
- mvn exec:java -Dexec.mainClass="co.edu.escuelaing.httpserver.WebFileServer"
### Navegador: http://localhost:35003
### Echo Server (con modo Cuadrado)
### Servidor (puerto 35001):
- mvn exec:java -Dexec.mainClass="co.edu.escuelaing.httpserver.EchoServer"
### Cliente (en otra terminal):
- mvn exec:java -Dexec.mainClass="co.edu.escuelaing.httpserver.EchoClient"
### Time Server UDP
Servidor (puerto 35004):
- mvn exec:java -Dexec.mainClass="co.edu.escuelaing.httpserver.TimeServerUDP"
Cliente:
- mvn exec:java -Dexec.mainClass="co.edu.escuelaing.httpserver.TimeClientUDP"

---
## 📂 Estructura del proyecto
src/main/java/co/edu/escuelaing/httpserver/
│── URLParser.java
│── URLReader.java
│── HttpServer.java
│── WebFileServer.java
│── EchoServer.java      
│── EchoClient.java
│── FunctionServer.java
│── FunctionClient.java
│── TimeServerUDP.java
└── TimeClientUDP.java

## Recursos estáticos (HTML/CSS/JS/img):
src/main/resources/public/

---

## Imágenes con resultados 
<img width="1440" height="900" alt="Captura de pantalla 2025-08-17 a la(s) 10 55 52 p m" src="https://github.com/user-attachments/assets/6a2f038b-3aa2-4909-881f-a95c67cce4df" />

<img width="1440" height="900" alt="Captura de pantalla 2025-08-18 a la(s) 2 32 58 p m" src="https://github.com/user-attachments/assets/e2b01d42-8bd3-4324-ab51-ff69c954b7cd" />

<img width="1440" height="900" alt="Captura de pantalla 2025-08-18 a la(s) 2 46 19 p m" src="https://github.com/user-attachments/assets/f13650d8-5623-4db4-a5a2-93ac165532f5" />

<img width="1440" height="900" alt="Captura de pantalla 2025-08-18 a la(s) 3 15 28 p m" src="https://github.com/user-attachments/assets/a10fe5f3-934e-4da7-9ad2-4a9cfc087eef" />

<img width="669" height="818" alt="Captura de pantalla 2025-08-18 a la(s) 6 23 49 p m" src="https://github.com/user-attachments/assets/3b4d3932-66a8-4b35-b08c-82e8756fc8bc" />

<img width="1440" height="900" alt="Captura de pantalla 2025-08-18 a la(s) 6 40 50 p m" src="https://github.com/user-attachments/assets/3190a773-d48c-4012-91f1-e3143d999641" />

--- 

## 📥 Instalación
Clona el repositorio:

```bash
 git clone https://github.com/AlexandraMorenoL/TallerDisenoyEstructuracionAREM.git
 mvn clean install
```
---

## 📧 Contacto

Alexandra Moreno Latorre

Email: alexandra.moreno-l@mail.escuelaing.edu.co

Universidad Escuela Colombiana de Ingeniería Julio Garavito
