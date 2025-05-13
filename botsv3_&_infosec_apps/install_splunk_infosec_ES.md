
# Guía de Instalación de Splunk InfoSec

Este documento proporciona una guía completa, paso a paso, para instalar **Splunk InfoSec**, basada en las mejores prácticas y recomendaciones oficiales de Splunk. Su objetivo es ayudar a los analistas de seguridad y arquitectos a implementar una solución InfoSec potente y escalable de manera eficiente.

---

## Tabla de Contenidos

- [Descripción General de Splunk InfoSec](#overview-of-splunk-infosec)
  - [Características Clave](#key-features)
  - [Beneficios](#benefits)
- [Quién Debería Implementar Splunk InfoSec](#who-should-deploy-splunk-infosec)
- [Acerca del Conjunto de Datos Boss of the SOC (BOTS) Versión 3](#about-boss-of-the-soc-bots-dataset-version-3)
- [Aplicaciones Prerrequisito](#prerequisite-apps)
- [Requisitos del Sistema y Prerrequisitos](#system-requirements-and-prerequisites)
- [Instalación de la Aplicación Splunk InfoSec y el Conjunto de Datos BOTS v3](#installing-the-splunk-infosec-app--bots-v3-dataset)
- [Fin de la Guía](#end-of-guide)

---

## Descripción General de Splunk InfoSec

Splunk InfoSec es una solución de seguridad de vanguardia que aprovecha las capacidades de análisis de datos de Splunk para proporcionar información de seguridad integral y detección de amenazas en tiempo real. Es esencial para las organizaciones que buscan fortalecer su postura de ciberseguridad en el dinámico panorama de amenazas actual.

### Características Clave

- **Monitoreo y Análisis en Tiempo Real**: Monitoreo continuo de flujos de datos para la detección y respuesta a amenazas en tiempo real.
- **Detección Avanzada de Amenazas**: Integración con Splunk Machine Learning Toolkit (MLTK) para correlación de amenazas basada en ML y alertas.
- **Investigación de Incidentes y Forense**: Herramientas para investigación detallada y forense.
- **Cumplimiento y Reportes**: Ayuda en el cumplimiento normativo con herramientas de reporte extensas.

### Beneficios

- **Mejora de la Postura de Seguridad**: Identificación proactiva de amenazas utilizando análisis avanzados.
- **Operaciones Simplificadas**: Gestión centralizada de operaciones de seguridad.
- **Escalabilidad y Flexibilidad**: Adecuado para organizaciones de todos los tamaños.
- **Detección y Respuesta Rápida a Amenazas**: Minimiza el daño mediante acciones rápidas.
- **Inteligencia Operativa**: Obtén información estratégica y optimiza los procesos de seguridad.

---

## Quién Debería Implementar Splunk InfoSec

Splunk InfoSec está diseñado para alinear **personas, procesos y herramientas**, ofreciendo:

- **Eficiencia para Recursos Limitados**: Ideal para equipos de seguridad pequeños.
- **Mejora de Habilidades**: Simplifica tareas complejas a través de interfaces intuitivas.
- **Plataforma de Seguridad Integral**: Centraliza la detección, respuesta y reporte de amenazas.
- **Integración y Personalización**: Se integra sin problemas con la infraestructura existente.
- **Libretos de Respuesta a Incidentes**: Ayuda en la creación y refinamiento de libretos de respuesta a incidentes.
- **Flujos de Trabajo Automatizados**: Asegura el manejo de incidentes repetible y documentado.

---

## Acerca del Conjunto de Datos Boss of the SOC (BOTS) Versión 3

Un conjunto de datos de seguridad de muestra y una plataforma CTF para profesionales de seguridad de la información, investigadores, estudiantes y entusiastas.

### Acerca de las Aplicaciones Prerrequisito de BOTS v3

El conjunto de datos requiere las siguientes aplicaciones que se distribuyen y licencian por separado y **deben instalarse antes de usar el conjunto de datos**. Estamos utilizando diferentes versiones de aplicaciones del uso originalmente previsto del conjunto de datos y algunas cosas pueden no funcionar correctamente, pero funcionará bien para propósitos de laboratorio. Más información sobre BOTS v3 se puede encontrar [aquí](https://github.com/splunk/botsv3).

---

## Aplicaciones Prerrequisito

Antes de implementar Splunk InfoSec, instala las siguientes aplicaciones prerrequisito:

| Aplicación | Propósito | Beneficio | Enlace |
|:----|:--------|:--------|:-----|
| **Splunk Common Information Model (CIM)** | Normaliza y categoriza datos | Datos consistentes y procesables en todas las fuentes | [Splunkbase](https://splunkbase.splunk.com/app/1621) |
| **Punchcard - Custom Visualization** | Visualización de patrones temporales | Identifica tendencias/anomalías fácilmente | [Splunkbase](https://splunkbase.splunk.com/app/3129) |
| **Force Directed App for Splunk** | Visualización de gráficos de relaciones | Descubre patrones ocultos en redes | [Splunkbase](https://splunkbase.splunk.com/app/3767) |
| **Splunk App for Lookup File Editing** | Edita archivos de búsqueda | Mejora la precisión y eficiencia en el manejo de datos | [Splunkbase](https://splunkbase.splunk.com/app/1724) |
| **Splunk Sankey Diagram - Custom Visualization** | Visualización de flujo e interacción | Comprende el movimiento de datos y relaciones | [Splunkbase](https://splunkbase.splunk.com/app/3112) |
| **Splunk Security Essentials (SSE)** | Ejemplos de casos de uso e ideas | Acelera el despliegue de seguridad | [Splunkbase](https://splunkbase.splunk.com/app/3435) |
| **Alert Manager Add-on** | Mejora la gestión de alertas | Mejora la clasificación de alertas y la respuesta a incidentes | [Splunkbase](https://splunkbase.splunk.com/app/3365) |
| **Alert Manager** | Extiende el marco de alertas | Gestión integral del ciclo de vida de alertas | [Splunkbase](https://splunkbase.splunk.com/app/2665) |

Antes de implementar el conjunto de datos BOTS v3, instala las siguientes aplicaciones prerrequisito:

| Aplicación / Complemento | Propósito | Beneficio | Enlace |
|:----|:--------|:--------|:-----|
| **Amazon GuardDuty Add-on for Splunk** | Proporciona objetos de conocimiento para datos de GuardDuty a través de Amazon CloudWatch Events. | Mejora la detección de amenazas integrando conocimientos de GuardDuty en Splunk. | [Splunkbase](https://splunkbase.splunk.com/app/3790/) |
| **Cisco Endpoint Security Analytics (CESA)** | Analiza y correlaciona el comportamiento de usuarios y puntos finales en Splunk Enterprise. | Proporciona mayor visibilidad en comportamientos de puntos finales con contexto como usuario, dispositivo y ubicación. | [Splunkbase](https://splunkbase.splunk.com/app/2992/) |
| **Code42 App For Splunk** | Integra Splunk y Code42 para la correlación de datos de puntos finales y copias de seguridad. | Mejora la protección de datos y las ideas de recuperación. | [Splunkbase](https://splunkbase.splunk.com/app/3736/) |
| **Code42ForSplunk Technology Add-On** | Proporciona un complemento técnico para Code42 App for Splunk. | Facilita la ingesta e indexación de datos para Code42. | [Splunkbase](https://splunkbase.splunk.com/app/3746/) |
| **DecryptCommands** | Proporciona comandos para rutinas Base32, Base64, XOR, ROTX, RC4 y ROL/ROR. | Útil para descifrar comunicaciones de malware ofuscadas. | [Splunkbase](https://splunkbase.splunk.com/app/2655/) |
| **ES Content Updates** | Ofrece contenido de seguridad preempaquetado para Splunk Enterprise Security. | Mantiene el contenido de seguridad actualizado con los últimos métodos de detección de amenazas. | [Splunkbase](https://splunkbase.splunk.com/app/3449/) |
| **Microsoft Azure Active Directory Reporting Add-on for Splunk** | Recoge datos de Microsoft Azure, incluidos datos de usuario, inicios de sesión y auditorías. | Mejora la supervisión y los informes de cumplimiento para entornos de Azure. | [Splunkbase](https://splunkbase.splunk.com/app/3757/) |
| **Microsoft Cloud App for Splunk** | Proporciona paneles para datos de Microsoft 365. | Mejora la visibilidad y gestión de servicios de Microsoft 365. | [Splunkbase](https://splunkbase.splunk.com/app/3786/) |
| **Microsoft Office 365 Reporting Add-on for Splunk** | Recoge datos de seguimiento de mensajes de Microsoft Office 365. | Mejora la seguridad del correo electrónico y la supervisión del cumplimiento. | [Splunkbase](https://splunkbase.splunk.com/app/3720/) |
| **Microsoft Sysmon Add-on** | Proporciona entrada de datos y extracciones de campo compatibles con CIM para Microsoft Sysmon. | Mejora la creación de procesos y la supervisión de conexiones de red. | [Splunkbase](https://splunkbase.splunk.com/app/1914/) |
| **OSquery App for Splunk** | Permite la recopilación remota de datos de clientes osquery. | Actúa como un servidor de gestión osquery para mejorar la visibilidad de puntos finales. | [Splunkbase](https://splunkbase.splunk.com/app/3902/) |
| **Splunk Add-on for Cisco ASA** | Mapea eventos de dispositivos Cisco ASA al CIM de Splunk. | Facilita la integración con otras aplicaciones de Splunk para una supervisión de seguridad integral. | [Splunkbase](https://splunkbase.splunk.com/app/1620/) |
| **Splunk Add-on for Microsoft Cloud Services** | Extrae datos de varios servicios en la nube de Microsoft. | Mejora la supervisión y el cumplimiento de servicios en la nube. | [Splunkbase](https://splunkbase.splunk.com/app/3110/) |
| **Splunk Add-on for Microsoft Office 365** | Recoge el estado del servicio y los registros de actividad de gestión de Office 365. | Mejora la supervisión y el cumplimiento para entornos de Office 365. | [Splunkbase](https://splunkbase.splunk.com/app/4055/) |
| **Splunk Add-on for Microsoft Windows** | Recoge datos de sistemas Windows y los normaliza al CIM. | Mejora la visibilidad y la supervisión de entornos Windows. | [Splunkbase](https://splunkbase.splunk.com/app/742/) |
| **Splunk Add-on for Symantec Endpoint Protection** | Recoge registros de actividad de servidores y clientes SEP. | Mejora la supervisión de seguridad de puntos finales y la detección de amenazas. | [Splunkbase](https://splunkbase.splunk.com/app/2772/) |
| **Splunk Add-on for Tenable** | Recoge datos de escaneo de vulnerabilidades de Tenable. | Mejora la gestión de vulnerabilidades y los informes de cumplimiento. | [Splunkbase](https://splunkbase.splunk.com/app/1710/) |
| **Splunk Add-on for Unix and Linux** | Proporciona información sobre entornos Unix y Linux. | Mejora la visibilidad operativa y la supervisión del rendimiento. | [Splunkbase](https://splunkbase.splunk.com/app/833/) |
| **Splunk Stream Add-on** | Captura y analiza datos de tráfico de red. | Mejora la visibilidad de la red y el análisis forense. | [Splunkbase](https://splunkbase.splunk.com/app/1809/) |
| **Splunk Add-on for AWS** | Recoge datos de servicios AWS para integración en Splunk. | Mejora la supervisión y el cumplimiento de servicios en la nube. | [Splunkbase](https://splunkbase.splunk.com/app/1876/) |
| **SA-cim_vladiator** | Valida la conformidad CIM de complementos tecnológicos. | Simplifica el proceso de validación y asegura la conformidad del modelo de datos. | [Splunkbase](https://splunkbase.splunk.com/app/2968/) |
| **URL Toolbox** | Proporciona herramientas para la manipulación y análisis de URLs. | Mejora el análisis de seguridad con capacidades avanzadas de análisis de URLs. | [Splunkbase](https://splunkbase.splunk.com/app/2734/) |
| **TA-VirusTotalActions** | Proporciona acciones de flujo de trabajo para VirusTotal. | Mejora la inteligencia de amenazas integrando conocimientos de VirusTotal. | [Splunkbase](https://splunkbase.splunk.com/app/3446/) |
| ---- | -------- | -------- | ----- |
| **Splunk Common Information Model** | Normaliza y categoriza datos | --**ya instalado con InfoSec**-- | [Splunkbase](https://splunkbase.splunk.com/app/1621/) |
| **Splunk Security Essentials**  | Ejemplos de casos de uso e ideas | --**ya instalado con InfoSec**-- | [Splunkbase](https://splunkbase.splunk.com/app/3435/) |

---

## Requisitos del Sistema y Prerrequisitos

### Compatibilidad del Kernel de Linux

- **General**: Se admiten la mayoría de las distribuciones modernas de Linux.
- **Recomendado**: Sigue [Requisitos del Sistema Operativo de Splunk](https://docs.splunk.com/Documentation/Splunk/latest/Installation/Systemrequirements#Supported_Operating_Systems).
- **Kernel Personalizado**: Puede requerir configuración adicional.

### Requisitos Mínimos de Hardware

| Recurso | Requisitos Mínimos |
|:---------|:----------------------|
| Procesador | CPU de cuatro núcleos (x64) |
| Memoria | 16 GB de RAM |
| Almacenamiento | 500 GB de espacio en disco (se recomienda SSD) |
| Red | Red interna de 1 Gbps |

### Dependencias de Software Requeridas

- **Sistema Operativo**: Linux actualizado (Ubuntu, CentOS, RHEL).
- **Entorno de Ejecución de Java**: JRE 8 o posterior (para funcionalidades específicas).
- **Splunk Enterprise**: Última versión compatible con Splunk InfoSec.

> **Nota**: Abre los puertos necesarios siguiendo las pautas y mejores prácticas de Splunk.

### Recomendaciones Adicionales

- Escala el hardware para implementaciones más grandes.
- Implementa un firewall e IDS.
- Mantén copias de seguridad regulares de los datos de Splunk.

---

## Instalación de la Aplicación Splunk InfoSec y el Conjunto de Datos BOTS v3

### Prerrequisitos

Asegúrate de que Splunk Enterprise esté instalado y en funcionamiento. Verifica el estado de la instalación:

```
su splunkuser
```
```
/opt/splunk/bin/splunk status
```

Si Splunk no está en funcionamiento, inícialo usando:

```
/opt/splunk/bin/splunk start
```

### Instalación Paso a Paso

#### Método 1: Instalar a través de Splunk Web

1. **Accede a Splunkbase:**
   - Visita [Splunkbase](https://splunkbase.splunk.com).
   - Busca "Splunk InfoSec App" y descárgala junto con todas las aplicaciones prerrequisito.

2. **Sube la Aplicación a Splunk:**
   - Inicia sesión en tu interfaz web de Splunk.
   - Navega a **Apps** > **Manage Apps**.
   - Haz clic en **Install app from file**.
   - Selecciona el paquete de la aplicación descargada y haz clic en **Upload**.

3. **Verifica la Instalación:**
   - Asegúrate de que las aplicaciones estén listadas bajo **Apps**.

4. **Instalación de BOTS v3:**
   - Descarga el conjunto de datos BOTS v3:
     ```bash
     wget https://botsdataset.s3.amazonaws.com/botsv3/botsv3_data_set.tgz
     ```
   - Descomprime/desempaqueta el archivo descargado en `$SPLUNK_HOME/etc/apps`:
     ```bash
     sudo tar -xvf botsv3_data_set.tgz -C /opt/splunk/etc/apps/
     ```
   - Asegúrate de que el usuario correcto tenga la propiedad de los directorios y archivos utilizados por Splunk:
     ```bash
     sudo chown -R splunkuser:splunkuser /opt/splunk
     ```

#### Método 2: Instalar a través de la Línea de Comandos

1. **Detén Splunk:**
   ```bash
   /opt/splunk/bin/splunk stop
   ```

2. **Descarga y Extrae las Aplicaciones:**
   Crea un directorio de descargas:
   ```bash
   sudo mkdir /opt/downloads
   ```
   ```bash
   cd /opt/downloads/
   ```
   Clona el repositorio o descarga manualmente:
   ```bash
   git clone https://github.com/artioli/splunk.git
   ```
   ```bash
   cd /opt/downloads/botsv3_&_infosec_apps/
   ```

3. **Descarga el Conjunto de Datos BOTS v3:**
   ```bash
   wget https://botsdataset.s3.amazonaws.com/botsv3/botsv3_data_set.tgz
   ```

4. **Extrae los Archivos:**
   ```bash
   for file in *.tgz; do
       tar -xf "$file" -C /opt/splunk/etc/apps/
   done
   ```

5. **Asigna la Propiedad:**
   ```bash
   sudo chown -R splunkuser:splunkuser /opt/splunk
   ```

6. **Inicia Splunk:**
   ```bash
   /opt/splunk/bin/splunk start
   ```

7. **Verifica la Importación de Datos:**
   Abre Splunk Web y busca el conjunto de datos usando:
     ```
     index=botsv3 earliest=0
     ```
   - Asegúrate de que los datos sean accesibles.
   - > **Nota** que este conjunto de datos no cuenta contra los límites de licencia de Splunk debido a su naturaleza preindexada.

8. **Configuración de InfoSec:**

   - Todos los datos utilizados por la aplicación InfoSec deben ser compatibles con el Common Information Model (CIM). 
   - Los siguientes Modelos de Datos deben ser acelerados:
      - Authentication
      - Change
      - Intrusion_Detection
      - Malware
      - Network_Sessions
      - Network_Traffic
      - Endpoint
      - Web

   - Pasos
      - En Splunk Web, ve a **Settings > Data Models**.
      - Para cada modelo de datos arriba, selecciona **Edit > Edit Acceleration**; **Summary Range > All Time** y **Save**.
      - > **Nota** Al acelerar modelos de datos a *All Time*, asegúrate de que esto solo se haga en un entorno de laboratorio controlado. En producción, considera el impacto en el rendimiento y el almacenamiento.

   - Consulta los [Documentación de Splunk® InfoSec App](https://docs.splunk.com/Documentation/InfoSec) para instrucciones detalladas.

---

## Fin de la Guía
