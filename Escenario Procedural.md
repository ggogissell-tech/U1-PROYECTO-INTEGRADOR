# Práctica: Construcción Procedural de un Escenario 3D
Objetivo: Implementar transformaciones tridimensionales (traslación y escalamiento) y modelos de color mediante scripting en Blender.
* Paso 1: Limpieza del Entorno y Preparación
Antes de construir cualquier geometría por código, debemos asegurar que la escena esté completamente vacía. Esto no solo evita que los objetos se encimen, sino que enseña la importancia de la gestión de objetos en memoria y el control del estado inicial del software.

* Paso 2: Definición de Materiales (Modelos de Color)
Según el tema 1.4 (Modelos del color) , utilizaremos el modelo RGB para dar vida al
escenario.

* Paso 3: Construcción de Paredes con Ciclos (Transformaciones)
Aquí aplicamos el Tema 3.3.1 (Traslación). Usaremos un ciclo for para automatizar la
creación de un pasillo.

* Paso 4: Completando la Geometría (Simetría y Suelo)
Para que parezca un videojuego, cerramos el pasillo y agregamos una superficie base.

* Paso 5: Iluminación Básica 
Un escenario de videojuego no está completo sin luz.
## CODIGO: 
<p align="center">
  <img src="https://github.com/user-attachments/assets/a934f87e-399f-47d4-944e-9666beeba951" width="329">
</p>

Este código de Python está diseñado para ejecutarse dentro de Blender (usando su API bpy). Y su función principal es generar automáticamente un pasillo 3D con paredes y suelo, utilizando lógica de programación para variar los colores y tamaños.

1. Configuración Inicial y Materiales
El script comienza importando las librerías de Blender y definiendo una función para crear "pinturas" (materiales) para los objetos.
* crear_material: Esta función toma un nombre y un color RGB. Crea un material nuevo en la base de datos de Blender y le asigna ese color.
* Dato técnico: Usa (color_rgb, 1.0) porque Blender requiere el canal Alpha (transparencia) para el color difuso.

2. Limpieza de la Escena (Líneas 11-13)
Antes de construir nada, el código ejecuta:
bpy.ops.object.select_all(action='SELECT') y bpy.ops.object.delete().
Esto borra todo lo que haya en tu escena actual (cubos, cámaras, luces) para que el script empiece desde cero cada vez que lo ejecutas.

3. Construcción del Pasillo (El Bucle for)
Aquí es donde ocurre la magia. El script define un pasillo de 10 unidades de largo y usa un ciclo para colocar paredes a ambos lados:
* Pared Izquierda: Crea cubos en una fila.
* Lógica de Alternancia: Usa if i % 2 == 0. Esto significa que si la pared es de una posición par, le pone el material oscuro. Si es impar, le pone un color naranja rojizo y, además, la hace más alta (scale.z = 1.5). Esto crea un efecto visual de columnas o detalles intermitentes.
* Pared Derecha: Crea cubos en el lado opuesto, pero estos son todos uniformes y de color oscuro.

4. El Suelo (Líneas 42-46)
Al final, el script añade un plano simple:
Lo posiciona en el centro del pasillo.
Lo escala (scale.x y scale.y) para que cubra exactamente el área entre las paredes que se acaban de crear.


