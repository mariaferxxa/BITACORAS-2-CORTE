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
Señal de referencia: es la entrada que queremos que siga el sistema. la unidad depende del sistema
comparador: este bloque compara la señal de referencia con la señal real que esta saliendo del sistema, o sea la retroalimentacion y a su salida tenemos el error
controlador: El controlador toma el error y genera una accion de control
Actuador: Convierte la señal del controlador en una ccion fisica que pueda influir sobre la planta, ejecuta las ordenes del controlador
planta: es el sistema fisico que queremos controlar
sensor: mide la salida del sistema y la convierte en una señal electrica que se puede comparar nuevamente con la referencia. esta señal se retoalimenta al comparador

## Ejemplos
### Ejemplo 1:
Se tiene un sistema en lazo abierto con un tiempo de establecimiento de 2seg y se propone reducir el tiempo de establecimiento a 1seg
$$G_{}(s)=\frac{0.25}{s+2}$$

se añade el controlador

$$G_0{}(s)=\frac{k_{p}\frac{0.25}{s+2}}{1+k_{p}\frac{0.25}{s+2}}$$

$$G_0{}(s)=\frac{0.25k_{p}}{{s+2}+k_{p}}$$

se plantea la funcion de transferencia en lazo cerrado en su forma canonica 

$$G_0{}(s)=\frac{\frac{0.25k_{p}}{{s+2}+k_{p}}}{\frac{0.25k_{p}}{{s+2}+k_{p}}+1}$$

$$\tau=\frac{1}{2+0.25k_{p}}$$

$$t_{s}=4*\tau=\frac{4}{2+0.25k_{p}}=1$$  necesitamos que este nuevo tiempo sea igual a 1

$$4=2+0.25k_{p}$$         $$ k_{p}=\frac{4-2}{0.25}=0.8$$

necesitamos un controlador con ganancia de 8

## Conclusiones
Los controladores proporcionales son una herramienta eficaz para modificar el comportamiento dinamico de un sistema sin necesidad de cambiar su estructura fisica
El diseño adecuado del controlador depende del analisis de la funcion de tranferencia del sistema en lazo cerrado
