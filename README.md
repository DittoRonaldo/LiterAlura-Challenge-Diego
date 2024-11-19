# LiterAlura-Challenge-Diego
OBJETIVO: Desarrollar un Catálogo de Libros que ofrezca interacción textual (vía consola) con los usuarios, proporcionando al menos 5 opciones de interacción. Los libros se buscarán a través de una API específica. La información sobre la API y las opciones de interacción con el usuario se detallará en la columna "Backlog"/"Listo para iniciar".


ChatGPT said:
ChatGPT
Sistema de Administración de Libros
Este proyecto consiste en una aplicación de consola desarrollada en Java con Spring Boot, diseñada para la administración de libros y autores. Permite realizar búsquedas, registrar y listar tanto libros como autores, utilizando una base de datos local o una API externa.

Ejecución de la Aplicación
El punto de entrada de la aplicación es la clase DesafioApplication, que implementa la interfaz CommandLineRunner para iniciar el programa automáticamente. El flujo comienza al llamar al método muestraElMenu() de la clase Principal, el cual despliega un menú interactivo con las funcionalidades del sistema.

Pasos para Ejecutar:
Clona o descarga el repositorio.
Verifica que tu entorno esté configurado con Java y Spring Boot.
Ejecuta la aplicación desde la clase DesafioApplication.
java
Copy code
@SpringBootApplication  
public class DesafioApplication implements CommandLineRunner {  

    private final Principal principal;  

    // Constructor que inyecta la clase `Principal` usando `@Lazy`.  
    public DesafioApplication(@Lazy Principal principal) {  
        this.principal = principal;  
    }  

    public static void main(String[] args) {  
        SpringApplication.run(DesafioApplication.class, args);  
    }  

    @Override  
    public void run(String... args) throws Exception {  
        principal.muestraElMenu();  
    }  
}  
Funcionalidades del Sistema
Menú Principal
Desde el menú interactivo puedes realizar las siguientes operaciones:

Buscar libro por título: Busca un libro en la base de datos; si no está registrado, lo obtiene y registra desde la API externa.
Listar libros registrados: Muestra todos los libros almacenados en la base de datos.
Listar autores registrados: Presenta los autores junto con sus libros asociados.
Listar autores vivos en un año específico: Permite consultar los autores vivos durante un año determinado.
Listar libros por idioma: Filtra libros según su idioma (ES, EN, FR, PT).
Salir: Cierra la aplicación.
Estructura de Paquetes
com.aluracursos.desafio.principal: Contiene la clase Principal que gestiona el menú y la lógica principal.
com.aluracursos.desafio.model: Define las clases de modelo Autor y Libro.
com.aluracursos.desafio.repository: Proporciona repositorios para interactuar con la base de datos (AutorRepository y LibroRepository).
com.aluracursos.desafio.service: Incluye servicios auxiliares como ConsumoAPI para consumir la API y ConvierteDatos para procesar la información.
Dependencias y Configuración
En la clase DesafioApplication, se definen los beans necesarios para los servicios auxiliares:

java
Copy code
@Bean  
public ConsumoAPI consumoAPI() {  
    return new ConsumoAPI();  
}  

@Bean  
public ConvierteDatos conversor() {  
    return new ConvierteDatos();  
}  
Ejemplo de Ejecución
css
Copy code
=== SISTEMA DE ADMINISTRACIÓN DE LIBROS ===  

1- Buscar libro por título  
2- Listar libros registrados  
3- Listar autores registrados  
4- Listar autores vivos en un determinado año  
5- Listar libros por idioma  
0- Salir  

Seleccione una opción:  
