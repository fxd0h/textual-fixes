# Análisis de Bugs - Textual Project

Este documento contiene el análisis de bugs del proyecto Textual para identificar cuáles son más fáciles de resolver.

---

## 🐛 Bugs Identificados y Análisis

### ✅ **BUG #4852 - TextArea scrollbar position not updated after paste** 
**Prioridad: ALTA (Fácil de resolver)**

**Descripción**: Cuando se pega texto en un `TextArea`, la posición del scrollbar vertical no se actualiza correctamente y debería estar al final del texto pegado.

**Ubicación del código**:
- `src/textual/widgets/_text_area.py`
  - Método `_on_paste()` (línea ~1847)
  - Método `action_paste()` (línea ~2526)

**Análisis**:
- Ambos métodos insertan texto pero no llaman a `scroll_cursor_visible()` después de pegar
- El método `move_cursor()` se llama pero sin el parámetro `center=False` que podría ayudar
- Existe un método `scroll_cursor_visible()` que puede ser llamado después de pegar

**Solución propuesta**:
1. Llamar a `self.scroll_cursor_visible()` después de `move_cursor()` en ambos métodos
2. O mejor aún, llamar a `scroll_cursor_visible()` dentro de `move_cursor()` cuando sea necesario

**Complejidad**: ⭐⭐ (Baja)
**Tiempo estimado**: 30-60 minutos

---

### ⚠️ **BUG #4968 - `@on` decorator matches widget subclass unexpectedly**
**Prioridad: MEDIA (Complejidad media)**

**Descripción**: El decorator `@on` está haciendo match con subclases de widgets cuando no debería. Si tienes `@on(MyButton.Pressed)` y un `Button` normal, también hace match.

**Ubicación del código**:
- `src/textual/_on.py` - Función `on()`
- Probablemente en el sistema de mensajes donde se hace el matching

**Análisis**:
- El decorator `@on` usa selectores CSS para hacer matching
- El problema parece estar en cómo se compara el tipo del widget en el mensaje
- Necesita verificar que el tipo sea exactamente el especificado, no una subclase

**Complejidad**: ⭐⭐⭐ (Media)
**Tiempo estimado**: 2-4 horas

---

### ⚠️ **BUG #5103 - TextArea scrollbar and wrapping interaction on initial render**
**Prioridad: MEDIA (Complejidad media)**

**Descripción**: Cuando un `TextArea` tiene wrapping habilitado y contenido que requiere scrollbar, el wrap inicial no tiene en cuenta el scrollbar, causando que el contenido se envuelva más ancho de lo que debería.

**Ubicación del código**:
- `src/textual/widgets/_text_area.py`
- Probablemente en el método de render inicial o en el cálculo del ancho disponible

**Análisis**:
- El problema está en el cálculo del ancho disponible para el wrapping
- El scrollbar debería restarse del ancho disponible antes de hacer el wrap inicial
- Necesita revisar `_watch_show_vertical_scrollbar()` y el cálculo de ancho

**Complejidad**: ⭐⭐⭐ (Media)
**Tiempo estimado**: 2-3 horas

---

### ⚠️ **BUG #3510 - [typing] Inconsistent typing in the work decorator**
**Prioridad: BAJA (Complejidad alta)**

**Descripción**: Inconsistencias en los tipos del decorator `@work`. Hay un uso inconsistente de `Decorator` versus `Decorator[..., ReturnType]`.

**Ubicación del código**:
- `src/textual/_work_decorator.py`

**Análisis**:
- El problema está en la definición de tipos del decorator
- Hay múltiples overloads pero puede haber inconsistencias
- Puede requerir cambios complejos en los tipos genéricos
- Mencionan que ya se intentó antes (PR #3862) y hubo problemas con mypy

**Complejidad**: ⭐⭐⭐⭐ (Alta)
**Tiempo estimado**: 4-8 horas (puede ser más si hay problemas con mypy)

---

### ❓ **BUG #4900 - KeyError error occurred in DataTable**
**Prioridad: DESCONOCIDA (Necesita más información)**

**Descripción**: KeyError cuando se limpia y renderiza contenido repetidamente en DataTable.

**Análisis**:
- Necesita más información para reproducir
- Puede ser un problema de sincronización o de limpieza de datos
- Requiere crear un caso de prueba para reproducir el error

**Complejidad**: ⭐⭐⭐ (Media-Alta)
**Tiempo estimado**: Desconocido hasta reproducir

---

## 🎯 Recomendación: Empezar con BUG #4852

**Razones**:
1. ✅ **Más simple**: Solo requiere agregar una llamada a método existente
2. ✅ **Bien definido**: El problema está claro y la solución es obvia
3. ✅ **Bajo riesgo**: No afecta otras funcionalidades
4. ✅ **Fácil de testear**: Se puede crear un test simple

**Plan de acción**:
1. Revisar el código de `_on_paste()` y `action_paste()`
2. Agregar llamada a `scroll_cursor_visible()` después de pegar
3. Crear test de regresión
4. Verificar que funciona correctamente
5. Actualizar CHANGELOG.md

---

## 📋 Otros Bugs para Considerar Después

- **#5155** - Transparent component class background blends with wrong colour
- **#4955** - Unable to switch tabs in TabbedContent using a key binding
- **#4639** - priority binding order is not respected in the Footer
- **#3449** - DataTable auto-width columns don't shrink back down

---

*Última actualización: Análisis inicial*
