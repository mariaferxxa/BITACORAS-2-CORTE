# SISTEMAS DE SEGUNDO ORDEN
En los sistemas de control, los sistemas de primer orden representan una de las bases más fundamentales. Se caracterizan por una única constante de tiempo y ganancia estática. Su comportamiento dinámico puede analizarse a través de funciones de transferencia, obtenidas al aplicar la transformada de Laplace a ecuaciones diferenciales de primer orden
## Definiciones importantes
transformada de la place
funcion de tranferencia
forma canonica
Entradas tipicas
## Estructura general y forma canonica
$$ \ddot{y}(t)+a_{1}\dot{y}(t)+a_{0}y(t)=b_{0}u(t) $$

$$s^{2}Y(s)+a_{1}sY(s)+a_{0}Y(s)=b_{0}U(s)$$

$$G(s)=\frac{Y(s)}{U(s)}=\frac{b_{0}}{s^{2}+a_{1}s+a_{0}}$$


$$ G(s)=\frac{K*\omega_{n}^{2}}{s^{2}+2\varsigma\omega_{n}s+\omega_{n}^{2}} $$



### Ejemplo
Hallar el factor de amortiguamiento y la frecuencia natural del sistema

$$G(s)=\frac{12}{s^{2}+8s+30}$$

$$\varsigma$$ = xxx

$$\omega_{n}$$ =xxx

## respuesta a un escalon
Con la entrada de un escalon se pueden dar tres diferentes tipos de respuesta

$$\varsigma\gt 1$$ sobreamotiguado

$$\varsigma\lt 1$$ sub-amortiguado

$$\varsigma=1$$ criticamente amortiguado
 ### ejemplo
 $$G(s)=\frac{12}{s^{2}+8s+30}$$
 
 ## Ejercicios
 ## Obervaciones claves
 
