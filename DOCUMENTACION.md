# Documentación de la interfaz - Pequetienda

## 1. Justificación del diseño
### 1.1 Importancia del diseño centrado en el usuario
El diseño centrado en el usuario es importante ya que cuando el programa esta pensado en las necesidades especificas del usuario, este aumenta su satisfacción ya que pueden utilizar una aplicación en la que encuentran los que buscan facilmente, lo que hará que el usuario tienda a volver a utilizar la aplicación en una futura ocasión, mejorando la retención. Otra cuestión por la que el diseño centrado en el usuario es importante es que  este nos ayuda a identificar y corregir problemas antes de que afecten a un gran número de usuarios, lo que puede ayudar a evitar el riesgo de fracaso del producto.
### 1.2 Objetivos y metas del proyecto
* Posibilidad de realizar una compra en menos de un minuto y medio
* Acceder al catálogo en menos de 25 segundos
* Iniciar sesión en menos de 10 segundos
### 1.3 Beneficios esperados
__Para el usuario:__ Una aplicación facil de usar y eficaz en la que hacer sus compras de manera sencilla.  
__Para el negocio:__ Mejorar la retención de usuarios, ya que estos se sentirán satisfechos con un diseño de interfaz sencillo de usar.

## 2. Investigación y análisis de usuarios
### 2.1 Datos demográficos y segmentación
El público principal al que va dirigido esta aplicación es a madres, padres, abuelos y personas que compran regalos a sus niños, pero que carecen de tiempo suficiente, compran desde el movil y tienen bastantes dudas con las tallas.
### 2.2 Personas (Nombre, edad, contexto, objetivo, frustración)                            (#### Persona 1: … y #### Persona 2: …)
#### Persona 1:
* __Contexto:__ Noelia de 38 años de edad, a punto de traer al mundo a su primer hijo
* __Objetivo:__ Comprar las primeras prendas de su futuro hijo
* __Frustración:__ Está muy confusa con respecto a la ropa que debe comprar.
#### Persona 2:
* __Contexto:__ Paco de 77 años de edad, tiene 2 nietos cuyos cumples están a la vuelta de la esquina
* __Objetivo:__ Comprar ropa como regalo para sus nietos
* __Frustración:__ No está muy familiarizado con las tecnologías y la compra online por lo que le resulta muy complicado y confuso y no quiere equivocarse con las tallas.
### 2.3 Análisis de la competencia           (tabla con mín. 3 apps)
| Aplicación | Qué hacen bien | Qué hacen mal | Qué me llevo |
| :--- | :--- | :--- | :--- |
| **PatPat** | - **Permitir reseñas:** Los usuarios tienen la posibilidad de revisar reseñas reales con fotos de otros padres y valoraciones por rangos de edad muy visibles.<br>- **Variedad y filtros:** Gran variedad de productos filtrados por temáticas. | - **Sobrecarga visual** La interfaz suele abusar de pop-ups, banners agresivos de cuenta atrás y estímulos que generan gran fatiga visual al usuario.<br>- **Tiempos de envío erróneos:** Los tiempos prometidos en la aplicación a menudo no coinciden con la realidad del envío.<br>- **Inconsistencia en las tallas:** Al agrupar fabricantes de terceros, las medidas varían drásticamente provocando confusión y errores. | **Importancia de las reseñas:** Los padres confían más en las fotos y opiniones de otros padres que en las del propio catálogo, por lo que es un elemento vital para nuestra aplicación. |
| **Gocco** | - **Especialización por etapas de crecimiento:** Se divide de forma muy intuiitiva el catálogo por etapas (Primera puesta, Bebé, Niño/Niña)<br>- **Estética de marca limpia:** Dirección de arte elegante y fotografía de estudio muy cuidada que refuerza su posicionamiento de gama media-alta. | - **Fallos técnicos de stock:** Problemas ocasionales de stock fantasma que indican disponibilidad que luego falla al seleccionar talla. <br>- **Inestabilidad:** La app móvil puede volverse lenta, quedarse colgada o incluso experimentar cierres en medio de una navegación. | **Coherencia entre estética y rendimiento:** En nuestra aplicación se debe cuidar que la estabilidad y rendimiento esté a la altura de la estética, ya que un pequeño bug de scroll o stock puede destruir la confianza del padre inmediatamente |
| **Boboli** | - **Estructura clara:** Las categorías estan estructuradas por edad, género, tipo de prenda y colecciones coordinadas.<br>- **Fichas de producto descriptivas:** Muestran con todo detalle la composición de los tejidos, lo cual es muy importante en ropa de niños por alergias, piel atópica o necesidades de lavado. | - **Experiencia de usuario móvil obsoleta:** Su interfaz a menudo se siente más como una páginaweb adaptada que como una app nativa fluida, lo que perjudica a la experiencia de usuario. | **La importancia de incluir detalles técnicos técnico:** Los padres compran con el tacto en mente para evitar molestias o alergias en sus hijos. Detallar texturas, tipos de algodón y facilidad de lavado reduce drásticamente la tasa de carritos abandonados. |
### 2.4 Insights y hallazgos clave           (mín. 4, cada uno con su decisión de diseño)
* __Dudas con las tallas:__ Incorporación de una guía de tallas basada en estatura y peso en lugar de solo la edad que sea visible en los detalles del producto.
* __Necesidad de acotar rápidamente catálogos masivos:__ Implementar una barra de filtrado en la pantalla de Catálogo que permitan filtrar por talla, color y precio, manteniendo la interfaz limpia y organizada.
* __Errores al rellenar el pago:__ En la pantalla de Checkout, usar campos de texto que marquen en rojo el error y muestren un mensaje de ayuda claro si el dato es incorrecto.
* __Borrar sin querer un producto del carrito:__ Mostrar un aviso flotante con un botón de Deshacer cada vez que se borre un artículo para poder recuperarlo al instante.

## 3. Diseño de la interfaz
### 3.1 Mapa de navegación
```mermaid
graph TD
    Login["Login"]
    Inicio["Inicio"]
    Catalogo["Catálogo"]
    Detalles["Detalles"]
    Carrito["Carrito"]
    Checkout["Checkout"]
    Confirmacion["Confirmación"]
    Favoritos["Favoritos"]

    Login -->|Inicia sesión| Inicio
    Inicio -->|Seleccionar categoría| Catalogo
    Inicio -->|Acceder| Carrito
    Inicio -->|Acceder| Favoritos
    Catalogo -->|Seleccionar| Detalles
    Catalogo -->|Volver atrás| Inicio
    Favoritos -->|Seleccionar| Detalles
    Favoritos -->|Volver atrás| Inicio
    Detalles -->|Añadir| Carrito
    Carrito -->|Comprar todo| Checkout
    Carrito -->|Seleccionar producto| Detalles
    Carrito -->|Volver atrás| Inicio
    Checkout -->|Confirmar y pagar| Confirmacion
    Checkout -->|Volver atrás| Carrito
    Confirmacion -->|Reiniciar| Inicio
```



### 3.2 Wireframes
#### Login
![Wireframe de login](capturas/wireframes/Login.png)
#### Inicio
![Wireframe de inicio](capturas/wireframes/Inicio.png)
#### Catálogo
![Wireframe de catálogo](capturas/wireframes/Catálogo.png)
#### Detalle de producto
![Wireframe de detalle de producto](capturas/wireframes/Detalles.png)
#### Carrito
![Wireframe de carrito](capturas/wireframes/Carrito.png)
#### Checkout
![Wireframe de checkout](capturas/wireframes/Checkout.png)
#### Confirmación
![Wireframe de confirmación](capturas/wireframes/Confirmación.png)
#### Favoritos
![Wireframe de favoritos](capturas/wireframes/Favoritos.png)
### 3.3 Guía de estilo Material Design 3
#### Estilo Claro
| Pareja de Tokens M3 | Color/OnColor | Ratio de Contraste | Cumplimiento WCAG AA |
| :--- | :--- | :--- | :--- |
| **Primary / On Primary** | #32618D / #FFFFFF | **5.4 : 1** | Sí |
| **Secondary / On Secondary** | #526070 / #FFFFFF | **6.1 : 1** | Sí |
| **Tertiary / On Tertiary** | #695779 / #FFFFFF | **6.3 : 1** | Sí |
| **Surface / On Surface** | #F8F9FF / #191C20 | **14.2 : 1** | Sí |
| **Error / On Error** | #BA1A1A / #FFFFFF | **5.9 : 1** | Sí |  

#### Estilo Oscuro
| Pareja de Tokens M3 | Color/OnColor | Ratio de Contraste | Cumplimiento WCAG AA |
| :--- | :--- | :--- | :--- |
| **Primary / On Primary** | #9ECAFC / #003355 | **7.8 : 1** | Sí |
| **Secondary / On Secondary** | #BAC8DA / #243240 | **8.0 : 1** | Sí |
| **Tertiary / On Tertiary** | #D5BEE5 / #3A2A48 | **7.9 : 1** | Sí |
| **Surface / On Surface** | #101418 / #E0E2E8 | **13.5 : 1** | Sí |
| **Error / On Error** | #FFB4AB / #690005 | **8.2 : 1** | Sí |

#### Tabla de Tipografía

La familia tipográfica seleccionada es Roboto. En la tabla se detallan los roles tipográficos utilizados en la interfaz, indicando el tamaño, interlineado y peso para garantizar la jerarquía visual y la legibilidad.

| Rol | Tamaño (sp) | Interlineado (sp) | Peso | Ejemplo de Uso |
| :--- | :---: | :---: | :---: | :--- |
| **headlineSmall** | 24 | 32 | Regular (400) | Títulos principales de pantallas o secciones destacadas |
| **titleLarge** | 22 | 28 | Regular (400) | Encabezados de tarjetas o modales importantes |
| **titleMedium** | 16 | 24 | Medium (500) | Subtítulos de componentes |
| **bodyLarge** | 16 | 24 | Regular (400) | Texto general de párrafos y descripciones |
| **labelLarge** | 14 | 20 | Medium (500) | Etiquetas en botones, pestañas y campos de formulario |

---

#### Rejilla y Áreas Táctiles

El sistema de layout y espaciado está construido sobre una base de 8 píxeles, asegurando una alineación coherente y una estructura visual ordenada en dispositivos móviles.

##### Rejilla y Márgenes
* **Base de espaciado:** 8px
* **Columnas:** 4 columnas para la disposición de elementos en pantalla.
* **Margen de pantalla:** 16px en los laterales para evitar que el contenido colisione con los bordes del dispositivo.

##### Áreas Táctiles
Para garantizar la accesibilidad y una experiencia de usuario fluida, evitando errores de interacción en pantallas táctiles:

* **Área táctil mínima:** 48x48px obligatorios para todos los elementos interactivos (botones, iconos enlazados, chips de filtrado, etc.), incluso cuando el elemento visual sea ligeramente más pequeño.

### 3.4 Prototipo de alta fidelidad
#### Login
![Prototipo de login](capturas/prototipo/Login.png)
#### Inicio
![Prototipo de inicio](capturas/prototipo/Inicio.png)
#### Catálogo
![Prototipo de catálogo](capturas/prototipo/Catálogo.png)
#### Detalle de producto
![Prototipo de detalle de producto](capturas/prototipo/Detalles.png)
#### Carrito
![Prototipo de carrito](capturas/prototipo/Carrito.png)
#### Checkout
![Prototipo de checkout](capturas/prototipo/Checkout.png)
#### Confirmación
![Prototipo de confirmación](capturas/prototipo/Confirmación.png)
#### Favoritos
![Prototipo de favoritos](capturas/prototipo/Favoritos.png)
#### Inicio en Modo Oscuro
![Prototipo de inicio en modo oscuro](capturas/prototipo/InicioOscuro.png)
#### Detalle de producto en modo oscuro
![Prototipo de detalle de producto en modo oscuro](capturas/prototipo/DetallesOscuro.png)

## 4. Validación y pruebas
### 4.1 Metodología
Las tareas que he encargado a los usuarios testeadores son las siguientes:
* __Tarea 1:__ Comprar Vestido Estampado colores claros talla 3 años.
* __Tarea 2:__ Comprar Vestido Estampado colores oscuros talla 4 años.
* __Tarea 3:__ Comprar Vestido Estampado colores claros talla 4 años.
### 4.2 Resultados                           (tabla con mín. 2 participantes)
| Usuario | Tarea | Éxito | Tiempo | Errores |
| --- | --- | --- | --- | --- |
| Paula | Tarea 1 | Éxito | 10 segundos | "Hubiera tardado menos si me hubiera dado cuenta de la guía de tallas" |
| Paula | Tarea 2 | Fracaso | 20 segundos | "No me dejaba seleccionar otra prenda que no sea el conjunto claro" |
| Paula | Tarea 3 | Fracaso | 20 segundos | "No funcionaba el botón 4 años" |
| Diego | Tarea 1 | Éxito | 14 segundos | "Ningún problema, tardé un poco al desconocer la interfaz" |
| Diego | Tarea 2 | Fracaso | 26 segundos | "No me deja cambiar el color de la prenda" |
| Diego | Tarea 3 | Fracaso | 29 segundos | "No funciona los botones de tallas |
### 4.3 Iteraciones y mejoras               (antes/después)
#### Antes
![antes](capturas/iteracion/antes.png)
#### Después
![despues](capturas/iteracion/despues.png)
#### Justificación
Después de que los usuarios de prueba detectasen errores a la hora de seleccionar tallas y color de la ropa en el carrusel de imagenes, he creado 3 frames adicionales de la pantalla de detalles que contengan las distintas variantes de los componentes afectados. Después de esto, al probar nuevamente, funciona correctamente 

## 5. Entrega y documentación final
### 5.1 Justificación del diseño propuesto
He propuesto un diseño de aplicación minimalista para evitar la fatiga visual a nuestro público objetivo (padres y abuelos que posiblemente no entiendan mucho de tecnología) y conseguir una experiencia de usuario sencilla y fluida al tener elementos muy simplificados. He apostado por colores azules suaves ya que estos transmiten confianza, seguridad, tranquilidad y limpieza, aparte de que aporta un toque tierno, alegre y acogedor, cosas muy características de la infancia. En cuanto a la tipografía, he apostado por utilizar roles personalizados de Roboto ya que esta tipografía es muy sencilla y facil de leer en comparación con otro tipo de tipografía, aparte de que es facilmente personalizable para ciertos elementos de la interfaz.  
También es importante aclarar que he escogido la opción de Android Grande en lugar de Android Compact ya que este último no tenía la resolución obligatoria de la tarea (360x800) mientras que la opción de Android Grande sí.

### 5.2 Recomendaciones y pasos a seguir
* Ampliaría el mapeo del modo oscuro ya que aunque ya estan formalizado en estilos.json es bueno testar el comportamiento de los contenedores en entornos de baja luminosidad y oscuros.
* Realizaría pruebas de usabilidad con lectores de pantalla para verificar que los elementos de la pantalla como textos e imagenes mantienen un orden lógico
* Incluiría animaciones de Smart Animate avanzadas para simular el estado en elementos como los corazones en favoritos o transiciones entre pantallas

## 6. Referencias bibliográficas              (mín. 4, APA 7, exportadas desde Zotero)
App Store. (2001, 10 julio). GOCCO - Valoraciones y reseñas - App Store. App Store. https://apps.apple.com/es/app/gocco/id1178614713?see-all=reviews&platform=iphone

Trusted Shops. (2026, 14 agosto). Opiniones sobre boboli.es/es: Lee las 4044 valoraciones sobre boboli.es/es. Nota Total: Excelente Para boboli.es/es. https://www.trustedshops.es/evaluacion/info_X32A5CA30C0352BA411CF5B403189FF1D.html?stars=3

Boboli. (s. f.). Tienda Online Boboli | Ropa Infantil con Diseño y Calidad. https://www.boboli.es/es/

Trustindex. (2026, 19 mayo). PatPat Reviews 2026 | Trustindex.io. Trustindex.io. https://www.trustindex.io/reviews/eur.patpat.com

Productos de PatPat. (s. f.). PatPat. https://www.patpat.com/es/products/christmas-family-matching-long-sleeves-very-merry-green-tops-allover-pattern-pants-pajamas-sets-flame-resistant-mediumspringgreen

Grau, B. (2024, 17 mayo). ¿Por qué es importante el diseño centrado en el usuario: cómo mejorar su experiencia en aplicaciones y sitios web? - ciclick · web solutions. Ciclick · Web Solutions. https://es.ciclick.net/importancia-diseno-centrado-en-el-usuario/

## Palabra del día: 29
