# Farmacia Marketplace Backend

## Project Overview
- Sistema: Marketplace de parafarmacia (venta de productos de cuidado personal y productos no medicamentosos)
- Restricción: Los medicamentos prohibidos su venta por internet
- Enfoque: Desarrollo Backend integral
- Stack Tecnológico: Java 21 + Spring Boot 4.X
Development Guidelines

### Architecture
- Arquitectura Hexagonal: Capa de núcleo (domain/services) aislada de adaptadores (DB, web, external services)
- Monolítico actual: Un solo artefacto Spring Boot
- Futuro: Migración a microservicios

### Database
- Motores evaluados: Oracle Database, PostgreSQL, MySQL (seleccionar 2)
- Contenedores: Docker para bases de datos
- Pendiente: Evaluar contenedorización de la aplicación

### Code Conventions
- Package structure: Por dominio (hexagonal) - core/, adapter/, config/
- **Package by domain**: `core/domain/` (entidades, servicios de dominio), `core/application/` (casos de uso), `adapter/` (repositorios, servicios externos), `config/` (configuración Spring)
- Capa `core/` no debe tener dependencias de capas externas
- Java 21 features: Records, Sealed Classes, Pattern Matching
- Spring Boot 4.X: Últimas características y mejoras

### Runtime Configuration
- **Perfiles**: `dev` (H2 en memoria), `test` (testcontainers), `prod` (Oracle/PostgreSQL)
- **Variables de entorno**: DB_URL, DB_USER, DB_PASSWORD obligatorios en producción

### Code Quality
- **Checkstyle**: Configurado en `checkstyle.xml` con reglas domain-first
- **PMD/Spotbugs**: Ejecutar en CI como parte del gate de PR
- **Java 21**: Maximum use de Records para DTOs inmutables, Sealed Classes para dominio controlado

### Compliance
- **Validación de medicamentos**: Middleware que intercepta requests y verifica producto.classification != "MEDICAMENTO"
- **Rate limiting**: Aplicar a endpoints de catálogo para prevenir scraping
- **Log audit**: Todos los cambios de stock/catálogo deben incluir user_id y motivo

### Git & GitHub
- Flujo: Feature branch → PR → main
- Convenciones de commit: Conventional Commits recomendado
- Protección de main: Revisión requerida

### Running & Testing
#### Levantar BDs con Docker
docker-compose up -db

#### Ejecutar aplicación
./mvnw spring-boot:run

#### Tests
./mvnw test

## AI Interaction Guidelines
- Sigue las convenciones del proyecto
- Prioriza soluciones hexagonal/clean code
- Mantén separación lógica/tecnología
- Considera restricciones de parafarmacia (medicamentos)

## Project-Specific Notes
- **Productos permitidos**: Solo venta de productos de cuidado personal y productos no medicamentosos
- **Auditoría**: Registro de quién aprobó la inclusión de un producto en catálogo
- Control de stock y disponibilidad
- Integración con pasarelas de pago (solo productos permitidos)
- Auditoría de cambios en catálogo de productos

## No hagas
- No puedes tocar el código, yo lo tocare.
- No tocar ningun fichero ni directorio.

## Flujo de trabajo
- Antes de una tarea no trivial, propón un plan y espera OK
- Una tarea a la vez.
- Si no estás seguro al 95%, pregunta.  No inventes.
- Tu misión es la de guiarme en mi trabajo y enseñarme.
- No puedes tocar, ni cambiar el codigo del proyecto.

## Documentación
Esta pendiente de desarrollar:
 - Análisis de requerimiento.
 - Análisis de la arquitectura del sistema / software.
 - Análisis del software o aplicación.
 - Juego de datos, incluyendo los endpoints de la aplicación.