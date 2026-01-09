# Mis proyectos

Aquí puedes ver los proyectos en los que estoy trabajando. Se irán actualizando a medida que avance en mi aprendizaje de ciberseguridad.

---

## Proyecto actual


!!! tip ":material-account-circle-outline: Proyecto principal"
    **Nombre:** hybrid-soc-lab

    **Repositorio:** [github.com/moabdib2000/hybrid-soc-lab](https://github.com/moabdib2000/hybrid-soc-lab)  
    **Estado:** 🟡 En desarrollo  
    **Descripción:** Laboratorio SOC Híbrido: Phishing + Respuesta a Incidentes (Enfoque L1) Enfoque: SOC Nivel 1: Detección de Phishing y Triaje de Incidentes Qué busca este laboratorio: Análisis de alertas, decisiones de triaje, criterios de escalamiento y documentación de incidentes.

    ### Arquitectura general
    ```mermaid
    graph TD
        P[Proxmox VE<br/><small>Host Físico: Mac Mini 2016</small>]

        W["Endpoint Windows 10/11<br>Agente Wazuh<br>Simulación de phishing"]
        K["Kali Linux<br>Herramientas simulación controlada<br>"]
        C["MITRE CALDERA<br>Emulación de adversarios<br>Validación de detección"]
        WAZ["Wazuh Manager<br>SIEM / XDR<br>Genera alertas"]
        IRIS["DFIR-IRIS<br>Gestión de casos<br>Respuesta a incidentes"]
        SH["Shuffle - Fase 2<br>SOAR - Automatización<br>Enriquecimiento"]
        TI["OpenCTI o MISP - Fase 3<br>Inteligencia de amenazas<br>IOCs"]

        CLOSED["Alerta cerrada<br>Falso positivo<br>Sin escalado"]
        ESCALATED["Escalado a L2<br>Amenaza real"]
        REPORT["Incidente cerrado<br>Reporte final generado"]

        P --> W
        P --> K
        P --> C
        P --> WAZ
        P --> IRIS
        P --> SH
        P --> TI

        W -->|Logs y eventos| WAZ
        K -->|Ataques manuales| W
        C -->|Comportamiento malicioso| W
        WAZ -->|Alertas| IRIS
        WAZ -->|Alertas| SH
        SH -->|Flujos automatizados| IRIS
        SH -->|Consultas IOC| TI
        TI -->|Contexto de inteligencia| IRIS

        IRIS -->|Decisión de triaje| CLOSED
        IRIS -->|Decisión de triaje| ESCALATED
        IRIS -->|Tras resolución| REPORT

        style P stroke:#666,stroke-width:3px,fill:none
        style W stroke:#0066cc,stroke-width:3px,fill:none
        style K stroke:#cc0000,stroke-width:3px,fill:none
        style C stroke:#cc0000,stroke-width:3px,fill:none
        style WAZ stroke:#00aa00,stroke-width:3px,fill:none
        style IRIS stroke:#00aa00,stroke-width:3px,fill:none
        style SH stroke:#00aa00,stroke-width:3px,stroke-dasharray: 5 5,fill:none
        style TI stroke:#00aa00,stroke-width:3px,stroke-dasharray: 5 5,fill:none
        style CLOSED stroke:#999,stroke-width:2px,fill:none
        style ESCALATED stroke:#ff6600,stroke-width:3px,fill:none
        style REPORT stroke:#00aa00,stroke-width:3px,fill:none

    ```
