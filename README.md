# GreenBite - Arquitectura de Microservicios FullStack

## Integrantes

* Fernanda Paredes
* Martina Flores
* Alexander Torres

---

# Descripción General

GreenBite es una aplicación FullStack desarrollada utilizando arquitectura de microservicios.

El sistema permite administrar productos y suscripciones mediante una interfaz web desarrollada en React, consumiendo servicios backend a través de un Backend For Frontend (BFF) implementado con Spring Cloud Gateway.

La solución fue desarrollada aplicando principios de desacoplamiento, cohesión y persistencia independiente por servicio.

---

# Arquitectura General

```text
Frontend React (5173)
          │
          ▼
     BFF Gateway
      Puerto 8080
          │
   ┌──────┴──────┐
   ▼             ▼
Productos     Suscripciones
  8081           8082
MongoDB          H2
```

---

# Tecnologías Utilizadas

## Frontend

* React
* Vite
* Axios
* CSS3

## Backend

* Java 17
* Spring Boot 3.4.1
* Spring Cloud Gateway
* Spring Data MongoDB
* Spring Data JPA
* H2 Database

## Testing

* JUnit 5
* Mockito
* JaCoCo

## Documentación

* Swagger / OpenAPI

## Contenedores

* Docker
* Docker Compose

---

# Patrones de Diseño Implementados

* Microservices Architecture
* Backend For Frontend (BFF)
* API Gateway Pattern
* DTO Pattern
* Repository Pattern
* Service Layer Pattern
* Exception Handler Pattern
* Database per Service

---

# Componentes del Sistema

## Frontend

Aplicación React encargada de la interacción con el usuario.

Funcionalidades:

* Registro de productos
* Listado de productos
* Eliminación de productos
* Registro de suscripciones
* Listado de suscripciones
* Eliminación de suscripciones

---

## BFF (Backend For Frontend)

Gateway encargado de centralizar el acceso a los microservicios.

Puerto:

```text
8080
```

Tecnologías:

* Spring Cloud Gateway
* Spring WebFlux

---

## Microservicio Productos

Responsable de la gestión de productos.

Puerto:

```text
8081
```

Persistencia:

```text
MongoDB
```

Funcionalidades:

* Obtener productos
* Obtener producto por ID
* Crear producto
* Eliminar producto

Cobertura de pruebas:

```text
62%
```

---

## Microservicio Suscripciones

Responsable de la gestión de suscripciones.

Puerto:

```text
8082
```

Persistencia:

```text
H2 Database + JPA
```

Funcionalidades:

* Obtener suscripciones
* Obtener suscripción por ID
* Crear suscripción
* Eliminar suscripción

Cobertura de pruebas:

```text
71%
```

---

# Persistencia de Datos

La solución implementa el patrón:

```text
Database per Service
```

Cada microservicio administra su propia base de datos de manera independiente.

| Microservicio | Persistencia |
| ------------- | ------------ |
| Productos     | MongoDB      |
| Suscripciones | H2 Database  |

---

# Documentación API

Swagger se encuentra disponible en:

## Productos

```text
http://localhost:8081/swagger-ui/index.html
```

## Suscripciones

```text
http://localhost:8082/swagger-ui/index.html
```

---

# Pruebas Unitarias

Las pruebas fueron desarrolladas utilizando:

* JUnit 5
* Mockito
* JaCoCo

Coberturas obtenidas:

| Componente    | Cobertura |
| ------------- | --------- |
| Productos     | 62%       |
| Suscripciones | 71%       |

Cumpliendo el mínimo exigido por la rúbrica (60%).

---

# Ejecución del Proyecto

## 1. Levantar MongoDB

Desde el repositorio Productos:

```bash
docker compose up -d
```

---

## 2. Ejecutar Productos

```bash
mvn spring-boot:run
```

Puerto:

```text
8081
```

---

## 3. Ejecutar Suscripciones

```bash
mvn spring-boot:run
```

Puerto:

```text
8082
```

---

## 4. Ejecutar BFF

```bash
mvn spring-boot:run
```

Puerto:

```text
8080
```

---

## 5. Ejecutar Frontend

```bash
npm install
npm run dev
```

Puerto:

```text
5173
```

---

# Documentación Entregada

El repositorio principal incluye:

## Arquitectura_GreenBite.pdf

Diagrama y explicación de la arquitectura implementada.

## Persistencia_GreenBite.pdf

Descripción detallada de la persistencia de datos, JPA, MongoDB y patrón Database per Service.

## Pruebas_Unitarias_GreenBite.pdf

Cobertura JaCoCo, pruebas implementadas y métricas obtenidas.

## repositorios.txt

Listado de todos los repositorios GitHub del proyecto junto a su descripción.

---

# Repositorios del Proyecto

La lista completa de repositorios se encuentra en:

```text
repositorios.txt
```

---

# Conclusión

GreenBite implementa una arquitectura de microservicios basada en Spring Boot y React, utilizando persistencia independiente por servicio, documentación OpenAPI, pruebas unitarias automatizadas y un BFF para centralizar la comunicación entre frontend y backend.

La solución cumple los requisitos de arquitectura, persistencia, pruebas y documentación establecidos para el proyecto de Desarrollo FullStack III.
