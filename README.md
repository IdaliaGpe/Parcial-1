# Proyecto 1

## Index
-El modelo de luz __wrap__ y __phong__ incluyendo un color para este mismo

-Soporte para __mapa de texturas__ y de __normales__ además de controlar su intensidad

-__Efecto de horizonte__, contiene el color de la iluminación (albedo)

-Efecto __banded__ que utiliza un __ramp texture__ para darle forma procedural

### Contenido
Utilizando un modelos de luz llamado __wrap__, el cual se basa del Lambert; iniciando en el color blanco, para lograr este efecto se utilizara "#pragma surface surf (nombre: en este nosotros lo nombramos como deseemos)", en este caso se le llamo Toon, se construirá el modelo de luz con: half4 LightingToon; nunca va a superar al 1 y tampoco va a llegar una sombra debajo de 0.

Dando un brillo (reflejo de la luz) a nuestro shader se utilizara el efecto __phong__ además de darle un color personalizado, para poder conseguirlo, se calculara el lambert con la normal, con el fin de calcular una nueva dirección, utilizando la función de reflect la cual refleja un vector, los reflejos pueden cambiar de posición pero no la luz y para esto se utiliza el viewdir; el specularity sirve para superponerse al albedo, el gloss para ver el tamaño que abarcara; se utiliza el max para poder proporcionar un máximo. Falloff: La caída de la sombra y en que magnitud va a ser. Llega la luz se esparce hasta que se ve negro.
Se calcula por medio de la normal: Producto punto ---> dot, el producto punto entre la normal y la dirección de la luz ---> N dot L

Añadiendo textura se utilizaran los __mapas de textura y de normales__ además de manejar la __intensidad__ de los mapas de normales, para poder guardar una textura es importante en el código márcalas como 2D; manejando la intensidad se colocara un rango de -5 a 5. Durante el código se utilizan samples2D para guardar la variable de nuestras texturas, se proporcionan coordenadas añadiéndoles el uv el cual se encarga de sacarle el color a la textura.

Efecto de horizonte llamado __Rim__ le proporcionara un brillo en las orillas a nuestro modelo, el cual inicia des del centro y finaliza hasta las orillas, para lograr esto se necesita invertirlo; no puede ser mayor que 1 y tampoco puede ser menor  0, si esto llegara a pasar, se reiniciaría, volvería a empezar y eso no es lo que se busca.
