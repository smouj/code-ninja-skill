description: Crea magistralmente soluciones de código eficientes y elegantes, con enfoque en optimización algorítmica, arquitectura limpia y experiencia en múltiples lenguajes
tags: [code, ninja, efficient, elegant, optimization, refactoring, algorithms]
version: 1.2
author: OpenClaw Team
dependencies: [node>=18.0.0, python>=3.9, git>=2.30, docker>=20.0]
environment_variables:
  - CODE_NINJA_MODE: "strict"  # Opciones: strict, lenient, experimental
  - CODE_NINJA_LANGUAGES: "js,py,ts,rb"  # Lenguajes soportados separados por coma
  - CODE_NINJA_TIMEOUT: "300"  # Segundos para optimizaciones de larga duración
requirements:
  - Acceso a repositorios de código fuente
  - Suites de pruebas para verificación
  - Herramientas de linting (eslint, ruff, etc.) configuradas
---

# Habilidad Code Ninja

## Propósito

La habilidad Code Ninja empodera a los desarrolladores para transformar codebases desordenados e ineficientes en soluciones elegantes y de alto rendimiento. Casos de uso reales incluyen:

- Refactorizar funciones monolíticas en una app React que causan congelamientos de UI, reduciendo el tiempo de renderizado en un 60% mediante memoización y carga lazy.
- Optimizar pipelines de procesamiento de datos en Python para aplicaciones de big data, logrando aceleraciones de 5x reemplazando bucles anidados con operaciones vectorizadas de NumPy.
- Crear APIs en TypeScript que manejen solicitudes concurrentes eficientemente, usando patrones async/await y pool de conexiones para eliminar cuellos de botella.
- Depurar y arreglar fugas de memoria en servidores Node.js, implementando pistas apropiadas de recolección de basura y procesamiento de streams para reducir el uso de heap en un 40%.
- Implementar flujos de autenticación seguros en apps Ruby on Rails, usando bcrypt para hashing y tokens JWT con expiración apropiada, previniendo vulnerabilidades comunes como ataques de timing.

Esta habilidad se invoca cuando problemas de calidad de código, rendimiento o seguridad demandan intervención a nivel ninja.

## Alcance

La habilidad Code Ninja soporta los siguientes comandos específicos, cada uno adaptado a desafíos comunes de codificación:

- `/code-ninja refactor <file_path> [--language <lang>] [--focus <area>]`: Refactoriza código para legibilidad y mantenibilidad.
  - `--language js|py|ts|rb`: Especifica lenguaje si la detección automática falla.
  - `--focus performance|security|readability`: Apunta a área específica de mejora.
- `/code-ninja optimize <function_name> [--benchmark] [--parallel]`: Optimiza algoritmos o funciones para velocidad.
  - `--benchmark`: Ejecuta pruebas de timing antes/después.
  - `--parallel`: Aplica procesamiento paralelo donde aplicable.
- `/code-ninja secure <file_path> [--scan <type>]`: Endurece código contra amenazas de seguridad.
  - `--scan injection|xss|auth`: Tipo de escaneo de vulnerabilidades.
- `/code-ninja test-gen <file_path> [--coverage 90]`: Genera pruebas unitarias comprehensivas.
  - `--coverage <percent>`: Porcentaje objetivo de cobertura de pruebas.
- `/code-ninja profile <script_path> [--output profile.json]`: Perfila código para cuellos de botella.
  - `--output <file>`: Guarda resultados de profiling en archivo.
- `/code-ninja migrate <old_lib> <new_lib> [--dry-run]`: Migra dependencias de manera segura.
  - `--dry-run`: Simula migración sin cambios.

Estos comandos se integran con herramientas existentes como ESLint, Ruff y Docker para testing containerizado.

## Proceso de Trabajo Detallado

El Code Ninja sigue un proceso metódico de 7 pasos para asegurar transformación magistral de código:

1. **Análisis de Código**: Escanea el archivo o función objetivo usando herramientas de análisis estático (ej. `eslint --fix` para JS, `ruff check` para Python). Identifica métricas como complejidad ciclomática, líneas de código y profundidad de dependencias. Por ejemplo, ejecuta `npx eslint src/components/BigComponent.tsx --format json` para recopilar datos detallados de linting.

2. **Identificación de Problemas**: Pincha problemas específicos como algoritmos O(n²), casos edge no manejados o prácticas inseguras. Usa herramientas de profiling como `python -m cProfile script.py` o `node --prof script.js` para cuantificar cuellos de botella.

3. **Diseño de Solución**: Propone soluciones elegantes, ej. reemplazar funciones recursivas con iterativas, implementar capas de caching, o adoptar patrones de diseño como Strategy para extensibilidad. Dibuja pseudocódigo y estima ganancias de rendimiento.

4. **Implementación Incremental**: Aplica cambios en commits pequeños y testeables. Por instancia, refactoriza una función sola primero, luego verifica con pruebas unitarias usando `npm test` o `pytest`.

5. **Aplicación de Optimización**: Introduce eficiencias como memoización (`React.useMemo`), vectorización (`np.vectorize`), o concurrencia (`asyncio.gather`). Asegura cambios backward-compatible.

6. **Endurecimiento de Seguridad**: Integra checks para SQL injection (usando queries parametrizadas), XSS (escapando outputs), y bypasses de auth (control de acceso basado en roles).

7. **Verificación Final**: Ejecuta suites de pruebas completas (`npm run test -- --coverage`), checks de lint, y benchmarks de rendimiento. Despliega a staging si disponible, monitoreando regresiones.

A lo largo, la habilidad mantiene historial git con commits descriptivos como `feat: optimize user lookup with indexed search`.

## Reglas de Oro

- **Eficiencia Primero**: Siempre prioriza mejoras algorítmicas sobre micro-optimizaciones; ej. prefiere sorting O(log n) sobre constantes más rápidas en datasets pequeños.
- **Elegancia Sobre Complejidad**: Usa la solución más simple que funciona; evita sobre-ingeniería—ej. no abstracciones innecesarias a menos que escalabilidad lo demande.
- **Seguridad por Diseño**: Incrusta checks de seguridad temprano; nunca introduces vulnerabilidades, incluso por ganancias de velocidad.
- **Refactorización Test-Driven**: Escribe o actualiza tests antes de cambiar código; apunta a cobertura 80%+ usando herramientas como Jest o pytest.
- **Maestría Agnóstica de Lenguaje**: Aplica mejores prácticas a través de JS, Python, TypeScript, Ruby—ej. usa patrones async en todos lenguajes capaces de async.
- **No Cambios Rompedores Sin Consentimiento**: Preserva APIs a menos que explícitamente autorizado; usa feature flags para refactors riesgosos.
- **Profiling Obligatorio**: Nunca optimiza ciegamente; siempre mide antes y después con herramientas como Chrome DevTools o Python's timeit.

## Ejemplos

### Ejemplo 1: Refactorizando Bucle Ineficiente

**Prompt del Usuario**: `/code-ninja refactor src/utils/dataProcessor.js --focus performance`

**Código de Entrada** (antes):
```javascript
function processData(data) {
  const results = [];
  for (let i = 0; i < data.length; i++) {
    for (let j = 0; j < data[i].items.length; j++) {
      if (data[i].items[j].value > 10) {
        results.push(data[i].items[j]);
      }
    }
  }
  return results;
}
```

**Código de Salida** (después):
```javascript
function processData(data) {
  return data.flatMap(item => item.items.filter(subItem => subItem.value > 10));
}
```
**Explicación**: Reemplazó bucles anidados con `flatMap` y `filter` para complejidad O(n), reduciendo tiempo de ejecución en ~70% en datasets grandes. Verificado con pruebas de benchmark.

### Ejemplo 2: Optimizando Función Python

**Prompt del Usuario**: `/code-ninja optimize fibonacci --benchmark`

**Código de Entrada** (antes):
```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

**Código de Salida** (después):
```python
import functools

@functools.lru_cache(maxsize=None)
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```
**Resultados de Benchmark**: Antes: 2.5s para n=35; Después: 0.001s para n=35. Usó memoización para eliminar cálculos redundantes.

### Ejemplo 3: Endurecimiento de Seguridad

**Prompt del Usuario**: `/code-ninja secure app/routes/auth.js --scan injection`

**Código de Entrada** (antes):
```javascript
app.post('/login', (req, res) => {
  const query = `SELECT * FROM users WHERE username='${req.body.username}' AND password='${req.body.password}'`;
  db.query(query, (err, result) => { /* ... */ });
});
```

**Código de Salida** (después):
```javascript
app.post('/login', (req, res) => {
  const query = 'SELECT * FROM users WHERE username=$1 AND password=$2';
  db.query(query, [req.body.username, req.body.password], (err, result) => { /* ... */ });
});
```
**Verificación**: Escaneado con SQLMap; no se detectaron vulnerabilidades de injection. Agregó queries parametrizadas.

## Comandos de Reversión

Si los cambios introducen problemas, usa estos comandos específicos de reversión:

- **Revertir Commit Específico con Git**: `git revert <commit-hash> --no-edit` para deshacer un commit de refactor único.
- **Resetear a Estado Anterior**: `git reset --hard HEAD~1` para descartar el último cambio si no está commited.
- **Reversión de Dependencia**: `npm uninstall <new-lib> && npm install <old-lib>@<version>` para reversiones de migración.
- **Reversión de Código vía Diff**: `git checkout -- <file_path>` para restaurar archivo original desde git.
- **Reversión de Docker**: `docker tag myapp:v1 myapp:rollback && docker run myapp:rollback` para probar imagen anterior.
- **Toggle de Feature Flag**: Establece variable de entorno `FEATURE_NEW_OPTIMIZATION=false` para deshabilitar cambios en runtime.

Siempre ejecuta `npm run test` y `npm run lint` después de reversión para confirmar estabilidad. Para producción, usa despliegues blue-green para minimizar downtime.