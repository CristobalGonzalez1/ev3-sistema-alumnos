# Registro de seguridad · Sistema Alumnos

Estudiante: Cristobal Gonzalez   Repositorio: https://github.com/CristobalGonzalez1/ev3-sistema-alumnos.git   Fecha: 23-11-2026

Completa este registro a medida que avanzas. Cada fila debe poder seguirse hasta un **build de Jenkins**
y un **commit** (usa el identificador `VULN-xx` en el mensaje del commit).

## 1. Revisiones de seguridad realizadas

| # | Etapa del SDLC | Herramienta / técnica | Build | Resultado (resumen) |
|---|---|---|---|---|
| R1 | Código (SAST) | Bandit en el pipeline | #__ | __ hallazgos High / __ Medium / __ Low |
| R2 | Dependencias (SCA) | pip-audit en el pipeline | #__ | __ vulnerabilidades en __ paquetes |
| R3 | Pruebas dinámicas (DAST) | OWASP ZAP sobre staging | #__ | __ High / __ Medium / __ Low |
| R4 | Revisión manual | Lectura de `app.py` | — | |
| R5 | Producción | Grafana + Prometheus | — | |

## 2. Vulnerabilidades identificadas y corregidas

| ID | Vulnerabilidad (CWE) | Detectada por | Ubicación | Riesgo | Corrección aplicada | Commit | Build que lo verifica |
|---|---|---|---|---|---|---|---|
| VULN-01 | SQL Injection (CWE-89, B608) | Bandit | app.py, /alumnos/buscar | Medio | Consultas parametrizadas con SQLite | VULN-01 | #6 |
| VULN-02 | Hash MD5 inseguro (CWE-327, B324) | Bandit | app.py, /login | Alto | Se reemplazó MD5 por hash scrypt y check_password_hash() | VULN-01 | #6 |
| VULN-03 | Clave secreta fija (CWE-259, B105) | Bandit | app.py, SECRET_KEY | Bajo | Se utiliza FLASK_SECRET_KEY desde variable de entorno | VULN-01 | #6 |
| VULN-04 | Debug habilitado (CWE-94, B201) | Bandit | app.py, app.run() | Alto | Se desactivó debug=True | VULN-01 | #6 |
| VULN-05 | Exposición de interfaces (CWE-605, B104) | Bandit | app.py, app.run() | Medio | Se configuró FLASK_HOST con 127.0.0.1 por defecto | VULN-01 | #6 |
| VULN-06 | Cross-Site Scripting (CWE-79) | Revisión manual | app.py, /hello | Alto | Se incorporó escape() de MarkupSafe | VULN-01 | #6 |



## 3. Resultados de OWASP ZAP

| Alerta de ZAP | Riesgo | URL de ejemplo | VULN relacionada | Cómo se mitiga | ¿Mitigada? Build |
|---|---|---|---|---|---|
| | | | | | |

## 4. Monitoreo e incidentes

| Hora | Panel / métrica de Grafana | Qué se observó | Entorno | Clasificación | Acción de respuesta | Verificación |
|---|---|---|---|---|---|---|
| | | | | | | |

## 5. Gestión de dependencias

| Paquete | Versión inicial | Vulnerabilidades (IDs) | Versión final | Origen del cambio (PR de Dependabot / manual) | ¿Pruebas, pip-audit y ZAP siguen OK? Build |
|---|---|---|---|---|---|
| Flask | 2.2.2 | | | | |
| Werkzeug | 2.2.2 | | | | |
| Jinja2 | 3.1.2 | | | | |
| gunicorn | 21.2.0 | | | | |
| prometheus-client | 0.17.1 | | | | |

## 6. Trazabilidad

Pega aquí (o adjunta) el `TRAZABILIDAD.md` del último build y completa un recorrido por cada actividad del pipeline:

| Actividad | Hallazgo | Build que lo detectó | Commit / PR que lo resolvió | Build que lo verificó | Versión en producción |
|---|---|---|---|---|---|
| Revisión de seguridad (Bandit) | | #__ | | #__ | |
| Prueba automatizada (OWASP ZAP) | | #__ | | #__ | |
| Gestión de dependencias (Dependabot) | | #__ | PR #__ | #__ | |
