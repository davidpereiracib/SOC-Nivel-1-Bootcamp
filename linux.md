# 🐧 Herramientas y Comandos para Threat Hunting en Linux

| Categoría                   | Herramienta/Comando | Descripción breve | Enlace |
|-----------------------------|---------------------|-------------------|--------|
| **Búsqueda de procesos**    | `ps aux`            | Lista todos los procesos activos con usuario, PID y consumo. | — |
|                             | `top` / `htop`      | Monitor interactivo de procesos y uso de recursos. | [htop](https://htop.dev/) |
|                             | `pstree`            | Muestra jerarquía de procesos. | — |
| **Análisis de red**         | `netstat -tulnp`    | Lista puertos abiertos y procesos asociados. | — |
|                             | `ss -tulwn`         | Alternativa moderna a netstat para sockets. | — |
|                             | `tcpdump`           | Captura tráfico de red para análisis. | [tcpdump](https://www.tcpdump.org/) |
|                             | `iftop`             | Muestra tráfico en tiempo real por conexión. | [iftop](https://www.ex-parrot.com/~pdw/iftop/) |
|                             | `nmap`              | Escaneo de puertos y servicios. | [nmap](https://nmap.org/) |
| **Registro y auditoría**    | `journalctl`        | Consulta logs del sistema (*systemd*). | — |
|                             | `last` / `lastlog`  | Muestra últimos inicios de sesión y fallos. | — |
|                             | `ausearch` / `aureport` | Busca y reporta eventos de *auditd*. | [auditd](https://linux.die.net/man/8/auditd) |
|                             | `syslog`            | Revisión de logs de sistema en `/var/log/`. | — |
| **Integridad de archivos**  | `aide`              | Verifica cambios no autorizados en el sistema. | [AIDE](https://aide.github.io/) |
|                             | `tripwire`          | Monitoreo de integridad de archivos. | [Tripwire](https://github.com/Tripwire/tripwire-open-source) |
| **Detección de rootkits**   | `chkrootkit`        | Escaneo de rootkits conocidos. | [chkrootkit](http://www.chkrootkit.org/) |
|                             | `rkhunter`          | Hunter de rootkits y backdoors. | [RKHunter](https://rkhunter.sourceforge.net/) |
| **Análisis de binarios**    | `file`              | Identifica tipo de archivo/binario. | — |
|                             | `strings`           | Extrae texto de binarios para análisis. | — |
|                             | `lsof`              | Lista archivos abiertos por procesos. | — |
| **Hunting de persistencia** | `crontab -l`        | Lista tareas programadas del usuario. | — |
|                             | `ls /etc/cron*`     | Verifica tareas programadas del sistema. | — |
|                             | `systemctl list-unit-files` | Lista servicios habilitados/deshabilitados. | — |
|                             | `systemctl status`  | Verifica estado de servicios. | — |
| **Análisis de usuarios**    | `id`                | Muestra UID/GID de usuario actual. | — |
|                             | `who` / `w`         | Lista usuarios conectados. | — |
|                             | `cat /etc/passwd`   | Lista cuentas del sistema. | — |
|                             | `cat /etc/shadow`   | Lista hashes de contraseñas (requiere root). | — |
| **Forense en memoria**      | `volatility`        | Análisis de memoria RAM en Linux. | [Volatility](https://www.volatilityfoundation.org/) |
|                             | `avml`              | Herramienta Microsoft para volcado de memoria. | [AVML](https://github.com/microsoft/avml) |
| **OSINT y análisis avanzado**| `maldetect`        | Escáner de malware para Linux. | [Linux Malware Detect](https://www.rfxn.com/projects/linux-malware-detect/) |
|                             | `yara`              | Reglas para detección de patrones maliciosos. | [YARA](https://virustotal.github.io/yara/) |
