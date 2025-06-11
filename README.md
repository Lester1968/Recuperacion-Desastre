# 💥 Packet Tracer: Recuperación ante Desastres en Infraestructura de Red

## 📘 Descripción
Este laboratorio práctico simula un escenario de desastre en la red, donde un switch ha fallado y se deben aplicar procedimientos de respaldo y restauración para recuperar la operación. Se utilizan comandos CLI estándar y un servidor TFTP para realizar la restauración completa del entorno de red.

## 🎯 Objetivos
- Revisar configuraciones activas y de inicio de un switch.
- Realizar copias de seguridad hacia un servidor TFTP.
- Sustituir un switch fallido por uno de repuesto.
- Restaurar la configuración y operatividad de la red.

## 🛠️ Requisitos
- Cisco Packet Tracer.
- Topología del laboratorio con switches y servidor TFTP.
- Conocimiento de comandos IOS (CLI) en switches Cisco.

---

## 🧪 Desarrollo del Laboratorio

### 🔍 Parte 1: Revisión de configuración del switch original

- **Tamaño del archivo de configuración**:  
  `dir nvram`
- **VLANs configuradas en MDF-1**:  
  `show vlan`
- **IP VLAN 99 y gateway predeterminado**:  
  `show running-config`
- **VLAN asignada a F0/1 y configuración de troncal G0/1**:  
  `show run`

### 📦 Parte 2: Copia de respaldo a servidor TFTP

- **Dirección IP del servidor TFTP**:  
  `ipconfig`
- **Copiar archivo vlan.dat**:  
  `copy flash:tftp` → nombre sugerido: `MDF-1_vlan.dat`
- **Copiar archivo startup-config**:  
  `copy startup-config tftp` → nombre sugerido: `MDF-1_startup-config`

### 🔁 Parte 3: Sustitución del switch fallido

- Instalar `spare-switch_01`.
- Reconectar cables siguiendo el diseño original.
- Verificar puertos físicos con tabla de conexiones.

### 🔄 Parte 4: Restauración de operación de red

- **Restaurar vlan.dat desde TFTP**:  
  `copy tftp flash`
- **Verificar archivo en flash**:  
  `dir flash`
- **Restaurar configuración de inicio**:  
  `copy tftp startup-config`
- **Verificar archivo en NVRAM**:  
  `dir nvram`
- **Confirmar tamaño de configuración restaurada**.
- **Recargar switch (sin guardar cambios)**:  
  `reload` → responder "no"
- **Verificaciones finales**:
  - `show running-config`: Hostname debe ser `MDF-1`
  - `show vlan`: VLANs restauradas
  - `show ip interface brief`: Interfaces físicas activas

---

## 📸 Capturas recomendadas

Coloca en la carpeta `/capturas/` imágenes de:

- Configuración VLANs antes/después
- Comandos de copia TFTP
- Verificación de interfaces

## 👨‍💻 Autor
**Lester Dávila**  
Laboratorio desarrollado dentro del plan de formación en redes y ciberseguridad.

## 📄 Licencia
Este proyecto está licenciado bajo la Licencia MIT.  
Consulta el archivo [LICENSE](LICENSE) para más detalles.
