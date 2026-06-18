# Security Automation with Python and Linux CLI

##  Language / Idioma
* [English Version](#-english-version)
* [Versión en Español](#-versión-en-español)

---

## 🇺🇸 English Version

### **1. General Information**
* **Project Name:** Security Automation with Python and Linux CLI
* **Target Role:** Junior Cybersecurity Technician / SOC Analyst
* **Core Technologies:** Python 3, Linux CLI (Bash), Log Analysis, Automation

### **2. Laboratory Description**
This laboratory demonstrates the practical application of Python to automate a critical Security Operations Center (SOC) task: log parsing and triage. Manually auditing large volume log files is inefficient and prone to human error. To solve this, a Python script was developed to automatically parse authentication logs, isolate critical failure events (`FAILED`), and generate a clean, structured security report.

### **3. Script Implementation (Python)**
```python
import os

def parse_security_logs(log_path, report_path):
    print("[*] Starting security log analysis...")
    if not os.path.exists(log_path):
        print(f"[-] Error: Target log file '{log_path}' not found.")
        return
        
    try:
        with open(log_path, 'r') as infile, open(report_path, 'w') as outfile:
            failed_count = 0
            outfile.write("=== SOC TRIAGE REPORT: RECENT SECURITY FAILURES ===\n")
            
            for line in infile:
                if "FAILED" in line.upper():
                    outfile.write(line)
                    failed_count += 1
                    
            outfile.write("==================================================\n")
            outfile.write(f"[+] Analysis Completed. Total critical failures isolated: {failed_count}\n")
            print(f"[+] Success! Isolated {failed_count} events into '{report_path}'.")
            
    except Exception as e:
        print(f"[-] Unexpected error processing files: {e}")

if __name__ == "__main__":
    # Example paths matching standard Linux structures
    TARGET_LOG = "falsos_logs.txt"
    SECURITY_REPORT = "security_alerts_report.txt"
    parse_security_logs(TARGET_LOG, SECURITY_REPORT)

    4. Skills Demonstrated
Log Triage Automation: Replaced manual text filtering with a scalable script architecture.

Defensive Scripting: Implemented exception handling (try-except) and file path validations (os.path.exists).

SIEM/SOC Readiness: Prepared analytical foundations for parsing complex log fields (timestamps, IPs, and user accounts).

🇪🇸 Versión en Español
1. Información General
Nombre del Proyecto: Automatización de Seguridad con Python y Linux CLI

Rol Objetivo: Técnico de Ciberseguridad Junior / Analista SOC

Tecnologías Clave: Python 3, CLI de Linux (Bash), Análisis de Logs, Automatización

2. Descripción del Laboratorio
Este laboratorio demuestra la aplicación práctica de Python para automatizar una tarea crítica dentro de un Centro de Operaciones de Seguridad (SOC): el procesamiento y triaje de logs. Auditar manualmente archivos de registro masivos es ineficiente y propenso a errores humanos. Para resolver esto, se desarrolló un script en Python que analiza registros de autenticación, aísla eventos críticos de fallo (FAILED) y genera un reporte de seguridad limpio y estructurado.

3. Implementación del Script (Python)

import os

def parse_security_logs(log_path, report_path):
    print("[*] Iniciando el análisis de logs de seguridad...")
    if not os.path.exists(log_path):
        print(f"[-] Error: No se encontró el archivo de logs '{log_path}'.")
        return
        
    try:
        with open(log_path, 'r') as infile, open(report_path, 'w') as outfile:
            failed_count = 0
            outfile.write("=== REPORTE TRIAJE SOC: FALLOS DE SEGURIDAD RECIENTES ===\n")
            
            for line in infile:
                if "FAILED" in line.upper():
                    outfile.write(line)
                    failed_count += 1
                    
            outfile.write("=========================================================\n")
            outfile.write(f"[+] Análisis Finalizado. Total de fallos críticos aislados: {failed_count}\n")
            print(f"[+] ¡Éxito! Se aislaron {failed_count} eventos en '{report_path}'.")
            
    except Exception as e:
        print(f"[-] Error inesperado al procesar los archivos: {e}")

if __name__ == "__main__":
    # Rutas de ejemplo alineadas con estructuras estándar de Linux
    TARGET_LOG = "falsos_logs.txt"
    SECURITY_REPORT = "security_alerts_report.txt"
    parse_security_logs(TARGET_LOG, SECURITY_REPORT)

    4. Habilidades Demostradas
Automatización de Triaje de Logs: Reemplazo del filtrado manual de texto por una arquitectura de script escalable.

Programación Defensiva: Implementación de manejo de excepciones (try-except) y validaciones de rutas del sistema (os.path.exists).

Preparación para Entornos SIEM/SOC: Creación de bases analíticas para procesar campos complejos de logs (marcas de tiempo, IPs y cuentas de usuario).