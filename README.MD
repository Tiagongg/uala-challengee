Uala Challenge 

Funcionalidades Principales

    "Búsqueda de Ciudades: Proporciona la opción de buscar ciudades por nombre a través de un TextField. La búsqueda es dinámica y ajusta la lista de ciudades mientras el usuario escribe."

   "Filtro de Favoritos: Incluye un Switch para cambiar entre la visualización de todas las ciudades o únicamente las favoritas."

   Navegación hacia la Pantalla de Mapa: Al seleccionar una ciudad, se redirige a una pantalla de detalles que despliega un mapa centrado en las coordenadas de la ciudad elegida.
    Mapa con Marcador: En la pantalla de detalles, se integra un mapa de Google Maps con un marcador que indica la ubicación exacta de la ciudad (latitud y longitud).

Estructura del Proyecto
MainViewModel

El MainViewModel administra toda la lógica relacionada con la pantalla principal, incluyendo:

    Búsqueda: Utiliza un StateFlow denominado searchQuery, el cual la interfaz observa para actualizar la lista de ciudades según el texto ingresado.
    Filtro de Favoritos: Implementa un segundo StateFlow llamado isFavouritesOnly que controla si se muestran todas las ciudades o solo las marcadas como favoritas.
    Navegación mediante eventos: A través de un Channel, el ViewModel genera eventos de navegación que la UI consume. Esto asegura que la lógica de navegación esté desacoplada del NavController.

Principales métodos del ViewModel:

    onSearchQueryChanged(query: String): Actualiza la lista de ciudades filtrándolas por el texto ingresado.
    onToggleFavourites(onlyFavourites: Boolean): Cambia entre la visualización de todas las ciudades o únicamente las favoritas.
    navigateToMap(lat: Double, lon: Double): Genera un evento de navegación que contiene las coordenadas de la ciudad seleccionada.

MainScreen

La pantalla principal muestra una lista de ciudades, permitiendo al usuario realizar búsquedas y aplicar el filtro de favoritos. La MainScreen observa los datos del ViewModel para reflejar los cambios en la UI automáticamente. También responde a los eventos de navegación para redirigir al mapa cuando el usuario selecciona una ciudad.
Componentes Clave:

    TextField de Búsqueda: Incluye un TextField con un leadingIcon para iniciar la búsqueda y un trailingIcon para borrar el texto.
    Switch de Favoritos: Un interruptor que alterna la vista para mostrar solo las ciudades favoritas.
    CityCard: Cada ciudad se presenta en una Card que permite marcarla como favorita y navegar a la pantalla de mapa correspondiente.

Detalles Técnicos:

    GoogleMap: Muestra un mapa con un marcador ubicado en las coordenadas de la ciudad seleccionada.

Decisiones de Implementación

    Navegación mediante eventos: Se implementó un patrón basado en eventos en el ViewModel, empleando Channel y StateFlow para gestionar la navegación. Esto garantiza una separación clara entre la lógica de negocio y la interfaz de usuario.

    Google Maps en Compose: La integración de Google Maps se realizó mediante la librería oficial maps-compose, que permite una incorporación sencilla de mapas en composables. Esta decisión optimiza el uso de Compose y facilita el mantenimiento del código.

    Filtrado de Ciudades: La lógica implementada en el ViewModel combina eficientemente los filtros de búsqueda y favoritos, asegurando un rendimiento fluido y sincronización constante del StateFlow con la interfaz gráfica.
#   U a l a - C h a l l e n g e 
 
 