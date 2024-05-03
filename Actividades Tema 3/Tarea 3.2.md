# Tarea 3.2 Caso real de Automata Finito

- Investigar caso de uso real de un autómata finito cual es su aplicación e implementación del mismo.

## ¿Que es un automata finito?

Un autómata finito es un modelo matemático que representa un sistema de computación con un conjunto finito 
de estados, una entrada de símbolos y reglas de transición entre estados basadas en los símbolos de entrada.

## Lector de tarjetas de crédito o débito.

# Aplicación de un Autómata Finito: Lector de Tarjetas de Crédito/Débito

## Aplicación:
Un lector de tarjetas de crédito/débito utiliza un autómata finito para procesar transacciones de manera segura y eficiente en puntos de venta, cajeros automáticos, 
y otros dispositivos similares. 

## Implementación:

### 1. Estados del Autómata:
   - **Esperando Tarjeta:** El lector espera que se inserte o pase una tarjeta.
   - **Leyendo Datos:** Una vez detectada la tarjeta, el lector lee los datos de la banda magnética o del chip.
   - **Verificando PIN:** Si es necesario, el lector solicita al usuario que ingrese su PIN para verificar la identidad.
   - **Autorizando Transacción:** Se solicita autorización al banco emisor para la transacción.
   - **Transacción Aprobada/Rechazada:** El lector recibe la respuesta del banco y aprueba o rechaza la transacción.

### 2. Símbolos de Entrada:
   - Los símbolos de entrada son los datos de la tarjeta (número, fecha de vencimiento, etc.) y, opcionalmente, el PIN.

### 3. Función de Transición:
   - Define cómo el lector cambia de estado en respuesta a los datos de entrada. Por ejemplo, si se detecta una tarjeta válida, el lector pasa de "Esperando Tarjeta"
   - a "Leyendo Datos".

### 4. Acciones:
   - En cada estado, el lector puede realizar acciones específicas, como mostrar mensajes, solicitar información adicional, o comunicarse con el banco para autorizar
   - la transacción.

### 5. Implementación Real:
   - Se realiza mediante software en el hardware del lector de tarjetas, interpretando los datos, gestionando estados y comunicándose con sistemas bancarios.

En resumen, el uso de un autómata finito en un lector de tarjetas asegura un proceso de transacción fluido y seguro, desde la detección de la tarjeta hasta la 
autorización final.

![17207334-tarjeta-de-crédito-y-lector-de-tarjetas-en-el-fondo-blanco](https://github.com/DonovanFranco/Lenguajes_Automatas_1/assets/161343179/0f76386b-18ec-4a1c-b859-9ed2c81dba4d)


## Conclusion

Los autómatas finitos son fundamentales en nuestra vida diaria, especialmente en la tecnología que utilizamos. Desde lectores de tarjetas hasta dispositivos de seguridad 
en puertas automáticas, estos modelos matemáticos proporcionan una estructura para procesos secuenciales discretos, garantizando eficiencia y seguridad en numerosas 
aplicaciones cotidianas. Su capacidad para interpretar datos, gestionar estados y tomar decisiones basadas en reglas definidas los convierte en herramientas esenciales en 
sistemas que interactúan con lenguajes formales, facilitando nuestras actividades diarias de manera confiable y automatizada.
