# Parte 3: Programación del servidor con Node.js

Ejercicios correspondientes a la [Parte 3](https://fullstackopen.com/es/part3) del curso Full Stack Open.

## Objetivo

Aprender a construir un servidor REST con Node.js y Express, conectarlo a una base de datos MongoDB, desplegarlo en la nube con Render y aplicar buenas prácticas de código con ESLint y validaciones con Mongoose.

## Demo en producción

🔗 [https://phonebook-backend-yd0v.onrender.com](https://phonebook-backend-yd0v.onrender.com)

---

## Ejercicios

### [phonebook-backend](./phonebook-backend/)
**Ejercicios 3.1 – 3.22**

Backend completo de la agenda telefónica construido con Node.js, Express y MongoDB.

#### Parte a — Node.js y Express (3.1–3.8)
- Servidor REST con Express
- Endpoints: GET, POST, DELETE para `/api/persons`
- Página `/info` con conteo de contactos y fecha
- Validaciones básicas (nombre único, campos requeridos)
- Logging de peticiones HTTP con Morgan (incluyendo body en POST)

#### Parte b — Deploy a Internet (3.9–3.11)
- Middleware `cors` para permitir peticiones cross-origin
- Build del frontend de la Parte 2 servido como archivos estáticos desde el backend
- Deploy completo (frontend + backend) en [Render](https://render.com)

#### Parte c — MongoDB (3.12–3.18)
- Conexión a MongoDB Atlas con Mongoose
- Modelo `Person` con esquema definido y transformación `toJSON`
- Script `mongo.js` standalone para listar y agregar contactos desde terminal
- Operaciones CRUD completas contra MongoDB: GET, POST, PUT, DELETE
- Manejo de errores con middleware centralizado (`CastError`, `ValidationError`)

#### Parte d — Validación y ESLint (3.19–3.22)
- Validación de nombre: mínimo 3 caracteres (`minLength`)
- Validación de número con expresión regular: formato `XX-XXXXXXXX` o `XXX-XXXXXXXX`, mínimo 8 caracteres
- Validadores habilitados en operaciones `findByIdAndUpdate` con `runValidators: true`
- Configuración de ESLint con reglas de estilo (`eqeqeq`, `no-trailing-spaces`, `object-curly-spacing`, `arrow-spacing`)
- Código sin advertencias de ESLint

---

## Lo aprendido

Esta parte fue la más completa del curso hasta ahora. Construir el backend desde cero con Node.js y Express ayudó a entender cómo funciona realmente el ciclo HTTP: la petición llega al servidor, pasa por los middlewares, llega al controlador de la ruta, interactúa con la base de datos y regresa la respuesta.

MongoDB y Mongoose introdujeron el concepto de base de datos NoSQL con documentos flexibles. La diferencia más importante con un array en memoria es la persistencia: los datos sobreviven a reinicios del servidor.

El deploy en Render con la variable de entorno `MONGODB_URI` enseñó la diferencia entre configuración local (`.env`) y configuración de producción, y por qué nunca se deben subir credenciales a GitHub.

---

## Desafíos técnicos superados

- Resolver problemas de conectividad DNS con MongoDB Atlas en la red local (ISP bloqueando registros SRV), solucionado usando la connection string estándar sin SRV
- Configurar correctamente el middleware de archivos estáticos para servir el frontend desde el backend
- Manejar el `.gitignore` para incluir la carpeta `dist` del backend en GitHub sin afectar el frontend
- Habilitar validadores de Mongoose en operaciones de actualización (`runValidators`, `context: 'query'`)
- Configurar ESLint con el nuevo formato de configuración plana (`eslint.config.mjs`)