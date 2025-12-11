# Backend UTN - API REST en TypeScript

Backend desarrollado en **TypeScript** con **Node.js**, **Express** y **MongoDB**, que permite gestionar productos y usuarios con autenticación JWT, subida de imágenes y envío de correos.  

El proyecto está desplegado en **Render.com** y listo para consumo desde un frontend.

API funcionando online en:  
   **https://backend-utn-msqw.onrender.com/**
 y con los productos en:   
   **https://backend-utn-msqw.onrender.com/products**
   
---

## Video explicativo de la API:

# Link: https://www.youtube.com/watch?v=Dj3YULS1FYM

---

# 📸 Capturas de Bruno y funcionamiento de los Endpoints:

## 📸 Obtener todos los productos
![Productos](./src/assets/getallproducts.png)

## 📸 Obtener producto por ID
![Producto por ID](./src/assets/getproductid.png)

## 📸 Registro de usuario
![Registro](./src/assets/registeruser.png)

## 📸 Registro "Usuario ya registrado"
!["Usuario ya registrado"](./src/assets/registerusuarioregistrado.png)

## 📸 Login de usuario
![Login](./src/assets/loginusers.png)

## 📸 Añadir producto
![Añadir Producto](./src/assets/addproduct.png) 

## 📸 Actualizar producto
![Actualizar producto](./src/assets/updateproduct.png)

## 📸 Borrar productos
![Borrar Productos](./src/assets/deleteproduct.png)

## 📸 Rate Limiter
![Rate Limiter](./src/assets/ratelimiter.png)


## 🔹 Tecnologías utilizadas:

- Node.js + Express
- TypeScript
- MongoDB + Mongoose
- JWT (autenticación)
- Bcryptjs (hash de contraseñas)
- Zod (validación de datos)
- Multer (subida de imágenes)
- Nodemailer (envío de correos)
- Morgan (logs)
- Express-rate-limit
- Render.com (deploy)


# 🔹 Instalación y ejecución local

## 1. Clonar el repositorio
git clone https://github.com/usuario/backend-utn.git
cd backend-utn

## 🔹 Instalar dependencias:

## 1. Instalar dependencias principales

npm install express mongoose jsonwebtoken bcryptjs zod multer nodemailer morgan express-rate-limit dotenv cors

Esto instala:

🔹Express

🔹Mongoose

🔹JWT

🔹Bcrypt

🔹Zod

🔹Multer

🔹Nodemailer

🔹Morgan

🔹Rate limit

🔹Dotenv

🔹Cors

## 2. Instalar dependencias de desarrollo (TypeScript + herramientas TS)

npm install -D typescript ts-node-dev @types/node @types/express @types/bcryptjs @types/jsonwebtoken @types/morgan @types/multer @types/cors

Esto instala:

typescript → lenguaje

ts-node-dev → ejecutar TS con recarga automática

Tipos: Node, Express, Cors, Multer, JWT, Morgan, Bcrypt…

## Ejecutar en desarrollo (con TypeScript y recarga automática):
npm run dev

## Compilar a JavaScript (para producción):
npm run build

## Ejecutar en producción (con JavaScript compilado):
npm start

## Crear archivo .env basado en .env.example:
PORT=5000
JWT_SECRET=tu_clave_secreta
URI_DB=mongodb+srv://usuario:pass@cluster.mongodb.net/dbname
EMAIL_USER=correo@gmail.com
EMAIL_PASS=contraseña_app


## 🔹Scripts disponibles

"scripts": {
  "dev": "ts-node-dev ./src/index.ts",   // Desarrollo
  "build": "tsc",                        // Compilación TS → JS
  "start": "node dist/index.js"          // Producción
}

## 🔹Instrucciones de uso

## 1. Registro e inicio de sesión
Para obtener el token JWT, primero registrarse:
POST /auth/register

## Luego iniciar sesión:
POST /auth/login
(El login devuelve un token JWT.)

## 2. Usar Token en rutas protegidas

Para crear, actualizar o eliminar productos:

Header:
Authorization: Bearer <token>

## 3. Subida de imágenes

Al crear o editar productos:

Enviar multipart/form-data

Campo de archivo: image

## 4. Filtros de productos

Puede filtrarse por:

/products?name=mouse
/products?category=tecnologia
/products?minPrice=100
/products?maxPrice=500
/products?stock=10


## 🔹 Endpoints:

## AUTH (Usuarios)

| Método | Ruta             | Descripción         | Body                                                     |
| ------ | ---------------- | ------------------- | -------------------------------------------------------- |
| POST   | `/auth/register` | Registrar usuario   | `{ "email": "waldoejemplo@gmail.com", "password": "123" }` |
| POST   | `/auth/login`    | Login y recibir JWT | `{ "email": "waldoejemplo@gmail.com", "password": "123" }` |


 ## 🔹 Productos

 | Método | Ruta            | Descripción                     | Body / Query Params                                               |
 | ------ | --------------- | ------------------------------- | ----------------------------------------------------------------- |
 | GET    | `/products`     | Listar todos los productos      | Query: `name`, `category`, `minPrice`, `maxPrice`, `stock`        |
 | GET    | `/products/:id` | Obtener producto por ID         | -                                                                 |
 | POST   | `/products`     | Crear producto (token JWT)      | `{ name, description, category, price, stock }` + imagen opcional |
 | PATCH  | `/products/:id` | Actualizar producto (token JWT) | `{ name?, description?, category?, price?, stock? }`              |
 | DELETE | `/products/:id` | Eliminar producto (token JWT)   | -                                                                 |
 
 ## 🔹 Envío de correo

 | Método | Ruta          | Descripción            | Body                                                                            |
| ------ | ------------- | ---------------------- | ------------------------------------------------------------------------------- |
| POST   | `/email/send` | Enviar correo al admin | `{ "subject": "Asunto", "email": "waldoejemplo@gmail.com", "message": "Contenido" }` |


## 🔹 Variables de entorno

PORT → Puerto del servidor

JWT_SECRET → Clave secreta para JWT

URI_DB → URI de conexión a MongoDB

EMAIL_USER → Correo para enviar emails

EMAIL_PASS → Contraseña de aplicación de correo

## 🔹 Notas importantes

Rutas de productos requieren token JWT para POST, PATCH y DELETE.

Se guarda log diario de todas las solicitudes en /logs.

Las imágenes de productos se suben a /uploads.
 
