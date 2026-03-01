<div align="center">

# VMWARE WORKSTATION PRO

### Marco Teórico — Configuración de Red en Máquinas Virtuales

**Juan Esteban Moreno Gamboa**<br>
**Fredy Oswaldo López Daza**<br>


**Docente:** Frey Alfonso Santamaría Buitrago — Ingeniero de Sistemas

**Universidad Pedagógica y Tecnológica de Colombia**<br>
Facultad de Ingeniería — Escuela de Ingeniería de Sistemas y Computación<br>
Electiva IaaS y Virtualización<br>
Tunja, 2026

</div>

---

## TABLA DE CONTENIDOS

- [LISTA DE FIGURAS](#lista-de-figuras)
- [LISTA DE TABLAS](#lista-de-tablas)
- [INTRODUCCIÓN](#introducción)
- [1. Virtualización de Escritorio: Principios y Plataformas](#1-virtualización-de-escritorio-principios-y-plataformas)
  - [1.1. El concepto de máquina virtual y el hipervisor](#11-el-concepto-de-máquina-virtual-y-el-hipervisor)
  - [1.2. Hipervisores de Tipo 1 y Tipo 2: diferencias y criterios de elección](#12-hipervisores-de-tipo-1-y-tipo-2-diferencias-y-criterios-de-elección)
  - [1.3. VMware Workstation Pro: definición, historia y posicionamiento](#13-vmware-workstation-pro-definición-historia-y-posicionamiento)
  - [1.4. El ecosistema de productos VMware](#14-el-ecosistema-de-productos-vmware)
  - [1.5. Modelo de licenciamiento: gratuito para uso personal desde 2024](#15-modelo-de-licenciamiento-gratuito-para-uso-personal-desde-2024)
- [2. Motor de Virtualización de VMware Workstation Pro](#2-motor-de-virtualización-de-vmware-workstation-pro)
  - [2.1. Virtualización asistida por hardware: Intel VT-x y AMD-V](#21-virtualización-asistida-por-hardware-intel-vt-x-y-amd-v)
  - [2.2. El Virtual Machine Monitor (VMM)](#22-el-virtual-machine-monitor-vmm)
  - [2.3. VMware Tools: integración y rendimiento del sistema invitado](#23-vmware-tools-integración-y-rendimiento-del-sistema-invitado)
- [3. Preparación del Entorno: Instalación y Configuración Inicial](#3-preparación-del-entorno-instalación-y-configuración-inicial)
  - [3.1. Requisitos del sistema anfitrión](#31-requisitos-del-sistema-anfitrión)
  - [3.2. Proceso de instalación en Windows](#32-proceso-de-instalación-en-windows)
  - [3.3. Interfaz de usuario: biblioteca de máquinas virtuales y menús principales](#33-interfaz-de-usuario-biblioteca-de-máquinas-virtuales-y-menús-principales)
- [4. Redes Virtuales en VMware Workstation Pro](#4-redes-virtuales-en-vmware-workstation-pro)
  - [4.1. Arquitectura de red virtual: conmutadores vmnet y el Virtual Network Editor](#41-arquitectura-de-red-virtual-conmutadores-vmnet-y-el-virtual-network-editor)
  - [4.2. Modo Bridged: integración directa con la red física](#42-modo-bridged-integración-directa-con-la-red-física)
  - [4.3. Modo NAT: conectividad a Internet con aislamiento de la red local](#43-modo-nat-conectividad-a-internet-con-aislamiento-de-la-red-local)
  - [4.4. Modo Host-Only: red privada entre máquinas virtuales y anfitrión](#44-modo-host-only-red-privada-entre-máquinas-virtuales-y-anfitrión)
  - [4.5. Redes personalizadas y segmentación avanzada](#45-redes-personalizadas-y-segmentación-avanzada)
  - [4.6. Adaptadores virtuales en el sistema anfitrión: VMnet1 y VMnet8](#46-adaptadores-virtuales-en-el-sistema-anfitrión-vmnet1-y-vmnet8)
  - [4.7. Configuración de direccionamiento IP en el sistema invitado](#47-configuración-de-direccionamiento-ip-en-el-sistema-invitado)
  - [4.8. Verificación de conectividad entre máquinas virtuales](#48-verificación-de-conectividad-entre-máquinas-virtuales)
- [5. Creación y Gestión de Máquinas Virtuales](#5-creación-y-gestión-de-máquinas-virtuales)
  - [5.1. Asistente de nueva máquina virtual](#51-asistente-de-nueva-máquina-virtual)
  - [5.2. Configuración de hardware virtual: CPU, memoria, disco y red](#52-configuración-de-hardware-virtual-cpu-memoria-disco-y-red)
  - [5.3. Clonación de máquinas virtuales](#53-clonación-de-máquinas-virtuales)
  - [5.4. Ciclo de vida de una máquina virtual](#54-ciclo-de-vida-de-una-máquina-virtual)
- [6. Almacenamiento Virtual: El Formato VMDK](#6-almacenamiento-virtual-el-formato-vmdk)
- [7. Instantáneas y Portabilidad](#7-instantáneas-y-portabilidad)
  - [7.1. Snapshots: instantáneas del estado de la máquina virtual](#71-snapshots-instantáneas-del-estado-de-la-máquina-virtual)
  - [7.2. Exportación e importación mediante OVF y OVA](#72-exportación-e-importación-mediante-ovf-y-ova)
- [8. Acceso y Consola de las Máquinas Virtuales](#8-acceso-y-consola-de-las-máquinas-virtuales)
- [9. Monitoreo de Recursos y Actividad de Red](#9-monitoreo-de-recursos-y-actividad-de-red)
- [REFERENCIAS BIBLIOGRÁFICAS](#referencias-bibliográficas)

---

## LISTA DE FIGURAS

| Figura | Descripción |
|--------|-------------|
| Fg. 1  | Interfaz principal de VMware Workstation Pro — biblioteca de máquinas virtuales |
| Fg. 2  | Virtual Network Editor — conmutadores vmnet configurados en el sistema |
| Fg. 3  | Adaptadores de red virtuales (VMnet1 y VMnet8) visibles en las interfaces de red de Windows |
| Fg. 4  | Comparativa gráfica del flujo de tráfico en los modos Bridged, NAT y Host-Only |
| Fg. 5  | Configuración del adaptador de red de una VM en modo NAT desde el editor de hardware virtual |
| Fg. 6  | Resultado de `ip addr show` en Ubuntu MATE — dirección IP asignada por DHCP en modo NAT |
| Fg. 7  | Configuración de IP estática en Ubuntu MATE mediante `nmcli` o el administrador de red gráfico |
| Fg. 8  | Verificación de conectividad entre dos máquinas virtuales con el comando `ping` |

> ⚠️ *Las capturas de pantalla deben tomarse durante la sesión de laboratorio y reemplazar los espacios indicados en el informe técnico. Actualizar la numeración si se añaden figuras adicionales.*

---

## LISTA DE TABLAS

| Tabla | Descripción |
|-------|-------------|
| Tabla 1 | Comparación entre hipervisores de Tipo 1 y Tipo 2 |
| Tabla 2 | Requisitos mínimos y recomendados del sistema anfitrión para VMware Workstation Pro |
| Tabla 3 | Comparativa de los modos de red disponibles en VMware Workstation Pro |
| Tabla 4 | Comparativa entre disco virtual dinámico y de tamaño fijo en formato VMDK |

---

## INTRODUCCIÓN

La virtualización es uno de los pilares tecnológicos sobre los que se construye la infraestructura de cómputo contemporánea. Desde los centros de datos empresariales hasta los laboratorios académicos, la capacidad de ejecutar múltiples sistemas operativos aislados sobre un único conjunto de hardware físico ha transformado radicalmente la manera en que se diseñan, despliegan y gestionan los entornos de tecnología de la información. En el contexto de la Infraestructura como Servicio (IaaS), la virtualización constituye el mecanismo fundamental que permite abstraer los recursos de cómputo, almacenamiento y red, ofreciéndolos de forma elástica y bajo demanda a los consumidores del servicio.

El presente documento expone el marco conceptual que sustenta el laboratorio práctico del grupo sobre VMware Workstation Pro, un hipervisor de tipo 2 cuyo énfasis en este trabajo recae en la configuración de red de máquinas virtuales para lograr conectividad con otros equipos, tanto físicos como virtuales. A diferencia de los hipervisores bare-metal estudiados por otros grupos de la electiva, VMware Workstation Pro opera sobre un sistema operativo anfitrión convencional, lo que lo hace especialmente apropiado para entornos de aprendizaje donde no se dispone de hardware de servidor dedicado, sin sacrificar por ello la riqueza funcional necesaria para comprender los principios de IaaS. El material se organiza desde los fundamentos de la virtualización y la clasificación de hipervisores, hasta los aspectos específicos de la arquitectura de red virtual de VMware, incluyendo los distintos modos de conectividad disponibles y los procedimientos de configuración aplicados durante el laboratorio.

---

## 1. Virtualización de Escritorio: Principios y Plataformas

### 1.1. El concepto de máquina virtual y el hipervisor

Una máquina virtual (VM) es una abstracción de software que emula el comportamiento de un equipo físico completo, incluyendo procesador, memoria, almacenamiento y dispositivos de entrada y salida, ejecutándose de forma aislada dentro de un sistema de cómputo real [1]. El software encargado de crear y gestionar estas abstracciones recibe el nombre de hipervisor o monitor de máquina virtual (VMM, por sus siglas en inglés). El hipervisor es responsable de arbitrar el acceso de las máquinas virtuales al hardware físico subyacente, garantizando al mismo tiempo el aislamiento entre ellas, de modo que el fallo o la actividad de una VM no afecte a las demás ni al sistema anfitrión.

La formalización matemática de las condiciones que debe cumplir un sistema para ser virtualizable fue propuesta por Gerald J. Popek y Robert P. Goldberg en 1974 en su influyente artículo "Formal requirements for virtualizable third generation architectures" [2]. Según este trabajo, un hipervisor debe proveer tres propiedades esenciales: equivalencia, es decir, que los programas ejecutados dentro de la VM se comporten de manera idéntica a como lo harían en hardware real; eficiencia, garantizando que la mayor parte de las instrucciones del sistema invitado se ejecuten directamente en el hardware sin intervención del hipervisor; y control de recursos, asegurando que el hipervisor mantenga siempre el control sobre los recursos físicos. Estas propiedades continúan siendo el criterio de referencia con el que se evalúa cualquier plataforma de virtualización moderna.

### 1.2. Hipervisores de Tipo 1 y Tipo 2: diferencias y criterios de elección

La industria clasifica los hipervisores en dos categorías principales según el nivel en que operan respecto al hardware y al sistema operativo del equipo físico. Esta clasificación es relevante para el presente laboratorio porque permite situar correctamente a VMware Workstation Pro dentro del panorama de plataformas estudiadas en la electiva.

Los hipervisores de **Tipo 1**, también denominados nativos o bare-metal, se instalan directamente sobre el hardware del servidor, sin la presencia de un sistema operativo anfitrión previo. Al tener acceso privilegiado directo al hardware, ofrecen el mayor rendimiento posible para las cargas de trabajo virtualizadas, junto con un aislamiento de seguridad más estricto, dado que la superficie de ataque se reduce notablemente al no existir un sistema operativo de propósito general por debajo. VMware ESXi, Proxmox Virtual Environment, Microsoft Hyper-V y KVM son ejemplos representativos de esta categoría [3]. Precisamente, Proxmox VE —estudiado por otro grupo de esta electiva— pertenece a esta clasificación.

Los hipervisores de **Tipo 2** u hosted se instalan sobre un sistema operativo anfitrión existente y se ejecutan como una aplicación más dentro de ese entorno. Su acceso al hardware está mediado por el propio sistema operativo del equipo, lo que introduce una capa adicional de software respecto a los hipervisores Tipo 1. Esta arquitectura implica una penalización moderada en rendimiento, pero ofrece ventajas considerables en facilidad de instalación y adopción, dado que puede implementarse sobre cualquier equipo de escritorio o portátil sin necesidad de hardware especializado ni particiones dedicadas. VMware Workstation Pro y Oracle VirtualBox son los representantes más conocidos de esta familia [3].

Tabla 1
*Comparación entre hipervisores de Tipo 1 y Tipo 2*

| Característica | Tipo 1 (Bare Metal) | Tipo 2 (Hosted) |
|----------------|---------------------|-----------------|
| Nivel de instalación | Directamente sobre el hardware físico | Sobre un sistema operativo anfitrión |
| Rendimiento | Máximo — acceso directo al hardware | Moderado — mediado por el SO anfitrión |
| Aislamiento de seguridad | Robusto — superficie de ataque reducida | Dependiente de la seguridad del SO anfitrión |
| Facilidad de instalación | Requiere hardware o partición dedicada | Se instala como una aplicación convencional |
| Entorno de uso típico | Centros de datos y servidores de producción | Desarrollo, laboratorio y formación técnica |
| Ejemplos | VMware ESXi, Proxmox VE, Hyper-V | VMware Workstation Pro, VirtualBox |

*Nota.* Elaboración propia a partir de [3][4].

En el contexto del proyecto integrador de la electiva, el conocimiento de ambas categorías resulta esencial: las VMs configuradas con VMware Workstation Pro en el laboratorio deben poder interactuar con instancias alojadas en plataformas Tipo 1 gestionadas por otros grupos, lo que exige una comprensión sólida de la configuración de red en ambos tipos de entorno.

### 1.3. VMware Workstation Pro: definición, historia y posicionamiento

VMware Workstation Pro es una aplicación de virtualización de escritorio desarrollada por VMware, Inc., empresa adquirida por Broadcom en noviembre de 2023. El producto fue lanzado en mayo de 1999 y se convirtió en el primer software comercial de virtualización para arquitectura x86 disponible en el mercado, marcando el inicio de la era moderna de la virtualización de propósito general [4]. Desde su primera versión, la plataforma ha sido el estándar de referencia en virtualización de escritorio para sistemas Windows y Linux, empleada tanto en la industria como en la academia por su estabilidad, amplitud funcional y fidelidad en la emulación del hardware virtual.

Funcionalmente, VMware Workstation Pro actúa como un intermediario entre el hardware físico del equipo anfitrión y los sistemas operativos invitados que corren dentro de las máquinas virtuales. Cada VM recibe un conjunto de dispositivos virtualizados estandarizados —procesador, memoria, disco, adaptadores de red, controladora USB— cuyo comportamiento es consistente independientemente del hardware real subyacente. Esta característica garantiza la portabilidad de las VMs entre equipos distintos, ya que el archivo de definición de la máquina virtual puede moverse o copiarse a otro equipo con VMware Workstation instalado y ejecutarse sin modificaciones. La plataforma soporta una amplia variedad de sistemas operativos invitados, incluyendo distribuciones Linux, versiones modernas de Windows, sistemas BSD y macOS con restricciones de licencia [1].

En el ámbito de esta práctica de laboratorio, VMware Workstation Pro se emplea para crear máquinas virtuales con Ubuntu MATE, configurar sus adaptadores de red en distintos modos de conectividad y verificar la comunicación entre instancias, lo que constituye la base técnica del proyecto integrador de la electiva.

### 1.4. El ecosistema de productos VMware

VMware, bajo la administración de Broadcom, mantiene una cartera de productos de virtualización que abarca desde el escritorio hasta la nube. Comprender este ecosistema permite situar a VMware Workstation Pro dentro de una jerarquía de herramientas cuyos conceptos son conceptualmente continuos, de modo que las habilidades adquiridas en el laboratorio resultan directamente transferibles a entornos de producción empresarial.

**VMware Workstation Pro** y su equivalente para macOS, **VMware Fusion Pro**, constituyen el extremo accesible del ecosistema, orientado a la virtualización en equipos personales. Fusion Pro incorpora las adaptaciones necesarias para los procesadores Apple Silicon (M1, M2, M3) con arquitectura ARM, manteniendo una experiencia funcional equivalente a la de Workstation Pro en sistemas Intel [5].

**VMware vSphere** es la plataforma de virtualización empresarial de VMware para centros de datos. Su hipervisor **ESXi** es un representante Tipo 1 que se instala directamente sobre servidores físicos; la gestión centralizada de múltiples hosts ESXi se realiza a través de **vCenter Server**, que habilita capacidades como la migración de VMs en vivo entre servidores físicos sin interrupción del servicio (*vMotion*) y la alta disponibilidad automática (*HA*) [6]. Los modos de red virtual aprendidos en Workstation Pro —Bridged, NAT, Host-Only y conmutadores personalizados— son equivalentes conceptuales de los *Standard vSwitch* y *Distributed vSwitch* de vSphere.

**VMware NSX** extiende la virtualización al plano de la red a escala de centro de datos, ofreciendo microsegmentación, firewalls distribuidos implementados en software, y redes superpuestas basadas en VXLAN y GENEVE [6]. Esta jerarquía ilustra que los principios de red virtual practicados con Workstation Pro en el laboratorio son la base conceptual de soluciones de infraestructura que operan a escala corporativa.

### 1.5. Modelo de licenciamiento: gratuito para uso personal desde 2024

En mayo de 2024, Broadcom anunció un cambio significativo en la política de distribución de VMware Workstation Pro y VMware Fusion Pro: ambos productos pasaron a estar disponibles de forma gratuita para uso personal, sin necesidad de licencia de pago [7]. Este cambio eliminó la barrera económica que previamente limitaba su adopción en contextos educativos e individuales. Para uso comercial, VMware Workstation Pro continúa requiriendo una suscripción activa a través del programa de licencias de Broadcom. En el contexto del presente laboratorio académico, la plataforma se utiliza bajo la modalidad de uso personal, lo que permite a los estudiantes instalarlo y practicar en sus propios equipos sin costo adicional.

---