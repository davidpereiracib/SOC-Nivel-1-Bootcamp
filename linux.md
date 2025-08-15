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

## 👤 Análisis de Usuarios

| Herramienta/Comando | Descripción | Enlace |
|---------------------|-------------|--------|
| `id`                | Muestra UID y GID del usuario actual. | — |
| `who` / `w`         | Lista usuarios conectados. | — |
| `cat /etc/passwd`   | Lista cuentas de usuario. | — |
| `cat /etc/shadow`   | Lista hashes de contraseñas (requiere root). | — |

---

## 🔐 Auditoría de Privilegios y Permisos

| Herramienta/Comando | Descripción | Enlace |
|---------------------|-------------|--------|
| `awk -F: '($3 == 0) {print $1}' /etc/passwd` | Lista cuentas con UID 0 (además de root). | — |
| `getent group sudo wheel admin` | Lista usuarios en grupos privilegiados. | — |
| `awk -F: '($2 == "" && $7 != "/usr/sbin/nologin") {print $1}' /etc/shadow` | Cuentas con shell válido pero sin contraseña. | — |
| `find / -type f \( -perm -4000 -o -perm -2000 \) -exec ls -l {} \; 2>/dev/null` | Busca archivos con bit SUID/SGID establecidos. | — |
| `find /etc -type f -perm -o+w -exec ls -l {} \;` | Detecta permisos débiles en archivos sensibles. | — |

# 🌐 Detección de Conexiones de Red Sospechosas en Linux

> Las conexiones de red sospechosas pueden indicar **C2**, **exfiltración de datos** o **movimiento lateral**.  
> Estos comandos y herramientas permiten identificar:
> - Conexiones a puertos o IPs inusuales  
> - Servicios escuchando en puertos no estándar  
> - Conexiones salientes desde usuarios/procesos inesperados  
> - Patrones de comunicación periódicos (*beaconing*)  
> - Volúmenes anómalos de tráfico  

| Herramienta / Comando | Descripción | Uso principal | Enlace |
|-----------------------|-------------|--------------|--------|
| `ss -tulwnp`          | Lista puertos en escucha y conexiones activas con PID/usuario. | Detectar servicios y procesos sospechosos. | — |
| `netstat -tulnp`      | Alternativa a `ss` para mostrar conexiones y procesos asociados. | Puertos abiertos no estándar. | — |
| `lsof -i`             | Lista procesos que tienen conexiones de red abiertas. | Identificar procesos inusuales con actividad de red. | — |
| `iftop`               | Monitor de tráfico en tiempo real por conexión. | Detección de grandes volúmenes de tráfico. | [🔗 iftop](https://www.ex-parrot.com/~pdw/iftop/) |
| `iptraf-ng`           | Interfaz interactiva para monitorear conexiones y tráfico. | Análisis visual del tráfico. | [🔗 iptraf-ng](https://linux.die.net/man/8/iptraf-ng) |
| `tcpdump`             | Captura paquetes para inspección detallada. | Análisis de contenido y patrones. | [🔗 tcpdump](https://www.tcpdump.org/) |
| `nload`               | Monitor de ancho de banda entrante y saliente. | Detectar tráfico inusual o picos. | [🔗 nload](https://github.com/rolandriegel/nload) |
| `nethogs`             | Muestra uso de ancho de banda por proceso. | Identificar aplicaciones con alto consumo. | [🔗 nethogs](https://github.com/raboof/nethogs) |
| `tshark`              | Versión CLI de Wireshark para captura y análisis. | Filtrar patrones de beaconing. | [🔗 Wireshark](https://www.wireshark.org/) |
| `ngrep`               | Busca cadenas en tráfico de red en tiempo real. | Detección de indicadores C2 en texto plano. | [🔗 ngrep](https://github.com/jpr5/ngrep) |
| `sar -n DEV 1 5`      | Muestra estadísticas de red por interfaz. | Detectar anomalías en volumen de tráfico. | [🔗 sysstat](https://github.com/sysstat/sysstat) |
| `conntrack -L`        | Lista todas las conexiones rastreadas por netfilter. | Identificar conexiones persistentes o inusuales. | — |
