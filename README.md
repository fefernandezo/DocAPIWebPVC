# Documentación


## Obtener Modelos de ventanas
#### Obtiene las variables de todos los modelos de ventanas de PVC para ser utilizados en la plataforma web.

 GET: cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetModels
 
 

    -ID (string) : Id del modelo.

    -Nombre (string): Nombre del modelo.

    -Desripcion (string): Descripcion del modelo.

    -Imagenes (string[]): URL imágenes disponibles para el modelo.

    -Colores (string[]): Colores disponibles para el modelo.
    
    -Restricciones (object(nombre,valor)): restricciones del modelo en milímetros.
        * AnchoMin: Ancho mínimo del modelo.
        * AnchoMax: Ancho máximo del modelo.
        * AltoMin: Alto mínimo del modelo.
        * AltoMax: Alto máximo del modelo.
        * EspesorMin: Espesor mínimo del modelo.
        * EspesorMax: Espesor máximo del modelo.
        
     - Categoria: Categoría a la cual pertenece el modelo.
     - Familia: Línea de perfiles a la cual pertenece el modelo.
     
## Obtener Vidrios
#### Obtiene las variables de todos los modelos de vidrios para ser utilizados en los modelos de PVC en la plataforma web.

 GET: cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetVidrios
 
 
 
    -ID (string): Id del vidrio.
    
    -Nombre (string): Nombre del vidrio.
    
    -Descripción (string): Descripción del vidrio.
    
    -Codigos (string[]): Códigos de Alfak de la composición del DVH.
    
    -IAcustica (int): Indicador de acústica del 1 al 3.
    
    -ISolar (int): Indicador solar del 1 al 3.
    
    -ITermica (int): Indicador térmico del 1 al 3.
    
    -ISeguridad (int): Indicar de seguridad del 1 al 3.
    
    -Estado (boolean): Estado del vidrio true o false.
    
 ## Consultar un producto específico
 #### Obtiene una simulación de las variables de un producto especificado por el usuario. Sirve para saber el precio de un producto sin realizar una cotización.
 
  GET:cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetValue
  
  ### Parámetros:
     -IDMODEL (string): ID del modelo utilizado.
     -IDVIDRIO (string): ID del vidrio utilizado.
     -COLOR (string): Color utilizado.
     -CANT (double): Cantidad de productos, solo números enteros.
     -ANCHO (double): Ancho del producto en milímetros.
     -ALTO (double): Alto del producto en milímetros.
     
 
  
