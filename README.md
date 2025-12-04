# Finca LODANA - Sistema de Gestión Agropecuaria

Sistema web completo para la gestión de registros del sector agropecuario, desarrollado para la Finca LODANA.

## 🚀 Características

- **Autenticación de Usuarios**: Sistema de login y registro con roles (Trabajador/Administrador)
- **Gestión de Cultivos**: Registro y seguimiento de cultivos
- **Gestión de Ganado**: Control de inventario animal
- **Sistema de Registros**: Registro de actividades y operaciones agropecuarias
- **Áreas de Trabajo**: Cultivos, Ganadería, Mantenimiento, Administración, Investigación

## 📋 Requisitos

- Node.js (v14 o superior)
- PostgreSQL (v12 o superior)
- pgAdmin 4 (opcional - para gestión de base de datos)
- npm o yarn

## 🔧 Instalación

1. Clonar el repositorio:
```bash
git clone <url-del-repositorio>
cd Proyecto-Vinculacion
```

2. Instalar dependencias:
```bash
npm install
```

3. Configurar variables de entorno:

Crea un archivo `.env` en la raíz del proyecto con el siguiente contenido:

```env
PORT=3000
DB_HOST=localhost
DB_PORT=5432
DB_NAME=finca_lodana
DB_USER=postgres
DB_PASSWORD=tu_contraseña_postgres
JWT_SECRET=tu_clave_secreta_muy_segura_aqui
NODE_ENV=development
```

4. Crear la base de datos en PostgreSQL:

Abre pgAdmin 4 o usa psql:
```sql
CREATE DATABASE finca_lodana;
```

5. Iniciar el servidor:

```bash
# Modo desarrollo (con auto-reload)
npm run dev

# Modo producción
npm start
```

El servidor estará disponible en `http://localhost:3000`

## 📁 Estructura del Proyecto

```
Proyecto-Vinculacion/
├── config/
│   └── database.js          # Configuración de PostgreSQL
├── controllers/
│   ├── authController.js    # Controlador de autenticación
│   ├── cultivoController.js # Controlador de cultivos
│   ├── ganadoController.js  # Controlador de ganado
│   └── registroController.js # Controlador de registros
├── middleware/
│   └── auth.js              # Middleware de autenticación
├── models/
│   ├── Usuario.js           # Modelo de usuario
│   ├── Cultivo.js           # Modelo de cultivo
│   ├── Ganado.js            # Modelo de ganado
│   └── Registro.js          # Modelo de registro
├── routes/
│   ├── auth.js              # Rutas de autenticación
│   ├── cultivos.js          # Rutas de cultivos
│   ├── ganado.js            # Rutas de ganado
│   └── registros.js         # Rutas de registros
├── login-lodana.html        # Página de login
├── server.js                # Archivo principal del servidor
├── package.json             # Dependencias del proyecto
└── README.md                # Este archivo
```

## 🔌 API Endpoints

### Autenticación

- `POST /api/auth/registro` - Registrar nuevo usuario
- `POST /api/auth/login` - Iniciar sesión
- `GET /api/auth/me` - Obtener información del usuario actual (protegido)

### Cultivos

- `GET /api/cultivos` - Obtener todos los cultivos
- `GET /api/cultivos/:id` - Obtener un cultivo específico
- `POST /api/cultivos` - Crear nuevo cultivo
- `PUT /api/cultivos/:id` - Actualizar cultivo
- `DELETE /api/cultivos/:id` - Eliminar cultivo

### Ganado

- `GET /api/ganado` - Obtener todo el ganado
- `GET /api/ganado/:id` - Obtener un animal específico
- `POST /api/ganado` - Registrar nuevo animal
- `PUT /api/ganado/:id` - Actualizar animal
- `DELETE /api/ganado/:id` - Eliminar animal

### Registros

- `GET /api/registros` - Obtener todos los registros
- `GET /api/registros/:id` - Obtener un registro específico
- `POST /api/registros` - Crear nuevo registro
- `PUT /api/registros/:id` - Actualizar registro
- `DELETE /api/registros/:id` - Eliminar registro

## 🔐 Autenticación

Todas las rutas (excepto login y registro) requieren autenticación mediante JWT Token.

Incluye el token en el header de las peticiones:
```
Authorization: Bearer <tu_token>
```

## 📝 Ejemplo de Uso

### Registrar Usuario

```javascript
POST http://localhost:3000/api/auth/registro
Content-Type: application/json

{
  "nombre": "Juan Pérez",
  "cedula": "1234567890",
  "email": "juan@example.com",
  "telefono": "0987654321",
  "area": "cultivos",
  "tipo": "trabajador",
  "password": "password123",
  "confirmPassword": "password123"
}
```

### Login

```javascript
POST http://localhost:3000/api/auth/login
Content-Type: application/json

{
  "user": "juan@example.com",
  "password": "password123",
  "tipo": "trabajador"
}
```

### Crear Cultivo

```javascript
POST http://localhost:3000/api/cultivos
Authorization: Bearer <token>
Content-Type: application/json

{
  "nombre": "Maíz",
  "tipo": "cereal",
  "area": 5,
  "unidad": "hectareas",
  "ubicacion": "Campo Norte",
  "fechaSiembra": "2024-01-15",
  "estado": "siembra"
}
```

## 🛠️ Tecnologías Utilizadas

- **Backend**: Node.js, Express.js
- **Base de Datos**: PostgreSQL con Sequelize ORM
- **Autenticación**: JWT (JSON Web Tokens)
- **Seguridad**: bcryptjs para hash de contraseñas

## 👥 Tipos de Usuario

- **Trabajador**: Acceso para registro de actividades
- **Administrador**: Acceso completo al sistema

## 📧 Áreas de Trabajo

- Cultivos
- Ganadería
- Mantenimiento
- Administración
- Investigación

## 📄 Licencia

ISC

---

Desarrollado para Finca LODANA - Sistema de Gestión Universitaria
