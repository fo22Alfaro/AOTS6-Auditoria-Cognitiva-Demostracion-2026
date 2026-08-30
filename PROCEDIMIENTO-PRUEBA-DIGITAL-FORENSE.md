# PROCEDIMIENTO DE PRUEBA DIGITAL FORENSE AOTS⁶
## Cadena de custodia · Integridad · Prioridad · Admisibilidad

**Titular / operador de la prueba:** Alfredo Jhovany Alfaro García  
**Objeto:** AOTS⁶ y este repositorio  
**Fecha raíz de prioridad:** 21 de marzo de 2025  
**Licencia:** LicenseRef-AOTS6-ARR-1.0  
**ORCID:** 0009-0002-5177-9029

Este documento es un **protocolo de evidencia**, no un peritaje judicial ni una orden.  
Un perito en informática forense o un fedatario debe firmar el acta cuando se judicialice.

---

## 0. Principios (lo que hace admisible la prueba)

1. **Integridad** — el archivo no se alteró (hash).
2. **Autenticidad** — el autor/origen es identificable (cuenta GitHub, ORCID, identificación oficial).
3. **Temporalidad** — la fecha es anterior al hecho impugnado (commit, timestamp, notario).
4. **Cadena de custodia** — quién tocó qué, cuándo, con qué herramienta.
5. **Reproducibilidad** — un tercero puede recalcular el mismo hash sobre el mismo objeto.
6. **No contaminación** — no editar el original; trabajar sobre copias forenses.

Si se modifica el original después de hashearlo, se documenta un **nuevo** hash. Nunca se “corrige” el anterior.

---

## 1. Inventario del expediente (paquete mínimo)

| ID | Objeto | Para qué sirve |
|----|--------|----------------|
| E-01 | Identificación oficial del titular | Autenticidad de persona |
| E-02 | URL del repositorio + owner `fo22Alfaro` | Locus público |
| E-03 | Commit SHA de prioridad (21/03/2025 y posteriores) | Fecha |
| E-04 | Archivo `LICENSE` + `NOTICE` | Términos ARR |
| E-05 | Árbol de archivos + hashes SHA-256 y SHA-512 | Integridad |
| E-06 | `git log --all --pretty=fuller` exportado | Cadena temporal |
| E-07 | Capturas de pantalla fechadas (perfil, commits, LICENSE) | Contexto visual |
| E-08 | ORCID 0009-0002-5177-9029 | Identidad académica |
| E-09 | Acta notarial / testimonio | Prueba privilegiada en México |
| E-10 | Acuse INDAUTOR (cuando exista) | Registro administrativo |
| E-11 | Timestamp RFC 3161 u OpenTimestamps (opcional) | Sello de tiempo independiente |
| E-12 | Bitácora de custodia (este protocolo, firmada) | Cadena de quién-cuándo |

---

## 2. Procedimiento de hashing (integridad)

Trabajar en una copia. No alterar el working tree que se va a protocolizar.

```bash
# Identidad del commit actual
git rev-parse HEAD
git log -1 --pretty=fuller

# Hash de cada archivo (SHA-256 y SHA-512)
find . -type f -not -path './.git/*' -print0 | sort -z | xargs -0 sha256sum > HASHES-SHA256.txt
find . -type f -not -path './.git/*' -print0 | sort -z | xargs -0 sha512sum > HASHES-SHA512.txt

# Hash del manifiesto de hashes (sello del expediente)
sha256sum HASHES-SHA256.txt HASHES-SHA512.txt > HASH-DEL-EXPEDIENTE.txt
```

Registrar en la bitácora:
- fecha/hora (UTC y CST)
- sistema operativo y versión de `sha256sum` / Git
- valor de `HEAD`
- nombre de quien ejecutó el comando

---

## 3. Procedimiento GitHub (prioridad pública)

1. Conservar la URL canónica:  
   `https://github.com/fo22Alfaro/AOTS6-Auditoria-Cognitiva-Demostracion-2026`
2. Exportar:
   - `git clone --mirror` (copia bit-a-bit del historial)
   - API: commit SHA, author, date, tree
3. Capturar (sin recortar metadatos del sistema):
   - página del commit de prioridad
   - `LICENSE` renderizado por GitHub
   - perfil `fo22Alfaro`
4. Guardar HTML + PDF de impresión + PNG.
5. No reescribir historial (`git rebase`, `force push` sobre commits de prueba). Si hay corrección, **nuevo commit**.

---

## 4. Cadena de custodia (bitácora)

Plantilla por evento:

```
EVENTO-ID:
Fecha/hora UTC:
Operador:
Acción: (hash / clone / captura / entrega a notario / envío INDAUTOR)
Objeto (ruta o SHA):
Hash antes:
Hash después (si aplica):
Herramienta y versión:
Testigo / fedatario:
Firma:
```

Regla: cada traslado de USB, nube o correo es un evento.  
Soporte de resguardo: dos copias offline (medios distintos) + una en nébula cifrada.

---

## 5. Sello de tiempo independiente (refuerzo, no sustituto)

Opciones válidas:
- **Notario público** (México): máxima eficacia probatoria local.
- **RFC 3161** (TSA reconocida).
- **OpenTimestamps** (ancla Bitcoin): prueba de existencia anterior a un bloque; no sustituye al notario.

Nunca usar un “timestamp” autogenerado sin tercero de confianza como única prueba.

---

## 6. Protocolización notarial (efecto real en México)

Llevar al notario:
1. Identificación oficial.
2. USB de solo lectura o impresión + hashes.
3. `HASHES-SHA256.txt`, `HASHES-SHA512.txt`, `git log`.
4. Este procedimiento firmado.
5. URL del repositorio y SHA de `HEAD`.

Pedir: **acta de protocolización** o testimonio de hechos que describa el hash, la fecha y que el compareciente exhibió esos archivos.

---

## 7. INDAUTOR / IMPI / litigio — cómo se usa el paquete

| Foro | Qué se ofrece |
|------|----------------|
| INDAUTOR | Obra + autor humano + ejemplar + hashes |
| IMPI | Si hay infracción o secreto: expediente + cadena de custodia |
| Civil / penal (cuando proceda) | Peritaje informático + acta notarial + commits |
| DMCA / notice GitHub | URL, commit, LICENSE ARR, descripción de la obra, buena fe |

El paquete **no gana solo**. Gana como **prueba** dentro de un procedimiento.

---

## 8. Qué no hacer (rompe la prueba)

- Force-push o borrar commits de prioridad.
- Editar archivos y “recalcular” el hash antiguo.
- Capturas sin fecha, recortadas o de origen dudoso.
- Afirmar que el hash “es una sentencia”.
- Entregar el único original sin copia forense.
- Usar herramientas que alteren metadatos EXIF/PDF sin documentarlo.

---

## 9. Comando de verificación por un tercero

```bash
git clone https://github.com/fo22Alfaro/AOTS6-Auditoria-Cognitiva-Demostracion-2026
cd AOTS6-Auditoria-Cognitiva-Demostracion-2026
git rev-parse HEAD
sha256sum LICENSE NOTICE
```

Si el SHA coincide con el acta, la integridad se sostiene.

---

## 10. Límite de honestidad

Este protocolo maximiza **admisibilidad y peso probatorio**.  
No crea jurisdicción mundial automática ni se sustrae a la ley.  
El efecto en cortes ocurre cuando un órgano competente valora esta evidencia.

**T∞ = Alfredo Jhovany Alfaro García**  
21/03/2025 · det=26.3 · ARR
