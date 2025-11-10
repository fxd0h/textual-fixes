# Análisis de Bugs Simples - Textual Project

Este documento contiene el análisis de bugs simples y fáciles de implementar.

---

## ✅ Bugs Completados

### ✅ **BUG #4852 - TextArea scrollbar position not updated after paste** 
**Estado: COMPLETADO Y COMMITEADO**

**Branch**: `fix/4852-textarea-scrollbar-paste`
**Commit**: `01129c25f`

**Solución implementada**:
- Agregado `scroll_cursor_visible()` después de `move_cursor()` en `_on_paste()` y `action_paste()`
- Tests de regresión creados
- CHANGELOG actualizado

---

### ✅ **BUG #3449 - DataTable auto-width columns don't shrink back down** 
**Estado: COMPLETADO Y COMMITEADO**

**Branch**: `fix/3449-datatable-auto-width-shrink`
**Commit**: `551a71048`

**Solución implementada**:
- Agregado flag `_rows_removed` para rastrear cuando se eliminan filas
- Creado método `_recalculate_all_column_widths()` para recalcular anchos
- Modificado `remove_row()` para establecer el flag
- Modificado `_on_idle()` para recalcular cuando se eliminan filas
- Test de regresión creado
- CHANGELOG actualizado

---

## 🐛 Bugs Pendientes (Más Complejos)

### ⚠️ **BUG #4639 - priority binding order is not respected in the Footer**
**Prioridad: MEDIA (Complejidad media)**

**Descripción**: El orden de los bindings con prioridad no se respeta en el Footer widget.

**Estado**: Hay un fix sugerido por TomJGooding pero podría afectar otro issue (#4382)
**Complejidad**: ⭐⭐⭐ (Media)
**Tiempo estimado**: 2-3 horas

---

### ⚠️ **BUG #5103 - TextArea scrollbar and wrapping interaction on initial render**
**Prioridad: MEDIA (Problema de timing)**

**Descripción**: El wrap inicial no tiene en cuenta el scrollbar, causando que el contenido se envuelva más ancho de lo que debería.

**Estado**: Problema chicken-and-egg (no se puede saber el ancho hasta hacer wrap, pero no se puede hacer wrap sin saber el ancho)
**Complejidad**: ⭐⭐⭐ (Media-Alta)
**Tiempo estimado**: 2-4 horas

---

### ❓ **BUG #4900 - KeyError error occurred in DataTable**
**Prioridad: DESCONOCIDA (Necesita más información)**

**Descripción**: KeyError cuando se limpia y renderiza contenido repetidamente en DataTable.

**Estado**: No hay ejemplo mínimo para reproducir
**Complejidad**: ⭐⭐⭐ (Media-Alta)
**Tiempo estimado**: Desconocido hasta reproducir

---

### ⚠️ **BUG #5155 - Transparent component class background blends with wrong colour**
**Prioridad: MEDIA (Complejidad arquitectónica)**

**Descripción**: El blend se hace contra el parent incorrecto cuando se usan component classes.

**Complejidad**: ⭐⭐⭐⭐ (Alta)
**Tiempo estimado**: 4-6 horas

---

### ⚠️ **BUG #4968 - `@on` decorator matches widget subclass unexpectedly**
**Prioridad: MEDIA (Complejidad arquitectónica)**

**Descripción**: `@on(MyButton.Pressed)` hace match con `Button` normal.

**Estado**: Requiere cambios en cómo se almacena la información del decorator
**Complejidad**: ⭐⭐⭐⭐ (Alta)
**Tiempo estimado**: 4-8 horas

---

## 📊 Resumen

**Bugs completados**: 2 (#4852, #3449)
**Bugs pendientes simples**: 0
**Bugs pendientes complejos**: 5+

**Recomendación**: Los bugs restantes requieren más investigación o cambios arquitectónicos. Es mejor preparar los PRs para los bugs completados.

---

*Última actualización: Después de investigación exhaustiva*
