# Diseño de controladores proporcionales
## Introduccion 
los controladores proporcionales son los mas basicos de la familia PID, aun asi son bastantes utiles dependiendo del sistemma que estemos controlando. Este tipo de controlador mide que tan lejos esta la salida del sistema con respecto a la referencia (error)
el diseño de un controlador proporcional consiste en ajustar el valor de kp para alcanzar un equilibrio entre velocidad de respuesta, precision y estabilidad.

## Conceptos claves
> 🔑 **Sistemas de control: son un conjunto de componentes diseñados para regular el comportamiento de un sistema, en funcion de una señal de entreda o refencia**

> 🔑 **Error: es la diferencia entre lo que deberia estar haciendo el sistema y lo que esta haciendo realmente**
> 
> 🔑 **Tiempo de establecimiento: es el tiempo que tarda el sistema en quedar alrededor del valor final y no volver a salirse de ahi. Es una medida de que tan rapido responde el sistema**
> 
> 🔑 **Factor de amortiguamiento: Es un parametro que indica cuanto se suaviza la respuesta del sistema, depende de la dinamica del sistema y afecta la forma de la curva de respuesta**
> 
> 🔑 **Constante de tiempo: Es un parametro que indica que tan rapido responde un sistema. se define como el tiempo que tarda la salida en alcanzar el 63,2% aproximadamente de su valor final.**
## Formulas importantes
Funcion de tranferencia en lazo cerrado

$$G_{o}(s)=\frac{K_{p}G(s)}{1+K_{p}G(s)}$$

## componentes de un sistema
comparador: a este primer componente llega la entrada o señal del sistema y la retroalimentacion en lazo cerrado y sale lo que conocemos como error
controlador:
actuador
planta
sensor

## Ejemplos
### Ejemplo 1:
Se tiene una planta con 
## Conclusiones
Los controladores proporcionales son una herramienta eficaz para modificar el comportamiento dinamico de un sistema sin necesidad de cambiar su estructura fisica
El diseño adecuado del controlador depende del analisis de la funcion de tranferencia del sistema en lazo cerrado
