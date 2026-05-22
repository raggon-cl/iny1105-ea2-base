# Evaluación Parcial N°2 — Despliegue de Prometheus con Docker Compose y AWS ECS

**INY1105 — Infraestructura de Aplicaciones I**  
DuocUC · Escuela de Informática y Telecomunicaciones · 2026/1

---

## Instrucciones

### 1. Crea tu rama de trabajo

Clona este repositorio y crea una rama con tu nombre antes de escribir cualquier código:

```bash
git clone https://github.com/raggon-cl/iny1105-ea2-base.git
cd iny1105-ea2-base
git checkout -b nombre-apellido
```

> **Importante:** todo tu trabajo debe quedar en tu rama. No hagas commits directamente en `main`.

---

### 2. Estructura del proyecto

```
iny1105-ea2-base/
├── Dockerfile             ← completar: FROM, LABEL, VOLUME, EXPOSE
├── docker-compose.yml     ← completar: Named Volume, Bind Mount y variable de entorno
├── config/
│   └── prometheus.yml     ← archivo de configuración base (ya configurado, no modificar)
├── .dockerignore          ← ya configurado
├── .gitignore             ← ya configurado
└── README.md              ← completar con instrucciones de uso
```

---

### 3. Flujo de trabajo

```
[1] Completar Dockerfile y docker-compose.yml
        ↓
[2] Validar localmente con Docker Compose
        ↓
[3] Publicar imagen en Amazon ECR
        ↓
[4] Desplegar en AWS ECS Fargate
        ↓
[5] Hacer push de tu rama a GitHub con las evidencias
```

---

### 4. Comandos de validación local

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
docker volume inspect iny1105-ea2-base_prometheus_data
```

Accede a Prometheus en: **http://localhost:9090**

---

### 5. Entregables

Al finalizar, tu rama debe contener:

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

Crea el directorio `evidencias/` en tu rama y agrega las capturas antes de hacer push.

---

### 6. Subir tu trabajo

```bash
# Agregar todos los cambios
git add .
git commit -m "feat: Prometheus containerizado con persistencia dual - Nombre Apellido"

# Subir tu rama
git push origin nombre-apellido
```

---

*Docente: Rodrigo Aguilar G. — r.aguilarg@profesor.duoc.cl*
