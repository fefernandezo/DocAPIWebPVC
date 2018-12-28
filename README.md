# Documentacion


## Obtener Modelos de ventanas
 GET: cproyecto.phglass.cl/ServiciosWeb/PVC.asmx/GetModels

    -ID (string) : Id del modelo.3

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
