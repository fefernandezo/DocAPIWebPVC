# Documentación


## Obtener Modelos de ventanas
#### Obtiene las variables de todos los modelos de ventanas de PVC para ser utilizados en la plataforma web.

 GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetModels](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetModels)
 
 
#### Retorna JSON Text:
    -ID (string) : Id del modelo.

    -Nombre (string): Nombre del modelo.

    -Descripcion (string): Descripcion del modelo.

    -Imagenes (string[]): URL imágenes disponibles para el modelo.

    -Colores (string[]): Colores disponibles para el modelo.
    
    -ImgModelo (string) : Imágen principal del modelo.
    
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

 GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetVidrios](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetVidrios)
 
 
 #### Retorna JSON Text:
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
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetValue](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetValue)
  
  ### Parámetros:
     -IDMODEL (string): ID del modelo utilizado.
     -IDVIDRIO (string): ID del vidrio utilizado.
     -COLOR (string): Color utilizado.
     -CANT (double): Cantidad de productos, solo números enteros.
     -ANCHO (double): Ancho del producto en milímetros.
     -ALTO (double): Alto del producto en milímetros.
     
 #### Retorna JSON Text:
    -IDENDODET (string): Siempre retorna null (no utilizable).
    
    -IDENDO (string): Siempre retorna vacío (no utilizable).
    
    -IDMODELO (string): Retorna el ID del modelo de ventana ingresada por el usuario.
    
    -NOMBRE (string): Retorna el nombre utilizado por el sistema para identificar el producto.
    
    -POS_NR (string): Siempre retorna 0 (no utilizable).
    
    -CANTIDAD (double): Retorna la cantidad ingresada por el usuario.
    
    -ANCHO (double): Retorna el Ancho ingresado por el usuario.
    
    -ALTO (double): Retorna el Alto ingresado por el usuario.
    
    -COLOR (string): retorna el color ingresado por el usuario.
    
    -OBSERVACION (string): Siempre retorna vacío (no utilizable).
    
    -COSTINSTUN (double): Siempre retorna 0 (no utilizable).
    
    -NETOUN (double): Retorna el precio unitario del producto en pesos chilenos (sin IVA).
    
    -NETOITM (double): retorna el precio total del item (NETOUN x CANT) sin IVA.
    
    -F_CREACION (DateTime): Retorna la fecha de creación de la simulación (no utilizable).
    
    -ESTADO (boolean): retorna el estado del producto true o false (no utilizable).
    
    -M2UN (double): Retorna el área unitaria del producto en metros cuadrados.
    
    -M2ITM (double): Retorna el área total del ítem (M2UN X CANT).
    
## Inserta un Item en la cotización
 #### dos forma de inserta un item: 
 #### - Crea una cotización e inserta un item dentro de esta. (para esto no de debe pasar id de cotización ni token)
 #### - Inserta un item dentro de una cotización existente. (para esto es necesario pasar el id de la cotización y el token)
 
 ## En todos los caso es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/SetItem](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/SetItem)
 
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
     - IDCOT (string): id de la cotización (acepta valores nulos para crear una nueva)
     - TOKEN (string): token de la cotización (acepta valores nulos para crear una nueva)
  ### Parámetros:
     -IDMODEL (string): ID del modelo utilizado.
     -IDVIDRIO (string): ID del vidrio utilizado.
     -COLOR (string): Color utilizado.
     -CANT (double): Cantidad de productos, solo números enteros.
     -ANCHO (double): Ancho del producto en milímetros.
     -ALTO (double): Alto del producto en milímetros.
     -OBS (string): Campo utilizado para identificar el item (V01,V02, ETC). generalmente es ingresado por el usuario
     
 #### Retorna JSON Text:
    -IDCOT (string): Id de la cotización.
    -TOKEN (string): Token de la cotización.
    -GENERADO (boolean): true/false.


## Obtiene los Items de una cotización
 
 #### De aquí se obtienen todos los items de la cotización, para esto es necesario tener el ID de la cotización y el Token.
 
 ## En todos los caso es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetItems](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetItems)
 
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
     
  ### Parámetros:
     - IDCOT (string): Id de la cotización.
     - TOKEN (string): Token de la cotización.
     
 #### Retorna JSON Text:
 ### Retorna dos objetos: Detalle, Vidrio
    -Detalle(objeto):
       -IDENDODET (string): id del item.
     -IDENDO(string): id de la cotización.
     -IDMODELO(string): Id del modelo utilizado.
     -NOMBRE(string): Descripción del item.
     -POS_NR(int): Número del item.
     -CANTIDAD(int): Cantidad.
     -ANCHO(double):ancho.
     -ALTO(double):alto.
     -COLOR(string):color.
     -OBSERVACION(string): Nombre de identificación del item.
     -NETOUN(double): Neto unitario.
     -NETOITM(double): Neto del item.
     -F_CREACION(Datetime): Fecha de creación.
     -ESTADO(boolean): estado.
     -M2UN(double): Metros cuadrados unitarios.
     -M2ITM(double): Metros cuadrados del item.
     -URLIMG(string): Imágen a escala referencial del item.
     
    -Vidrio(objeto):
    -ID (string): Id del vidrio.
    -Nombre (string): Nombre del Vidrio.
    -Descripción (string): Descripción del vidrio.
    -Codigos (string[]): Códigos de Alfak de la composición del DVH.
    -IAcustica (int): Indicador de acústica del 1 al 3.
    -ISolar (int): Indicador solar del 1 al 3.
    -ITermica (int): Indicador térmico del 1 al 3.
    -ISeguridad (int): Indicar de seguridad del 1 al 3.
    -Estado (boolean): Estado del vidrio true o false.

## Eliminar un item
 #### Elimina un item de una cotización determinada
 
 ## En todos los caso es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/DeleteItem](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/DeleteItem)
  
  
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
     - IDCOT (string): id de la cotización (obligatorio)
     - TOKEN (string): token de la cotización (obligatorio)
     
  ### Parámetros:
     -IDENDODET (string): ID del item.
     
     
 #### Retorna JSON Text:
 true/false
 
 
   ## Obtener las regiones disponibles
 #### Obtiene el objeto de las regiones que están habilitadas
 
 ## En todos los casos es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetRegiones](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetRegiones)
  
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
   
     
 #### Retorna JSON Text:
    retorna objeto.
    
 
 
 ## Obtener las comunas disponibles para la region seleccionada
 
 #### Obtiene el objeto de las comunas disponibles para la region seleccionada
 
 ## En todos los casos es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetComunas](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetComunas)
  
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
   
     ### Parámetros:
     -codigo: Codigo de la region
     
 #### Retorna JSON Text:
    retorna objeto.

 
 
   ## Poner costo de despacho
 #### pone o saca el costo de despacho de la cotizacion
 
 ## En todos los casos es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/Despachoweb](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/Despachoweb)
  
  
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
     - IDCOT (string): id de la cotización (obligatorio)
     - TOKEN (string): token de la cotización (obligatorio)
     
  ### Parámetros:
     -ConDespacho (string): Acepta los siguientes valores:
     --NO: Quita la instalacion.
     --SI: Pone instalacion a la cotizacion.
     -CodRegion (string): codigo de la region.
     -CodComuna (string): codigo de la comuna.
     -Direccion (string): direccion de despacho
     
     
     
 #### Retorna JSON Text:
 Objeto de encabezado de la cotizacion
 
 
 
 
  ## Poner instalacion a la cotizacion
 #### pone o saca el costo de instalacion de la cotizacion
 
 ## En todos los casos es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/Instalacionweb](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/Instalacionweb)
  
  
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
     - IDCOT (string): id de la cotización (obligatorio)
     - TOKEN (string): token de la cotización (obligatorio)
     
  ### Parámetros:
     -ConInstalacion (string): Acepta los siguientes valores:
     --NO: Quita la instalacion.
     --SI: Pone instalacion a la cotizacion.
     
     
     
 #### Retorna JSON Text:
 Objeto de encabezado de la cotizacion
 
 ## Enviar Cotización a la base de datos
 #### Envia la cotización a la base de datos y le notifica a un ejecutivo para que se contacte con el cliente
 
 ## En todos los caso es necesario la autenticación
 
  GET: [cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/AceptarCotizacion](http://cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/AceptarCotizacion)
  
  
   ## Parámetros del Header
     - Authorization (string): Clave de identificación.
     - IDCOT (string): id de la cotización (obligatorio)
     - TOKEN (string): token de la cotización (obligatorio)
     
  ### Parámetros:
     -Nombre (string): Nombre del cliente.
     -Telefono (string): Telefono del cliente (acepta valores vacios)
     -Correo (string): Correo del cliente.
     
     
 #### Retorna JSON Text:
 True/False
