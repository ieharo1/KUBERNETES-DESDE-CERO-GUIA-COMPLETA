# ☸️ KUBERNETES DESDE CERO - GUÍA COMPLETA

**Kubernetes desde Cero** es un sitio educativo completo diseñado para enseñar Kubernetes desde los fundamentos hasta conceptos avanzados, con explicaciones claras, ejemplos prácticos y código listo para usar.

> *"Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services."*

---

## 🎯 ¿Qué es este Proyecto?

Este proyecto proporciona un recurso educativo gratuito para aprender Kubernetes, incluyendo:

- **Documentación completa** de cada tema
- **Ejemplos de código** listos para ejecutar
- **Ejercicios prácticos** para reforzar el aprendizaje
- **Sitio web educativo** con navegación intuitiva

---

## 📚 Contenido del Curso

### Módulo 1: Fundamentos

1. **Introducción**
   - ¿Qué es Kubernetes?
   - Contenedores y orquestación
   - Arquitectura de Kubernetes

2. **Instalación**
   - Minikube para desarrollo local
   - kubectl CLI
   - Kind (Kubernetes in Docker)
   - Cloud providers (GKE, EKS, AKS)

3. **Conceptos básicos**
   - Pods
   - Deployments
   - Services
   - Namespaces

### Módulo 2: Intermedio

4. **Ejemplos prácticos**
   - ConfigMaps y Secrets
   - Volumes y PersistentVolume
   - Ingress y networking
   - Health checks (liveness/readiness)

5. **Buenas prácticas**
   - Resource limits y requests
   - Security contexts
   - Network policies
   - Helm charts

### Módulo 3: Avanzado

6. **Casos reales**
   - StatefulSets para stateful apps
   - DaemonSets
   - Jobs y CronJobs
   - Auto-scaling (HPA/VPA)

7. **Proyecto final**
   - Aplicación completa en K8s
   - CI/CD con Kubernetes
   - Monitoring con Prometheus

---

## 🗂️ Estructura del Proyecto

```
Practica-Nro14/
├── index.html          # Página principal
├── css/
│   └── styles.css      # Estilos del sitio
├── js/
│   └── main.js         # JavaScript del sitio
└── README.md
```

---

## 🚀 Cómo Usar este Proyecto

### Opción 1: Navegar el Sitio Web

1. Abre `index.html` en tu navegador
2. Navega por las secciones del curso
3. Haz clic en los temas para ver la documentación detallada

### Opción 2: Ejecutar los Ejemplos

1. Instala Minikube y kubectl
2. Aplica manifests con `kubectl apply`
3. Verifica con `kubectl get`

### Requisitos

- Minikube o cluster Kubernetes
- kubectl instalado
- Docker instalado

---

## 📝 Ejemplos Rápidos

### Pod Básico

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mi-pod
  labels:
    app: web
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

### Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mi-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: nginx
        image: nginx:1.21
        ports:
        - containerPort: 80
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"
```

### Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: mi-servicio
spec:
  selector:
    app: web
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: LoadBalancer
```

### ConfigMap y Secret

```yaml
# ConfigMap
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  DATABASE_URL: "postgres://localhost:5432/db"
  LOG_LEVEL: "info"

# Secret
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
type: Opaque
stringData:
  API_KEY: "mi-clave-secreta"
```

### Ingress

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: mi-ingress
spec:
  rules:
  - host: mi-app.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: mi-servicio
            port:
              number: 80
```

---

## 🎓 Metodología de Aprendizaje

### 1. Leer la Teoría
Cada tema comienza con una explicación clara del concepto.

### 2. Ver Ejemplos
Los ejemplos de código muestran la aplicación práctica.

### 3. Practicar
Los ejercicios te permiten aplicar lo aprendido.

### 4. Experimentar
Modifica los ejemplos para entender cómo funcionan.

---

## 🔧 Comandos Esenciales

### kubectl

```bash
# Ver información del cluster
kubectl cluster-info

# Listar pods
kubectl get pods

# Listar deployments
kubectl get deployments

# Aplicar manifest
kubectl apply -f archivo.yaml

# Eliminar recurso
kubectl delete -f archivo.yaml

# Ver logs
kubectl logs <pod-name>

# Ejecutar comando en pod
kubectl exec -it <pod-name> -- /bin/bash

# Port forwarding
kubectl port-forward <pod-name> 8080:80
```

---

## 📖 Recursos Adicionales

### Documentación Oficial

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
- [Kubernetes GitHub](https://github.com/kubernetes/kubernetes)

### Herramientas Recomendadas

- **Minikube** - Kubernetes local
- **Kind** - Kubernetes en Docker
- **Helm** - Package manager
- **Lens** - IDE para Kubernetes

### Comunidades

- [Kubernetes Community](https://kubernetes.io/community/)
- [Stack Overflow - Kubernetes](https://stackoverflow.com/questions/tagged/kubernetes)
- [Reddit r/kubernetes](https://www.reddit.com/r/kubernetes/)

---

## 💡 Consejos para Principiantes

1. **Empieza con Minikube**: Es más simple para aprender.
2. **Entiende Pods**: Son la unidad básica.
3. **Usa labels**: Facilitan la gestión.
4. **Configura recursos**: Evita problemas de memoria.
5. **Aprende troubleshooting**: `kubectl describe` es tu amigo.

---

## ⚠️ Mejores Prácticas

### Seguridad

- Usa RBAC para permisos
- No uses latest tags en producción
- Implementa network policies

### Rendimiento

- Configura requests y limits
- Usa affinity rules cuando sea necesario
- Implementa horizontal pod autoscaling

### Producción

- Usa múltiples réplicas
- Configura health checks
- Implementa backup de etcd

---

## 🧪 Ejercicios Prácticos

### Nivel Básico

1. Crea tu primer pod
2. Despliega una aplicación con Deployment
3. Expón servicio con Service

### Nivel Intermedio

1. ConfigMap y Secrets en acción
2. Ingress con routing múltiple
3. PersistentVolume para datos

### Nivel Avanzado

1. StatefulSet con base de datos
2. Auto-scaling con HPA
3. Cluster completo con Helm

---

## 👨‍💻 Desarrollado por Isaac Esteban Haro Torres

**Ingeniero en Sistemas · Full Stack · Automatización · Data**

- 📧 Email: zackharo1@gmail.com
- 📱 WhatsApp: 098805517
- 💻 GitHub: https://github.com/ieharo1
- 🌐 Portafolio: https://ieharo1.github.io/portafolio-isaac.haro/

---

© 2026 Isaac Esteban Haro Torres - Todos los derechos reservados.
