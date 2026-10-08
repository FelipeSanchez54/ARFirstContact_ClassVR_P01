<snippet>
  <content><![CDATA[
# ${1:Project Name}

AR app that spawns beach balls when detecting plains and a sardine when detecting a crab image, which collide with the elements around them. 

## Installation

This app uses Unity version 6000.5.0b2. AR Foundation. Compatible with Android.

## Usage

Scan crab image and surroundings with back camera.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

University project to experiment with AR experiences using Unity's AR Foundation.

## Credits

Felipe Sánchez, Marc García, Carla Jiménez, Jordina Quesada

## License

Project under MIT lisence. You may copy, use, modify and distribute for both personal and professional purposes.

## Additional Information
AR Foundation

Name: A day at the beach.

Descripción de las tres actividades:

1. Es un AR en qué consiste que en el suelo (o en una zona plana) salga un modelo 3D en la ubicación elegida y el modelo elegido.

  
2  Esta funcionalidad permite al usuario escanear una imagen de un cangrejo con la cámara trasera del teléfono, que al ser detectada hace aparecer pelotas de play aleatorias y una sardina de considerables dimensiones con texturas realistas. 


3. En esta actividad, el usuario puede trasladarse a través del espacio mientras cierta cantidad de peces payaso van apareciendo paulatinamente. Estos aparecen de manera rotada y aleatoria, pero toman como origen de spawn los Cloud Point trackeados en el suelo. De este modo, cuando el espectador/cliente usa la funcionalidad en su espacio, ve cómo aparecen los peces y da la sensación de estar sumergido en el mar.

AR Foundation (A1):

Para empezar, el proceso ha sido crear una escena y añadir las funciones de XR, la UI ya estaba implementada.

He hecho una copia de un cuadrado de prefabs (lo he repetido 2 veces), cambiar las colisiones y medidas, eso una vez añadido el modelo 3D que he elegido por internet. 

Una vez hecho el paso anterior, he ido a las UI para añadir 2 botones más y cambiar la imagen (la imagen se debía de cambiar a sprite single) y decir que tiene un modelo propio en cada de esos nuevos botones y finalizando en cambiar el orden para meter esos 2 botones nuevos como a primeros botones elegibles.


Resultado;

AR Foundation (A2):

Para conseguir la imagen detectable se han creado en el AR mobile template un XR Origin y un AR session. Dentro del XR Origin se han añadido los componentes de AR Raycast manager, AR plane manager para detectar superficies del mundo físico y por último el AR Tracked image manager. Este último era sustitutivo del Anchor placer, que no existe en nuestra versión. Después creamos un Image reference library en el cual añadimos nuestra imagen, elegida tras un exhaustivo proceso de selección. Esta Image reference library fue vinculada al AR Tracked image manager, en el apartado de serialized library. Después se añadió en la carpeta de prefabs un modelo 3d de una sardina, el cual también se bajo el AR Tracked image manager en Tracked image prefab. Por último, hicimos otra funcionalidad de plane tracking, para la cuál pusimos una esfera con textura de pelota de playa bajo AR plane manager, en Plane prefab.  


AR Foundation (A3):  

Para seguir el hilo narrativo del proyecto, y analizando las diferentes funcionalidades de AR, se optó por seleccionar Point Clouds. Esta función, que hace un tracking por puntos de la escena, podía servir para «spawnear» animales u otros elementos reminiscientes al entorno marino. Es por ello que, se importó un modelo de un pez payaso— ClownFish en el archivo—; se extrajeron materiales y texturas y se creó una escena con un XROrigin y ARSession. La clave de la funcionalidad reside en el XROrigin, al que se le atribuyó un AR Point Cloud Manager.



En el Prefab que iba a generar en cada punto, se adjudicó el modelo del pez, pero se detectó un problema que consitía en que, al inciarlo, aparecía solamente un pez en un punto fijo trakeado.


Consecuentemente, se pensó que, para poder crear más de uno, se dtenía que usar un sistema de partículas. De hecho, analizando el sample, era usado de este modo. 
Habiendo creado “ClownFish_CPoint_Base/Small” (con los atributos correspondientes), e iniciar el test, los peces aparecían, efectivamente, en los puntos, tal y como se mencionaba en esta funcionalidad.

Sin embargo, y tal como se puede observar, la visualización de estos era muy diferente al resultado que se quería obtener. Los peces estaban anclados a las paredes y suelo y no rotaban en la dirección correcta. 

Para poder conseguir el efecto deseado, se creó un nuevo sistema de partículas “ClownFish_CPoint_PS” que lograba generar muchos peces, y se indicó en las porpiedades el límite en la vida de las  partículas; la rotación aleaoria en el eje y (para que cada pez rotase de manera distinta); y estableciendo una margen para que no se creasen más partículas de las necesarias y colapsase la futura Build.


Resumen de desarrollo:

Cada miembro del grupo ha realizado una parte del trabajo (funcionalidad de AR) y la última persona del grupo las ha juntado en una sola escena. El trabajo tiene un hilo narrativo sobre cómo es un día en la playa y juega con los diferentes elementos característicos (fauna y elementos lúdicos). 



Problemas y soluciones:

En el caso de la A3, que se especifica en el apartado superior, el problema principal fue detectar cómo poder generar más peces y evitar que se incrustasen todos en paredes y suelo. Gracias al análisis de los samples y de tests con rotaciones, gradientes y atributos del sistema de partículas, entre otros, se conisguió el resulatdo esperado.



Contribución de los miembros del grupo:

Jordina: Toda la parte 1 (excepto probar desde el móvil por problemas de compatibilidad del móvil) y un poco de documento. Los assets 3D y fotos los he tomado de internet. 

Carla: He creado la funcionalidad de Image tracking y un segundo Plane detection. He empleado mis habilidades creativas para decidir sobre la temática general del proyecto y seleccionar la imágen y los modelos de la segunda parte.

Marc: Me he encargado principalmente de desarrollar la A3 y maquetar el documento final. Entre otras de las actividades, he puesto principal atención en la nomenclatura de mis archivos para facilitar el trabajo grupal y la eficiencia; he buscado información sobre la funcionalidad y la he aplicado siguiendo el hilo narrativo del proyecto. He realizado numerosas pruebas con sistemas de partículas y he llevado a cabo diferentes tests que me permitían acotar los resultados y detectar cuales eran los atributos que permitían que funcionase.

Felipe: Me he encargado de juntar todas las funcionalidades en un solo proyecto y he creado el repositorio inicial de GItHub. He gestionado todas las As en la escena final. 

