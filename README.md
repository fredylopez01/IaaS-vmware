<div align="center">

# VMware Workstation Pro — Documentación

**Juan Esteban Moreno Gamboa**<br>
**Fredy Oswaldo López Daza**

---

**Docente:** Frey Alfonso Santamaría Buitrago — Ingeniero de Sistemas

**Universidad Pedagógica y Tecnológica de Colombia**<br>
Facultad de Ingeniería — Escuela de Ingeniería de Sistemas y Computación<br>
Electiva IaaS y Virtualización<br>
Tunja, 2026

</div>

---

## Descripción

Este repositorio contiene la documentación completa del laboratorio sobre **VMware Workstation Pro**, desarrollado en el marco de la electiva de **Infraestructura como Servicio (IaaS) y Virtualización**. El trabajo tiene como eje central la configuración de red en máquinas virtuales con Ubuntu MATE, abordando los modos NAT, Host-Only y Bridged, y la comunicación entre instancias como base para el proyecto integrador de la electiva.

---

## Documentos

### Marco Teórico

> **Archivo:** [marco-teorico-vmware.md](marco-teorico-vmware.md)

Documento de investigación que expone los fundamentos conceptuales de la virtualización de escritorio y la arquitectura de red virtual de VMware Workstation Pro. Abarca desde la clasificación de hipervisores (Tipo 1 y Tipo 2), el motor de virtualización asistida por hardware y el ecosistema de productos VMware, hasta la descripción detallada de los modos de red disponibles (Bridged, NAT, Host-Only y redes personalizadas), la gestión de máquinas virtuales, el almacenamiento virtual en formato VMDK y los mecanismos de instantáneas y portabilidad.

---

### Informe Técnico

> **Archivo:** [informe-tecnico-vmware.md](informe-tecnico-vmware.md)

Informe técnico que documenta paso a paso el desarrollo del laboratorio: instalación de VMware Workstation Pro, creación de una VM con Ubuntu MATE, exploración del Virtual Network Editor, configuración y prueba de los tres modos de red con sus resultados reales de conectividad, comunicación entre dos máquinas virtuales por Host-Only y por Bridged, gestión de instantáneas y monitoreo de red. Incluye capturas de pantalla, comandos ejecutados, IPs obtenidas y una tabla resumen de resultados.

---

## Estructura del Repositorio

```
vmware-docs/
├── README.md                   # Este archivo
├── marco-teorico-vmware.md     # Fundamentos teóricos
├── informe-tecnico-vmware.md   # Informe técnico final
└── images/                     # Capturas de pantalla del laboratorio
```