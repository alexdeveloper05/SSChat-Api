# SSChat-Api

El backend de SSChat. Básicamente es el servidor que hace que la app funcione - maneja usuarios, mensajes, y toda la magia de los WebSockets.

## Qué hace esto?

- Maneja el login y registro de usuarios
- Gestiona los chats y los mensajes
- WebSockets para que los mensajes lleguen en tiempo real
- Se conecta a una base de datos PostgreSQL

## Tech Stack

- **Node.js + Express** - El servidor
- **TypeScript** - Para no morir con errores raros
- **WebSockets (ws)** - Mensajes en tiempo real
- **PostgreSQL** - Base de datos
- **Zod** - Validación de datos

## Cómo desplegarlo

### Opción 1: En local (para desarrollo)

1. Clona el repo
```bash
git clone https://github.com/alexdeveloper05/SSChat-Api.git
```

2. Instala las dependencias
```bash
npm install
```

3. Crea un archivo `.env` en la raíz con esto:
```env
DB_URL="tu_url_de_postgresql"
API_PORT="8080"
```

4. Corre el servidor en modo desarrollo
```bash
npm run dev
```

Y listo, debería decir que está corriendo en `http://localhost:8080`

### Opción 2: En Railway (lo que yo uso)

Railway es gratis y muy fácil de usar para esto.

1. Crea una cuenta en [railway.app](https://railway.app)

2. Crea un nuevo proyecto y selecciona "Deploy from GitHub repo"

3. Conecta tu repo de SSChat-Api

4. Railway te da una base de datos PostgreSQL gratis. Créala desde "New" > "Database" > "PostgreSQL"

5. Configura las variables de entorno en Railway:
   - `DB_URL` - Railway te da esta URL cuando creas la base de datos (la encuentras en "Variables" de tu DB)
   - `API_PORT` - Pon `8080` o el puerto que quieras

6. Railway hace el deploy automático cuando pushas a main

7. Te da una URL pública tipo `https://tu-proyecto.up.railway.app` - esa es la que usas en la app de SSChat

### Opción 3: En cualquier VPS/servidor

1. Clona el repo en tu servidor

2. Instala dependencias
```bash
npm install
```

3. Compila TypeScript
```bash
npm run build
```

4. Configura las variables de entorno (.env o las de tu sistema)

5. Corre el servidor
```bash
npm start
```

Tip: Usa PM2 o algo así para que no se muera el servidor:
```bash
npm install -g pm2
pm2 start dist/index.js --name sschat-api
```

## Variables de entorno

| Variable | Descripción |
|----------|-------------|
| `DB_URL` | URL de conexión a PostgreSQL |
| `API_PORT` | Puerto donde corre el servidor (default: 8080) |

## Scripts disponibles

- `npm run dev` - Corre el servidor con hot reload (para desarrollo)
- `npm run build` - Compila TypeScript a JavaScript
- `npm start` - Corre el servidor compilado (para producción)

## Estructura del proyecto

```
src/
├── index.ts          # Punto de entrada
├── conf/             # Configuración de la DB
├── http/             # API REST
│   ├── controllers/  # Lógica de los endpoints
│   ├── models/       # Modelos de datos
│   └── router.ts     # Rutas HTTP
└── sockets/          # WebSockets
    ├── controllers/  # Lógica de los eventos
    ├── models/       # Modelos de datos
    └── router.ts     # Manejo de conexiones WS
```

## Importante

Esta es la API del proyecto SSChat. Para que sirva de algo necesitas la app:

👉 **https://github.com/alexwebdev05/SSChat.git**

---

Hecho con mas café del que debería tomar
