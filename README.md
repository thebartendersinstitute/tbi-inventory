# TBI Inventory — Inventario de Botellas por Peso

**Desarrollado por [The Bartenders Institute](https://thebartendersinstitute.com)**  
Guadalajara, México · Desde 2007

---

## ¿Qué es esto?

TBI Inventory es una aplicación gratuita y de código abierto para hacer inventario de botellas por peso en bares, restaurantes y hoteles.

En lugar de estimar visualmente si una botella está "a la mitad" o "a tres cuartos", el sistema usa la báscula: pesas la botella, y la app calcula exactamente cuántos mililitros quedan y cuánto se ha consumido. El resultado es un inventario objetivo, trazable y reproducible.

El método está basado en el **Método TBI de Inventario por Peso**, desarrollado e implementado por The Bartenders Institute a lo largo de 18 años de formación profesional de bartenders en México.

---

## ¿Por qué inventario por peso?

El inventario visual tiene un margen de error constante. Dos personas distintas mirando la misma botella pueden estimar contenidos diferentes. Bajo luz tenue, al cierre del turno, con botellas de formas irregulares, el error se multiplica.

El pesaje elimina la subjetividad. La báscula siempre da el mismo número. Y con la densidad práctica de cada líquido registrada, ese número se convierte directamente en mililitros.

---

## Características

- **Sin servidor.** Todo funciona en el dispositivo. No requiere internet después de la primera carga.
- **Instala como app.** Funciona como aplicación nativa en celular y tablet sin pasar por ninguna tienda.
- **Gratuita y de código abierto.** Licencia MIT. Sin pagos, sin suscripciones, sin anuncios.
- **Catálogo precargado.** Incluye 14 productos de referencia con sus densidades TBI listas para usar.
- **Densidades propias.** Registra la densidad práctica de cualquier producto con probeta de 100 mL o matraz de 10 mL.
- **Trazabilidad completa.** Cada botella tiene código único, historial de lecturas y registro de quién hizo cada pesaje.
- **Backup y restauración.** Exporta todos tus datos en JSON e impórtalos en otro dispositivo cuando lo necesites.
- **Reportes exportables.** Inventario actual y consumo por período, descargables en CSV.

---

## Cómo instalar en celular

No necesitas descargar nada de una tienda. El proceso es:

**En Android (Chrome):**
1. Abre Chrome y entra a la URL de la app
2. Toca el menú (tres puntos arriba a la derecha)
3. Selecciona "Agregar a pantalla de inicio"
4. Confirma. La app aparece en tu pantalla de inicio como cualquier otra aplicación

**En iPhone / iPad (Safari):**
1. Abre Safari y entra a la URL de la app
2. Toca el botón de compartir (el cuadro con la flecha hacia arriba)
3. Selecciona "Agregar a pantalla de inicio"
4. Confirma. La app aparece en tu pantalla de inicio

> Una vez instalada, la app funciona sin conexión a internet.

---

## Primeros pasos

El orden correcto para empezar es el siguiente:

### 1. Revisa el catálogo de productos

Entra a **Catálogo** y verifica los productos que ya están precargados. Si el producto que necesitas ya está, puedes usarlo directamente. Cada producto precargado tiene la densidad de referencia TBI registrada.

Si necesitas agregar un producto que no está en la lista, toca **+ Producto** y llena nombre, marca y categoría.

### 2. Mide la densidad de tus productos

Para cada producto que vayas a inventariar necesitas tener registrada su densidad práctica. Esto se hace una sola vez por producto (o cuando cambias de proveedor o lote).

Entra a **Catálogo**, toca el ícono de edición junto al producto y sigue el flujo de medición:

- Llena exactamente **100 mL** del líquido en una probeta o matraz aforado de 100 mL
- Coloca el recipiente en la báscula **previamente tareada** (en cero)
- Registra el peso que marca la báscula
- La app calcula la densidad automáticamente

> Si solo tienes matraz de 10 mL, úsalo, pero asegúrate de que tu báscula tenga resolución de 0.01 g o menor. Con básculas de 0.1 g el margen de error es significativo en volúmenes pequeños.

### 3. Registra tus botellas

Entra a **Botellas** y toca **+ Nueva** para registrar cada botella que entra a tu barra.

Para cada botella necesitas:
- Seleccionar el producto del catálogo
- Asignar un código único (la app sugiere el siguiente automáticamente: A0001, A0002...)
- Indicar la capacidad en mL (700, 750, 1000, etc.)
- Pesar la botella **completamente llena** y registrar ese peso en gramos

Este peso inicial es el punto de partida. No lo cambies después.

### 4. Haz tu primer inventario

Entra a **Pesar**, escribe o escanea el código de la botella, coloca la botella en la báscula y registra el peso actual. La app calcula en tiempo real cuánto se ha consumido y cuánto queda.

---

## Flujo de inventario periódico

El inventario por peso funciona mejor cuando se hace de forma regular. El procedimiento en cada corte es:

1. Toma la primera botella, busca su código en la app
2. Colócala en la báscula y registra el peso que muestra
3. Revisa el resultado: mililitros consumidos, mililitros restantes, porcentaje
4. Guarda la lectura y pasa a la siguiente botella
5. Repite hasta completar todas las botellas de la ubicación

Al terminar, en **Reportes** tienes el inventario actual de todas las botellas con su nivel de llenado, y en la pestaña de Consumo puedes ver cuánto se ha consumido de cada una entre lecturas.

---

## Resguardo de datos

Los datos se guardan localmente en el navegador del dispositivo. Esto significa que:

- Si borras los datos del navegador o desinstala la app, los datos se pierden
- Si cambias de celular, necesitas exportar el backup antes de cambiar
- Dos dispositivos distintos no se sincronizan automáticamente

**Se recomienda hacer un backup en JSON cada semana desde Reportes → Exportar backup.** Guarda ese archivo en Google Drive, WhatsApp contigo mismo, o donde tengas acceso desde cualquier lugar.

Para restaurar en un dispositivo nuevo: instala la app, entra a Reportes, toca **Importar backup** y selecciona el archivo JSON.

---

## Fórmula del cálculo

La conversión de peso a volumen usa la densidad práctica de cada líquido:

```
Volumen consumido (mL) = (Peso inicial (g) − Peso actual (g)) / Densidad (g/mL)
Volumen restante (mL)  = Capacidad (mL) − Volumen consumido (mL)
Porcentaje restante    = Volumen restante / Capacidad × 100
```

La densidad se mide en el establecimiento con el producto real, no se usa un valor teórico genérico. Esto es lo que hace al método confiable: el factor de conversión corresponde exactamente al líquido que estás controlando.

---

## Stack técnico

La app es un único archivo HTML autocontenido. No requiere instalación ni compilación.

- **React 18** via CDN — interfaz de usuario
- **Dexie.js 3** — base de datos IndexedDB en el navegador
- **Fuentes:** Space Mono + DM Sans via Google Fonts

Para hacer cambios al código, abre `index.html` en cualquier editor de texto.

---

## Cómo contribuir

Este proyecto es de código abierto. Si encuentras un error, tienes una mejora o quieres agregar productos al catálogo de referencia, puedes:

1. Hacer un fork del repositorio
2. Aplicar tus cambios
3. Abrir un Pull Request con la descripción de lo que cambiaste

También puedes abrir un Issue si encuentras algo que no funciona correctamente.

---

## Créditos

Desarrollado y mantenido por **The Bartenders Institute**  
Escuela de bartenders profesionales — Guadalajara, México  
18 años formando bartenders en el sector de hospitalidad

El Método TBI de Inventario por Peso, la estructura didáctica, el procedimiento de medición de densidad práctica y los materiales explicativos son propiedad intelectual de The Bartenders Institute.

---

## Licencia

El código de esta aplicación se distribuye bajo licencia **MIT**.  
Puedes usarlo, modificarlo y distribuirlo libremente citando la fuente.

```
MIT License © 2026 The Bartenders Institute
```

---

*TBI Inventory · v1.0 · Mayo 2026*
