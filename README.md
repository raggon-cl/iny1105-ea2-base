# Evaluación Parcial N°2 — Despliegue de Prometheus con Docker Compose y AWS ECS

**INY1105 — Infraestructura de Aplicaciones I**  
DuocUC · Escuela de Informática y Telecomunicaciones · 2026/1

---

## Instrucciones

### 1. Crea tu propio repositorio desde este template

1. Haz clic en el botón **"Use this template"** → **"Create a new repository"**
2. En el campo **Repository name** escribe: `iny1105-ea2-nombre-apellido` (usa tu nombre real)
3. Selecciona **Private**
4. Haz clic en **"Create repository"**

> **Importante:** El repositorio debe quedar en **tu cuenta personal** de GitHub, no en la cuenta del curso.  
> El nombre debe seguir el formato `iny1105-ea2-nombre-apellido` exactamente.

---

### 2. Clona tu repositorio y comienza a trabajar

```bash
git clone https://github.com/tu-usuario/iny1105-ea2-nombre-apellido.git
cd iny1105-ea2-nombre-apellido
```

---

### 3. Estructura del proyecto

```
iny1105-ea2-nombre-apellido/
├── Dockerfile             ← completar: FROM, LABEL, VOLUME, EXPOSE
├── docker-compose.yml     ← completar: Named Volume, Bind Mount y variable de entorno
├── config/
│   └── prometheus.yml     ← archivo de configuración base (ya configurado, no modificar)
├── .dockerignore          ← ya configurado
├── .gitignore             ← ya configurado
└── README.md              ← completar con instrucciones de uso
```

---

### 4. Flujo de trabajo

```
[1] Completar Dockerfile y docker-compose.yml
        ↓
[2] Validar localmente con Docker Compose
        ↓
[3] Publicar imagen en Amazon ECR
        ↓
[4] Desplegar en AWS ECS Fargate
        ↓
[5] Hacer push de tus cambios a GitHub con las evidencias
```

---

### 5. Comandos de validación local

```bash
# Construir la imagen
docker compose build

# Iniciar el servicio
docker compose up -d

# Verificar que está corriendo
docker compose ps

# Revisar logs en tiempo real
docker compose logs -f prometheus

# Verificar el Bind Mount (debe aparecer prometheus.yml)
ls -la ./config/

# Inspeccionar el Named Volume
docker volume inspect $(basename $(pwd))_prometheus_data
```

Accede a Prometheus en: **http://localhost:9090**

---

### 6. Entregables

Al finalizar, tu repositorio debe contener:

| # | Archivo / evidencia | Descripción |
|---|---|---|
| 1 | `Dockerfile` | Completado con FROM, LABEL, VOLUME y EXPOSE |
| 2 | `docker-compose.yml` | Completado con Named Volume, Bind Mount y variable de entorno |
| 3 | `README.md` | Completado con instrucciones de uso y variables de entorno |
| 4 | `evidencias/01_compose_ps.png` | Captura: `docker compose ps` con estado `running` |
| 5 | `evidencias/02_prometheus_local.png` | Captura: interfaz de Prometheus en `http://localhost:9090` |
| 6 | `evidencias/03_bind_mount.png` | Captura: contenido del directorio `./config/` en el host |
| 7 | `evidencias/04_named_volume.png` | Captura: salida de `docker volume inspect` |
| 8 | `evidencias/05_ecr_imagen.png` | Captura: imagen `prometheus-healthtrack:1.0.0` en la consola ECR |
| 9 | `evidencias/06_ecs_running.png` | Captura: tarea ECS en estado `RUNNING` con IP pública |
| 10 | `evidencias/07_prometheus_aws.png` | Captura: interfaz de Prometheus accesible desde la IP pública de ECS |

---

### 7. Subir tu trabajo

```bash
# Agregar todos los cambios
git add .
git commit -m "feat: Prometheus containerizado con persistencia dual - Nombre Apellido"

# Subir a tu repositorio
git push origin main
```

Luego, en el AVA:
1. Adjunta tu **reporte técnico en PDF**
2. Pega la **URL de tu repositorio GitHub** en el campo de texto de la tarea

---

*Docente: Rodrigo Aguilar G. — r.aguilarg@profesor.duoc.cl*
