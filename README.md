# Security Automation with Python and Linux CLI

Description: A Python-based log parser that automates SOC triage by filtering failed authentication events in Linux.
Descripción: Un analizador de logs en Python que automatiza el triaje del SOC filtrando eventos de autenticación fallida en Linux.

================================================================================
Laboratorio: Automatización de Seguridad con Python y Linux CLI
================================================================================

1. Información General
--------------------------------------------------------------------------------
* Fecha: 2026-06-17
* Autor: Yung Lee
* Objetivo: Desarrollar un script automatizado en Python para analizar logs del sistema y detectar intentos de acceso no autorizados.

2. Marco Ético y Legal
--------------------------------------------------------------------------------
Este laboratorio se realizó en un entorno de virtualización completamente aislado. Todos los scripts y registros están controlados y simulados contra recursos propios, cumpliendo con los protocolos de ética en ciberseguridad y las pautas de trabajo práctico supervisado.

3. Objetivo del Laboratorio
--------------------------------------------------------------------------------
* Crear una estructura de scripting en Python para interactuar con logs basados en texto de Linux.
* Implementar lógica condicional (sentencias if) para filtrar el ruido de fondo e aislar eventos de seguridad críticos (FAILED).

4. Topología y Entorno
--------------------------------------------------------------------------------
* Sistema Operativo: Kali Purple (Kali Linux).
* IP del Objetivo: 192.168.1.100 (Interfaz local eth0).
* Herramientas: Python 3, Linux CLI, Editor Nano.

5. Metodología
--------------------------------------------------------------------------------
* 5.1 Fase de Preparación: Verificación de la dirección IP local usando ip a para alinear los segmentos de red y preparación de datos estructurados de simulación.
* 5.2 Fase de Ejecución (Simulación): Creación de un flujo de logs simulados mediante la redirección de la terminal (>) y apertura segura de archivos en Python con with open.
* 5.3 Fase de Análisis (Detección): Implementación de un filtro lógico de strings para inspeccionar cada renglón y discriminar eventos de éxito frente a amenazas activas.

6. Resultados y Evidencias
--------------------------------------------------------------------------------

6.1 Fase de Preparación
Verificación del direccionamiento IP real en la interfaz de red activa mediante la CLI de Linux:
comando: ip a
Resultado en terminal: Interfaz eth0 operando bajo la dirección IP 192.168.1.100/24.

6.2 Fase de Ejecución (Simulación)
Generación del archivo de registros simulados reflejando accesos fallidos y exitosos:
comando: echo -e "IP: 192.168.1.50 - FAILED\nIP: 192.168.1.100 - SUCCESS" > falsos_logs.txt

6.3 Fase de Análisis (Detección)
Creación y ejecución del script de automatización lector.py:

with open("falsos_logs.txt", "r") as archivo:
    for linea in archivo:
        if "FAILED" in linea:
            print(f"[ALERTA SOC] Intento sospechoso detectado: {linea.strip()}")

Salida final obtenida en la consola de Kali Linux, demostrando el funcionamiento del filtro:
└─$ python3 lector.py
[ALERTA SOC] Intento sospechoso detectado: IP: 192.168.1.50 - FAILED

7. Conclusiones y Remediación
--------------------------------------------------------------------------------
* Conclusiones: La revisión manual de registros consume tiempo crítico. La integración de scripts básicos en Python permite optimizar el triaje en el SOC aislando alertas de forma instantánea.
* Remediación (En Progreso): El script actual lee y detecta los fallos. La fase de remediación automatizada requerirá extraer la IP del atacante mediante código para inyectarla directamente en las reglas del firewall de Linux (iptables).

8. Referencias
--------------------------------------------------------------------------------
* Python Software Foundation. (2026). Input and Output: Reading and Writing Files. [https://docs.python.org/3/tutorial/inputoutput.html](https://docs.python.org/3/tutorial/inputoutput.html)
* Linux Documentation Project. (2026). I/O Redirection Fundamentals. [https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)
