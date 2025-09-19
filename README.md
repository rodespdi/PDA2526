# PDA2526
Sesiones de Problemas del Bloque 1. 

Tres sesiones de problemas de una hora de duración 

Objetivo: Introducción a la postproducción digital y animación, con resolución práctica en MATLAB y Python. 

 

Sesión 1: La Imagen como Matriz de Datos 

Tema Principal: Concepto y Tipo de Imágenes. 

Objetivos de Aprendizaje: 

Comprender que una imagen digital es fundamentalmente una matriz de números. 

Saber cómo acceder y manipular las propiedades básicas de una imagen: dimensiones, canales y profundidad de bits. 

Diferenciar programáticamente entre imágenes en escala de grises y en color. 

Generar imágenes sintéticas simples desde cero. 

Actividades Propuestas (1 hora): 

Introducción Teórica (10 min): 

Repaso rápido: ¿Qué es un píxel? ¿Qué es un canal (R, G, B, Alpha)? 

Visualización de una imagen como un array 3D (Alto x Ancho x Canales). 

Breve mención a los tipos de datos (uint8, uint16, float) y su importancia en el rango dinámico (HDR). 

Problema 1: "Inspección de la Imagen" (20 min): 

Enunciado: Carga una imagen proporcionada (ej. un fotograma de una animación en formato .png o .tif). 

Tareas: 

En Python/MATLAB, escribe un script que cargue la imagen. 

Imprime por consola sus dimensiones (alto y ancho en píxeles). 

Detecta e informa cuántos canales tiene. Si tiene 3 canales, es RGB. Si tiene 4, es RGBA. Si tiene 1, es escala de grises. 

Extrae y muestra por separado cada uno de los canales de color (mostrar el canal Rojo como una imagen en escala de grises, por ejemplo). 

Discusión: ¿Qué información visual representa cada canal? ¿Cómo se vería el canal Alpha? 

 

 

Problema 2: "Creando desde la Nada" (20 min): 

Enunciado: No cargues ninguna imagen. Crea una nueva imagen desde cero. 

Tareas: 

Crea una matriz de 512x512 píxeles de color negro. 

Dibuja un cuadrado blanco de 100x100 píxeles en el centro de la imagen. Para ello, deberás calcular las coordenadas y asignar el valor de color correspondiente (ej. [255, 255, 255] en RGB) a ese bloque de píxeles en la matriz. 

(Bonus): En lugar de un cuadrado, genera un gradiente de color suave de izquierda a derecha (ej. de negro a rojo puro). 

Discusión: ¿Cómo se relaciona esto con la generación de texturas procedurales o máscaras en postproducción? 

Recursos y Código de Apoyo: 

Python: Librerías opencv-python (cv2.imread, cv2.imshow) y numpy. 

MATLAB: Funciones imread, imshow, size. 

 

Sesión 2: Jugando con el Color  

Tema Principal: Espacios de Color. 

Objetivos de Aprendizaje: 

Entender las limitaciones del espacio de color RGB para la manipulación intuitiva. 

Trabajar con el espacio de color HSV (Tono, Saturación, Valor) para ajustes más perceptuales. 

Implementar una corrección de color básica o un efecto de keying simple. 

Actividades Propuestas (1 hora): 

Introducción Teórica (10 min): 

¿Por qué necesitamos otros espacios de color además de RGB? (Ej: "Quiero hacer los rojos más intensos" es difícil en RGB pero fácil en HSV). 

Explicación del modelo HSV: El Tono como el color puro, la Saturación como su intensidad y el Valor como su brillo. 

Aplicación directa en software de postproducción (ej. la rueda de color en DaVinci Resolve o After Effects). 

Problema 1: "Corrección de Color Selectiva" (25 min): 

Enunciado: Carga una imagen de un paisaje o un personaje. El objetivo es aumentar la intensidad solo de los colores verdes. 

Tareas: 

Carga la imagen en Python/MATLAB. 

Conviértela del espacio de color BGR/RGB al espacio HSV. 

Aísla el canal de Saturación (S). 

Crea una máscara para seleccionar solo los píxeles cuyo Tono (H) caiga en el rango del verde. 

Aplica una multiplicación al canal de Saturación (S = S * 1.5) únicamente en los píxeles definidos por la máscara. 

Vuelve a convertir la imagen de HSV a RGB y muéstrala junto a la original para comparar. 

Discusión: ¿Por qué este método es más eficaz que intentar manipular los canales RGB por separado? 

Problema 2: "Chroma Key Simplificado" (15 min): 

Enunciado: Se proporciona una imagen de un objeto sobre un fondo de color uniforme (ej. un croma verde o azul). 

Tareas: 

Convierte la imagen a HSV. 

Define un rango de Tono, Saturación y Valor que corresponda al color del fondo. 

Crea una máscara binaria (blanco y negro) donde el blanco represente el fondo y el negro el objeto. 

(Bonus): Usa esta máscara para recortar el objeto y ponerlo sobre otra imagen de fondo. 

Discusión: ¿Qué desafíos existen en un croma real (sombras, bordes, rebotes de color)? 

Recursos y Código de Apoyo: 

Python: cv2.cvtColor (con flags cv2.COLOR_BGR2HSV y cv2.COLOR_HSV2BGR), cv2.inRange. 

MATLAB: rgb2hsv, hsv2rgb. 

Forma 

Sesión 3: El Dilema de la Compresión  

Tema Principal: Formatos de Compresión en Imagen Digital. 

Objetivos de Aprendizaje: 

Diferenciar entre compresión sin pérdidas (Lossless) y con pérdidas (Lossy). 

Visualizar y cuantificar los "artefactos" generados por la compresión con pérdidas. 

Comprender por qué en un flujo de trabajo profesional se usan ciertos formatos (ej. EXR, TIFF) y por qué otros se usan para la entrega final (ej. JPEG, H.264). 

Actividades Propuestas (1 hora): 

Introducción Teórica (10 min): 

Compresión Lossless (PNG, TIFF LZW): "Guardar toda la información, pero de forma más inteligente". 

Compresión Lossy (JPEG): "Descartar información que el ojo humano no nota (o no tanto)". Explicar brevemente el concepto de la transformada de coseno discreta (DCT) y la cuantificación. 

El caso de los formatos profesionales: EXR, DPX. ¿Por qué son importantes? (Alto rango dinámico, múltiples canales/capas). 

Problema 1: "El Coste de la Calidad" (25 min): 

Enunciado: Analizar el impacto de la compresión JPEG en una imagen de alta calidad. 

Tareas: 

Carga una imagen de alta calidad sin comprimir o con compresión lossless (ej. un .tif o .png). 

Guarda tres versiones de esa imagen en formato JPEG con diferentes niveles de calidad: 

Calidad 95 (alta) 

Calidad 50 (media) 

Calidad 10 (baja) 

Vuelve a cargar las tres imágenes JPEG y la original. 

Muéstralas una al lado de la otra para una comparación visual. Presta atención a los bordes y a las áreas de color suave. 

Discusión: ¿Dónde son más visibles los artefactos de compresión? ¿Qué tamaño de archivo tiene cada imagen? 

Problema 2: "Midiendo la Diferencia" (15 min): 

Enunciado: Cuantificar la pérdida de información del ejercicio anterior. 

Tareas: 

Calcula la diferencia absoluta píxel a píxel entre la imagen original y la versión JPEG de calidad 10. 

Muestra esta "imagen de diferencia". Las áreas negras significan que no hay error, mientras que las áreas más brillantes indican una mayor pérdida de información. 

(Bonus): Calcula una métrica de error como el Error Cuadrático Medio (MSE) entre la original y cada una de las versiones comprimidas. 

Discusión Final: ¿En qué fase de un proyecto de animación (modelado, render, compo, entrega) usarías un formato lossy? ¿Y uno lossless? ¿Por qué nunca harías la postproducción sobre un archivo JPEG? 

Recursos y Código de Apoyo: 

Python: cv2.imwrite (permite pasar parámetros de compresión como [cv2.IMWRITE_JPEG_QUALITY, 90]). 

MATLAB: imwrite (con el par nombre-valor 'Quality'). 

 
