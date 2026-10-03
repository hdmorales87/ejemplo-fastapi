# Ejemplo FastAPI

Proyecto de ejemplo con FastAPI, un framework web moderno y rápido para construir APIs con Python 3.14+.

## 📋 Tabla de Contenidos

- [Requisitos Previos](#requisitos-previos)
- [Instalación](#instalación)
- [Configuración del Entorno Virtual](#configuración-del-entorno-virtual)
- [Ejecución del Proyecto](#ejecución-del-proyecto)
- [Documentación de la API](#documentación-de-la-api)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Comandos Útiles](#comandos-útiles)

## 🔧 Requisitos Previos

- **Python**: 3.14 o superior
- **uv**: Gestor de paquetes y entornos virtuales de Python (recomendado)
  - Instalación: `pip install uv`
- **Git** (opcional, para control de versiones)

## 📦 Instalación

### 1. Clonar el repositorio (si aplica)

```bash
git clone <url-del-repositorio>
cd ejemplo-fastapi
```

### 2. Configuración del Entorno Virtual

#### Opción A: Usando uv (Recomendado)

```bash
# Crear entorno virtual con la versión de Python especificada
uv venv --python 3.14

# Activar el entorno virtual
# En Windows:
.venv\Scripts\activate
# En Linux/Mac:
source .venv/bin/activate

# Instalar dependencias
uv pip install -e .
```

#### Opción B: Usando venv estándar

```bash
# Crear entorno virtual
python -m venv .venv

# Activar el entorno virtual
# En Windows:
.venv\Scripts\activate
# En Linux/Mac:
source .venv/bin/activate

# Actualizar pip
pip install --upgrade pip

# Instalar dependencias
pip install -e .
```

## 🚀 Ejecución del Proyecto

### Iniciar el servidor de desarrollo

```bash
# Usando uvicorn directamente
uvicorn ejemplo_fastapi.main:app --reload

# O usando el script definido en pyproject.toml
python -m uvicorn ejemplo_fastapi.main:app --reload
```

El servidor se iniciará en `http://localhost:8000`

### Opciones adicionales de ejecución

```bash
# Especificar puerto diferente
uvicorn ejemplo_fastapi.main:app --reload --port 8080

# Especificar host específico
uvicorn ejemplo_fastapi.main:app --reload --host 0.0.0.0

# Ver logs detallados
uvicorn ejemplo_fastapi.main:app --reload --log-level debug
```

## 📚 Documentación de la API

FastAPI genera automáticamente documentación interactiva:

- **Swagger UI**: `http://localhost:8000/docs`
- **ReDoc**: `http://localhost:8000/redoc`
- **OpenAPI Schema**: `http://localhost:8000/openapi.json`

### Endpoints Disponibles

#### 1. GET `/`
Endpoint de prueba que retorna un saludo.

**Respuesta:**
```json
{
  "Hello": "World"
}
```

#### 2. POST `/items`
Crea un nuevo item con el ID proporcionado.

**Parámetros:**
- `item_id` (int, required): ID del item en el cuerpo de la solicitud

**Respuesta:**
```json
{
  "Saved": 123
}
```

**Ejemplo de solicitud:**
```bash
curl -X POST "http://localhost:8000/items" -H "Content-Type: application/json" -d '{"item_id": 123}'
```

#### 3. GET `/items/{item_id}`
Obtiene un item por su ID con un parámetro de consulta opcional.

**Parámetros de ruta:**
- `item_id` (int, required): ID del item

**Parámetros de consulta:**
- `q` (str, optional): Parámetro de consulta opcional

**Respuesta:**
```json
{
  "item_id": 123,
  "q": "algún-valor"
}
```

**Ejemplo de solicitud:**
```bash
curl "http://localhost:8000/items/123?q=test"
```

## 📁 Estructura del Proyecto

```
ejemplo-fastapi/
├── .gitignore              # Archivos ignorados por Git
├── .python-version         # Versión de Python requerida (3.14)
├── pyproject.toml          # Configuración del proyecto y dependencias
├── uv.lock                 # Lockfile de dependencias (uv)
├── README.md               # Este archivo
└── src/
    └── ejemplo_fastapi/
        ├── __init__.py     # Inicialización del paquete
        └── main.py         # Aplicación principal FastAPI
```

### Descripción de Archivos

- **pyproject.toml**: Contiene la configuración del proyecto, dependencias y scripts. 
  - Usa `fastapi[standard]` que incluye: uvicorn, pydantic, etc.
  - Define el entrypoint para FastAPI: `ejemplo_fastapi.main:app`
  
- **src/ejemplo_fastapi/main.py**: Archivo principal con la aplicación FastAPI y los endpoints.

- **src/ejemplo_fastapi/__init__.py**: Inicialización del paquete Python.

## 🛠️ Comandos Útiles

### Gestión de Dependencias

```bash
# Agregar una nueva dependencia
uv add nombre-del-paquete

# Agregar dependencia de desarrollo
uv add --dev nombre-del-paquete

# Actualizar dependencias
uv pip install -e .

# Ver dependencias instaladas
uv pip list
```

### Entorno Virtual

```bash
# Desactivar el entorno virtual
deactivate

# Eliminar el entorno virtual (Windows)
rmdir /s .venv

# Eliminar el entorno virtual (Linux/Mac)
rm -rf .venv
```

### Desarrollo

```bash
# Formatear código (si se usa black)
black src/

# Verificar tipos (si se usa mypy)
mypy src/

# Ejecutar pruebas (si existen)
pytest
```

## 📖 Documentación Técnica

### Tecnologías Utilizadas

- **FastAPI 0.141.1+**: Framework web moderno y de alto rendimiento
- **Uvicorn**: Servidor ASGI para ejecutar aplicaciones FastAPI
- **Pydantic**: Validación de datos usando anotaciones de tipo Python
- **Python 3.14+**: Última versión de Python con características modernas

### Características de FastAPI

- ✅ Validación automática de datos
- ✅ Documentación interactiva automática (Swagger UI, ReDoc)
- ✅ Soporte para async/await
- ✅ Type hints de Python
- ✅ Extremadamente rápido (comparable con NodeJS y Go)
- ✅ Basado en estándares OpenAPI

### Desarrollo Futuro

Para expandir este proyecto, considera:

1. **Agregar más endpoints**: CRUD completo para recursos
2. **Base de datos**: Integrar SQLAlchemy o Tortoise ORM
3. **Autenticación**: JWT, OAuth2
4. **Middleware**: CORS, logging, etc.
5. **Testing**: Pytest con pytest-asyncio
6. **Docker**: Contenedorización para despliegue
7. **Configuración**: Variables de entorno con python-dotenv

## 📝 Licencia

Agregar información de licencia aquí.

## 👥 Autores

- **hdmorales87** - hdmorales87@gmail.com

## 🤝 Contribución

Instrucciones para contribuir al proyecto.
