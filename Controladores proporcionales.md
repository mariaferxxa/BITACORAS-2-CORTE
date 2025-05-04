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
**Señal de referencia:** es la entrada que queremos que siga el sistema. la unidad depende del sistema

**comparador:** este bloque compara la señal de referencia con la señal real que esta saliendo del sistema, o sea la retroalimentacion y a su salida tenemos el error

**controlador:** El controlador toma el error y genera una accion de control

**Actuador:** Convierte la señal del controlador en una ccion fisica que pueda influir sobre la planta, ejecuta las ordenes del controlador

**planta:** es el sistema fisico que queremos controlar

**sensor:** mide la salida del sistema y la convierte en una señal electrica que se puede comparar nuevamente con la referencia. esta señal se retoalimenta al comparador

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

## Ejercicios
### Ejercicio 1.
Diseñar un controlador de accion proporcional para que el sistema se comporte sub-amortiguado

 $$G(s)=\frac{1}{s^{2}+12s+16}$$

#### Paso 1.
Se analiza la respuesta del sistema en lazo abierto

$$\omega_{n}=\sqrt{16}=4$$

$$2\zeta(4)=12$$

$$\zeta=\frac{12}{2(4)}=1.5 \longrightarrow sistema sobreamortiguado $$

#### Paso 2.
Se obtiene la funcion en lazo cerrado

$$Go(s)=\frac{k_{p}}{s^{2}+12s+16+k_{p}}$$

#### Paso 3.
Para garantizar la respuesta $\zeta\lt 1$ 

Se toma $\zeta\lt 0.8$ como factor de amortiguamiento

$$2 \zeta \omega_{n}=2 * 0.8*\sqrt{16+k_{p}}=12$$

$$1.6*\sqrt{16+k_{p}}=12$$

$$\sqrt{16+k_{p}}=\frac{12}{1.6}$$

$$(\sqrt{16+k_{p}})^{2}=(\frac{12}{1.6})^{2}$$

$${16+k_{p}}=56.25\longrightarrow k_{p}=56.25-16\longrightarrow k_{p}=40.25$$

### Ejercicio 2.
Diseñar un controlador que garantice la salida en un tiempo de 2 segundos

$$G=\frac{s+4}{s^{2}+5s+8}$$

#### Paso 1.
Hallar el lazo cerrado del sistema

$$Go(s)=\frac{k_{p}(s+4)}{s^{2}+5s+8+k_{p}(s+4)}$$

#### Paso 2.
Hallar los parametros

$$2\zeta\omega_{n}=5+k_{p}$$

$$\omega_{n}^{2}=8+4k_{p}$$

#### Paso 3.
Despejar y hallar kp

$$2\zeta\omega_{n}=5+k_{p}$$

$$\zeta\omega_{n}=\frac{5+k_{p}}{2}$$

$${5+k_{p}}=4$$

$${k_{p}}=4-5$$

$${k_{p}}=-1$$




## Conclusiones
El controlador proporcional es una herramienta fundamental en el diseño de sistemas de control por su simplicidad y facilidad de implementación, siendo especialmente útil en sistemas donde no se requiere eliminar completamente el error en estado estacionario.

Si bien el controlador proporcional no siempre es la solución definitiva, representa una base esencial para entender controladores más complejos como los PI y PID, y su estudio permite fortalecer los fundamentos del análisis y diseño de sistemas de control.

Aunque el uso de una ganancia proporcional adecuada puede mejorar significativamente la velocidad de respuesta y reducir el error transitorio, un mal ajuste puede provocar sobrepaso, oscilaciones e incluso inestabilidad en el sistema.


