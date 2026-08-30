# CADENA DE CUSTODIA DIGITAL — LISTO PARA NOTARIO

Expediente: AOTS⁶  
Titular: Alfredo Jhovany Alfaro García  
Repositorio: https://github.com/fo22Alfaro/AOTS6-Auditoria-Cognitiva-Demostracion-2026

## Datos a protocolizar

| Campo | Valor |
|-------|-------|
| Titular | Alfredo Jhovany Alfaro García |
| ORCID | 0009-0002-5177-9029 |
| Fecha raíz de divulgación | 21 de marzo de 2025 |
| URL | https://github.com/fo22Alfaro/AOTS6-Auditoria-Cognitiva-Demostracion-2026 |
| Licencia | LicenseRef-AOTS6-ARR-1.0 |

## Procedimiento ante notario

1. Exhibir identificación oficial del titular.
2. Exhibir captura de la URL del repositorio y del commit HEAD (SHA).
3. Entregar listado de hashes SHA-256 de archivos críticos (LICENSE, NOTICE, marcos legales, este protocolo).
4. Solicitar **fe de hechos** o protocolización del expediente digital.
5. Conservar testimonio y copia certificada en resguardo offline.

## Bitácora (llenar en cada exportación)

| Fecha UTC | Persona | Acción | Herramienta | Hash / SHA commit | Firma |
|-----------|---------|--------|-------------|-------------------|-------|
| | | | | | |

## Comandos de verificación (referencia)

```
git rev-parse HEAD
git log -1 --format=%H%n%cI%n%s
sha256sum LICENSE NOTICE README.md
```

La cadena de custodia documenta **quién tocó qué y cuándo**. Sin ella, el hash pierde valor procesal.
