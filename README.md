# Cajero automático — Spring Core e inyección de dependencias

**Autor:** José Rodrigo Benítez Rivera

## Cómo correrlo

    ./correr.sh App final-app
    ./probar.sh final

## Las piezas

| Bean     | Clase         | Cómo lo declara Spring (@Component o @Bean) | Singleton o prototype   |
| ---------------------- | ---------------------- | ----------------- | --------- |
| configuracionBanco   | ConfiguracionBanco   | @Configuration  | Singleton |
| antifraudePorMonto   | AntifraudePorMonto   | @Component      | Singleton |
| cajeroAutomatico     | CajeroAutomatico     | @Component      | Singleton |
| notificadorConsola   | NotificadorConsola   | @Component      | Singleton |
| repositorioEnMemoria | RepositorioEnMemoria | @Component      | Singleton |
| reloj                | Clock                | @Bean           | Singleton |

## Boleto de salida

1. ¿Qué es la inyección de dependencias? Explícalo con el cajero, en tus palabras.
Permite que las clases reciban los objetos que necesitan sin tener que crearlos directamente. Esto reduce el acoplamiento y facilita cambiar implementaciones y realizar pruebas.

2. En la MP-1, ¿quién decidía qué antifraude usaba el cajero? ¿Y desde la MP-2?
En MP-1, los objetos se crean manualmente desde main. Por otro lado, en MP-2, se registran mediante métodos @Bean dentro de una clase @Configuration. En MP-3, las clases se registran automáticamente mediante @Component y @ComponentScan.

3. ¿Cuándo usarías @Bean en vez de @Component? Da el ejemplo de hoy.
@Component se utiliza normalmente en clases propias que Spring puede detectar automáticamente. @Bean se usa cuando se necesita crear un objeto mediante un método, por ejemplo, al configurar un Clock o una clase de una biblioteca externa.

4. ¿Qué gana: @Primary o @Qualifier? ¿Por qué tiene sentido?
@Primary indica cuál bean debe preferirse por defecto cuando hay varias implementaciones compatibles. @Qualifier permite indicar específicamente cuál se quiere utilizar en un punto de inyección.

5. En tu proyecto de Empleados de la Semana 3 nunca escribiste @ComponentScan. ¿Quién lo hace? (Pista: abre la
   anotación @SpringBootApplication con Ctrl+clic y busca las anotaciones que tiene arriba.)
@SpringBootApplication incluye @ComponentScan, por lo que Spring Boot puede detectar los componentes del paquete de la clase principal y sus subpaquetes, sin necesidad de añadir esa anotación por separado en la configuración habitual.
