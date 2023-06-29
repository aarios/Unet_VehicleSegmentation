# Unet_VehicleSegmentation
Reto solucionado de segmentación de imágenes aéreas para la detección automática de vehículos. Este proyecto se lleva acabo en el marco del Macroentrenamiento en Inteligencia Artificial (MeIA) impartido por la red macro de universidades de latinoamerica y el caribe. 

# Profesores a cargo
Este modulo se desarrolló bajo la tutoría y acompañamiento del equipo de la Universidad Nacional de Colombia de la Facultad de Minas, especificamente, miembros del Grupo de Investigación y Desarrollo en Inteligencia Artificial - GIDIA:

- John William Branch,Ph. D
- John Rovbbert Ballesteros Branch,Ph. D
- Mateo Cano, M.Sc
- Maria Camila Durango, M.Sc
- Camilo Laiton, M.Sc

# Miembros del equipo que desarrolló este reto

Este reto fue desarrollado por un equipo multidisciplinar de diferentes universidades participantes en el macroentrenamiento:

-	Juan Camilo Arteaga Ibarra (camilo.arteaga1@udea.edu.co): Estudiante de Ingeniería Electrónica de la Universidad de Antioquia ubicada en Medellín, Colombia.
-	As Augusto Rios Muñoz (aarios@unal.edu.co): Ingeniero químico y actual estudiante de la Maestría en Analítica de la Facultad de Minas de la Universidad Nacional de Colombia ubicada en Medellín, Colombia.
-	Wassilla Ajbar (wassila.ajbar@gmail.com): Licenciada en Ingeniería Quimica de la Facultad de Ciencias y Técnicas de Tánger de la Universidad Abdelmalek Esaadi uibicada en Marruecos. M.Sc y Ph.D en el Centro de Investigación en Ingeniería y Ciencias Aplicadas de la Universidad Autónoma del Estado de Morelos. México. Actualmente pasante posdoctoral de la Universidad Autonoma de México, Ciudad de México, México.

# Metodología y descripción general

El reto consiste en la optimización y mejoramiento de la arquitectura U-net suministrada por los profesores programada específicamente para la segmentación automática de vehículos en imágenes tomadas por drones en Colombia. Adicionalmente, se requiere implementar una etapa de aumentación de datos y un mejoramiento de las capacidades de predicción del algoritmo ya sea sintonizando hiperparametros, funciones de activación, el tamaño de la partición de las imágenes ó la estructura de la U-net entregada. 

Para este caso de estudio se realizaron variaciones en la función de la capa de salida entre tanh y sigmoide obteniendo resultados interesantes, sin embargo, la función sigmoide presenta un ajuste y precisión en la predicción. Para la función tanh se probaron diferentes épocas, tamaño de la imagen y aumento en la cantidad de neuronas. El incremento en la cantidad de neuronas en las capas de convolución demostró una alta capacidad para la detección de vehículos en imágenes de alta ambigüedad (vehículos fantasma o zonas donde los vehículos no están completos) pero predice vehículos donde solo existen líneas de trafico u otros objetos presentes como canecas de basura o detalles en los techos. 

La disminución en el tamaño del parche mejora la predicción de imágenes con alta ambigüedad, pero extiende la predicción a objetos que no son vehículos. Por otro lado, la implementación de etapas de aumentación disminuyó considerablemente en la capacidad de predicción y por el contrarió entregaba resultados completamente alejados del esperados desde el “true mask”.

Por otro lado, se probaron funciones de perdida diferentes a la predeterminada (binary_cross_entropy) como sparse_entropy, tversky y dice_loss obteniendo un resultado importante cuando se implementa la función de perdida dice_loss por lo que fue implementada en la versión final. Por otro lado, la cantidad de neuronas en el cuello de botella se redujo a 512 obteniendo resultados adecuados mejorando la precisión y los resultados para el conjunto de imágenes resultado. 

Finalmente, se modificaron los siguientes parámetros PONER PARAMETROS MODIFICADOS FINALMENTE.

