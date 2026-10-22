# BITSS — Despliegue con Docker Compose

### Estructura del proyecto

```text
BITSS-Deploy/
├── .gitignore
├── .env.example
├── .env
├── docker-compose.yml
├── mysql/
│   └── init.sql
├── Usuario/
├── Catalogo/
├── Carro/
├── Gestion/
├── Pagos/
├── Coleccion/
├── Notificaciones/
└── ApiGateway/
```

Cada carpeta de microservicio corresponde a un repositorio independiente de GitHub.

### Configuración inicial

Crea el archivo `.env` a partir de la plantilla:

**Linux / Git Bash**
```bash
cp .env.example .env
```

**Windows PowerShell**
```powershell
Copy-Item .env.example .env
```

Edita `.env` y configura las variables necesarias, especialmente la contraseña de MySQL y el secreto JWT.

## Iniciar todos los servicios

Desde la carpeta raíz del proyecto, ejecuta:

```bash
docker compose up --build -d
```

Para revisar el estado de los contenedores:

```bash
docker compose ps
```

Para consultar los registros:

```bash
docker compose logs -f
```

## Acceso a los servicios

La API Gateway queda disponible en:

- **API Gateway:** http://localhost:8080

## Detener los servicios

Para detener y eliminar los contenedores:

```bash
docker compose down
```

Para detenerlos y eliminar también el volumen persistente de MySQL:

```bash
docker compose down -v
```

> **Advertencia:** `docker compose down -v` elimina el volumen de datos de MySQL administrado por Compose. Los datos se perderán si no tienes una copia de seguridad.