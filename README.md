# PRÁCTICA 1: El Arquitecto Visual - CSS y Modelo de Caja

---

## 1. PORTADA
* **Estudiante:** JOSUE VLADIMIR PALACIOS MARTINEZ
* **Módulo:** Módulo III - CSS, Diseño Responsivo y UX Básico
* **Proyecto:** "La Pokédex Digital" - Ficha Informativa de Pikachu (El Último Checkpoint)
* **Fecha:** 20 de Agosto 2026

---

## 2. AUDITORÍA MANUAL Y CORRECCIÓN (estilos.css)
Al revisar el código CSS inicial proporcionado por el practicante, identificamos los siguientes **3 errores sintácticos y conceptuales críticos** [1]:

1. **Error de sintaxis en el Borde (`border`):** El practicante intentó escribir la regla pero omitió el estilo de línea obligatorio (como `solid` o `dashed`), o bien escribió mal la propiedad (ej. `boder`) [1]. Al no respetar la sintaxis estricta `border: [grosor] [estilo] [color]`, el navegador ignora la regla por completo y la tarjeta queda sin borde [2, 3].
2. **Falta de unidades de medida en dimensiones:** En propiedades como anchos o rellenos se escribieron valores numéricos planos sin especificar la unidad (escribiendo `20` o `300` en lugar de `20px` o `300px`) [1]. Para el navegador, un número sin unidad en CSS es un error de sintaxis y descarta la declaración [3, 4].
3. **Falta de puntos y comas (`;`) al final de las declaraciones:** El navegador lee el CSS de forma secuencial [5]. Al omitir un punto y coma, el intérprete fusiona esa línea con la siguiente, provocando que ambas queden invalidadas y rompan la cascada de estilos [6, 7].

---

## 3. INVESTIGACIÓN TÉCNICA: Serif vs. Sans-serif en Pantallas
La propiedad `font-family` nos permite definir la tipografía y su familia genérica [8, 9]:

* **Fuentes Serif (Con Serifas):** Se caracterizan por tener pequeñas terminaciones, adornos o "patines" en los extremos de las letras (ejemplos clásicos: *Times New Roman*, *Georgia*) [10]. Históricamente se diseñaron para libros impresos, ya que la línea visual que forman las serifas ayuda a guiar la lectura horizontal en papel físico [10].
* **Fuentes Sans-serif (Sin Serifas):** Poseen cortes limpios, rectos y geométricos en sus bordes, careciendo de adornos adicionales (ejemplos: *Segoe UI*, *Arial*, *Verdana*) [10, 11].

### Recomendación para Interfaces y Pantallas Digitales
**Se recomienda categóricamente el uso de familias Sans-serif para pantallas digitales.** Las pantallas (móviles, tablets y monitores) representan las imágenes mediante una cuadrícula de píxeles. Las serifas muy delgadas o curvas de las fuentes Serif tienden a pixelarse o verse borrosas si la pantalla no es de altísima resolución, lo que cansa la vista del usuario. Las líneas limpias, uniformes y simplificadas de las tipografías Sans-serif garantizan una lectura nítida, fluida y altamente accesible [10, 12].

---

## 4. RETO DEL MODELO DE CAJA
La tarjeta original de Pikachu presentaba un problema grave de usabilidad y legibilidad porque el texto chocaba físicamente contra los bordes del contenedor [1].

### ¿Qué propiedad lo resuelve?
Para solucionar esto, la propiedad que se debe utilizar es **`padding`** (relleno interior) [4, 13]:
* El **`padding`** expande el espacio **adentro** de la caja (crea un colchón de aire protector entre el contenido del texto y el borde físico) [4, 13].
* Como el color de fondo (`background-color`) se visualiza en toda la extensión del contenido y su `padding` (pero no en el `margin`), el uso de `padding` "descolapsa" el texto y mantiene la estética del componente [14].
* El **`margin`** (margen exterior) es transparente e invisible, y su única función es separar la tarjeta de otros elementos externos [4, 13]. Aplicar `margin` solo habría alejado la tarjeta de los bordes de la pantalla, pero el texto interno habría seguido amontonado e ilegible [4, 13].

---

## 5. CONCLUSIÓN: Separación de Incumbencias (HTML vs. CSS)
El principio de **Separación de Incumbencias (Separation of Concerns)** establece que cada tecnología dentro del sistema web debe cumplir una única función aislada [15]:
* El **HTML** se encarga exclusivamente del **esqueleto estructural y semántico** (definir qué es cada elemento en la página) [16, 17].
* El **CSS** se encarga exclusivamente de la **presentación visual y estética** (definir cómo se ve cada elemento) [15].

Mezclar ambos conceptos (por ejemplo, usando estilos en línea con el atributo `style` o metiendo diseño directo en las etiquetas HTML) hace que el código sea sumamente pesado de descargar, complejo de entender y virtualmente imposible de mantener en el tiempo [18, 19]. Si tuviéramos un portal con 100 páginas y quisiéramos cambiar el color corporativo, tendríamos que editar manualmente 100 archivos HTML individuales [19].

Al separar la presentación en un archivo externo como **`css/estilos.css`**, podemos modificar la apariencia estética de cientos de páginas web de manera centralizada editando un único archivo de estilos [15, 20]. Esto optimiza el procesamiento del servidor, reduce el consumo de ancho de banda del cliente y eleva la eficiencia y escalabilidad del proyecto [15, 21].
