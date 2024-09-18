# portafolioweb

1 Estructura de Carpetas:

/public: Archivos estáticos (HTML, imágenes, favicon, etc.).
/src: Todo el código fuente de React.
/src/components: Componentes React reutilizables (p. ej., tarjetas de imágenes, encabezados).
/src/pages: Vistas de las páginas principales (Inicio, Detalle de Imagen, Login).
/src/services: Interacciones con la API y la base de datos.
/src/utils: Funciones auxiliares (p. ej., generación de IDs aleatorios).
/src/styles: Archivos CSS o SCSS globales.
/backend: Archivos PHP para manejo de datos y API.
/backend/config: Configuraciones de la base de datos (MySQL).
/backend/controllers: Controladores PHP para las operaciones CRUD.
/backend/models: Modelos de datos.
/backend/routes: Definición de rutas para interactuar con el frontend (React).
/uploads: Carpeta para almacenamiento de imágenes subidas.

2 Base de datos

Tabla Usuarios:
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL
);

Tabla imágenes:

CREATE TABLE images (
    id CHAR(6) PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    image_url VARCHAR(255) NOT NULL,
    dimensions VARCHAR(50),
    aspect_ratio VARCHAR(20),
    camera VARCHAR(100),
    focus VARCHAR(50),
    aperture VARCHAR(10),
    iso INT,
    shutter_speed VARCHAR(20),
    colors TEXT,
    user_id INT,
    categories VARCHAR(255),
    tags VARCHAR(255),
    description TEXT,
    publication_date TIMESTAMP,
    status ENUM('active', 'inactive'),
    location POINT,
    likes INT DEFAULT 0,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

3. Desarrollo del Backend con PHP

  1 Configuración de la Base de Datos:
    - Configura MySQL y crea las tablas users e images

  2 API para CRUD de Publicaciones
    - GET: Obtener imágenes con paginación para scroll infinito.
    - POST: Crear nuevas publicaciones de imágenes.
    - PUT: Actualizar detalles de una imagen (incluido el conteo de likes).
    - DELETE: Eliminar publicaciones
    
4. Desarrollo del Frontend con React
   1 Componentes principales:
     - ImageCard.js: Muestra los detalles de cada imagen.
     - ImageGrid.js: Implementa el scroll infinito para cargar imágenes de manera dinámica.
     - LoginForm.js: Gestiona el inicio de sesión para administradores.
     - AdminDashboard.js: Permite a los administradores gestionar publicaciones y usuarios.
   
   2 Implementación de Scroll infinito:
     - Utiliza la biblioteca react-infinite-scroll-component para gestionar la carga dinámica       de imágenes.
  
5. Seguridad y Autenticación

  1 Autenticación
    - Implementa sesiones para los administradores. Usa bcrypt para cifrar contraseñas.
    
  2 Protección de Rutas:
    - Protege las rutas administrativas asegurando que solo los usuarios autenticados puedan       acceder a ellas.
    
6. Implementación de Likes y Geolocalización

  1 Sistema de Likes:
    - Almacena el número total de likes directamente en la tabla images.

  2 Geolocalización:
    - Almacena latitud y longitud en la columna location de tipo POINT.
