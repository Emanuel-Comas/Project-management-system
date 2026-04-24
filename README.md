# 📌 Sistema de Gestión de Proyectos

Sistema backend desarrollado con **NestJS** como trabajo integrador académico.  
El objetivo del sistema es permitir la gestión simple de **proyectos, clientes y tareas**, con autenticación de usuarios.

---

## 🚀 Tecnologías utilizadas

- NestJS
- TypeScript
- TypeORM
- PostgreSQL
- JWT (autenticación)
- bcrypt (encriptación de contraseñas)
- Swagger (documentación API)
- class-validator / class-transformer
- Compodoc (documentación automática del código)

---

## 🔐 Autenticación

El sistema cuenta con acceso mediante usuarios registrados.

Cada usuario posee:
- Nombre de usuario
- Contraseña encriptada
- Estado: Activo / Baja

Solo usuarios válidos pueden acceder al sistema mediante login.

---

## 📁 Módulos del sistema

### 📌 Gestión de Proyectos

Permite:
- Crear proyectos
- Editar proyectos
- Ver detalle de proyectos
- Ver tareas asociadas
- Asociar cliente (opcional)

Cada proyecto tiene:
- Nombre
- Estado: Activo / Finalizado / Baja
- Cliente asociado (opcional)
- Tareas asociadas

---

### 👤 Gestión de Clientes

Permite:
- Crear clientes
- Editar clientes
- Asociarlos a proyectos

Cada cliente tiene:
- Nombre
- Estado: Activo / Baja

📌 Regla importante:
- Un cliente solo puede darse de baja si **no está asociado a ningún proyecto**

---

### 📝 Gestión de Tareas

Permite:
- Crear tareas dentro de un proyecto
- Editar tareas
- Eliminar tareas

Cada tarea tiene:
- Descripción
- Estado: Pendiente / Finalizado / Baja

---

## 🔎 Reglas del sistema

- Todos los usuarios pueden ver todos los proyectos, clientes y tareas
- No existen propietarios de registros
- Los clientes pueden ser opcionales en proyectos (proyectos internos)
- Solo clientes activos pueden asignarse a proyectos
- Validaciones de estado en todas las entidades

---


## 📚 Documentación

### 📌 API (Swagger)

La documentación de la API está disponible en:
```
    http://localhost:3000/api
```

### 📌 Código (Compodoc)

La documentación del código del proyecto se genera con Compodoc:

```bash
npx @compodoc/compodoc -p tsconfig.json -s
```

Luego se puede acceder en:

```
http://localhost:8080
```



---

## 🛠️ Instalación y ejecución

```
-- bash
# instalar dependencias
npm install

# levantar en desarrollo
npm run start:dev

# build producción
npm run build

# ejecutar tests
npm run test
```


## Variables de entorno

Crear un archivo .env en la raíz del backend:

    DB_HOST=
    DB_PORT=
    DB_USER=
    DB_PASSWORD=
    DB_NAME=

    JWT_SECRET=
    JWT_EXPIRES_IN=


## Estructura del proyecto


```
└── 📁backend
    └── 📁src
        └── 📁modulos
            └── 📁auth
                └── 📁controller
                    ├── auth.controller.ts
                └── 📁dtos
                    └── 📁input
                        ├── login.dto.ts
                └── 📁entitites
                └── 📁enums
                    ├── estados-usuarios.enum.ts
                └── 📁guards
                └── 📁services
                ├── auth.module.ts
            └── 📁gestion
                └── 📁controller
                    ├── clientes.controller.ts
                    ├── proyectos.controller.ts
                    ├── tareas.controllers.ts
                └── 📁dtos
                    └── 📁input
                        ├── create-cliente.dto.ts
                        ├── create-proyecto.dto.ts
                        ├── create-tarea.dto.ts
                        ├── update-cliente.dto.ts
                        ├── update-proyecto.dto.ts
                        ├── update-tarea.dto.ts
                    └── 📁output
                        ├── list-cliente.dto.ts
                        ├── list-proyecto.dto.ts
                        ├── list-tarea.dto.ts
                        ├── proyecto.dto.ts
                └── 📁entitites
                    ├── cliente.entity.ts
                    ├── proyecto.entity.ts
                    ├── tarea.entity.ts
                └── 📁enums
                    ├── estados-clientes.enum.ts
                    ├── estados-proyectos.enum.ts
                    ├── estados-tareas.enum.ts
                └── 📁services
                    ├── tarea.service.ts
                ├── gestion.module.ts
        ├── app.controller.spec.ts
        ├── app.module.ts
        └── main.ts
```


## Notas importantes

    -- El sistema está construido como API REST
    -- No hay frontend incluido
    -- Toda la lógica está centralizada en el backend
    -- Se utiliza validación con DTOs
    -- Seguridad con JWT