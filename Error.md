# Error en estado estacionario
## Introduccion
En los sistemas de control, uno de los objetivos principales es que la salida siga con precisión una entrada de referencia. El error en estado estacionario permite evaluar cómo funciona el sistema en régimen permanente. Es fundamental analizar el error para poder diseñar sistemas precisos, confiables y estables, así como para implementar estrategias de compensación cuando sea necesario.
## Conceptos claves
**Error en estado estacionario: Es la diferencia entre la entrada de referencia y la salida del sistema cuando el tiempo tiende a infinito.**

**Función de transferencia: Relación entre la salida y la entrada de un sistema lineal.**

**Constante de error: Parámetros que permiten calcular el error en estado estacionario para distintos tipos de entrada.**
## Funcion de error
La función de error en el dominio de Laplace se define como:

$$E=R-Y$$

$$E=R-EG$$

$$E=\frac{R}{1+G}$$

## Teorema del valor final
El error en estado estacionario corresponde al valor del error cuando el tiempo tiende a infinito. Se utiliza para determinar el valor final del error que se mantiene una vez que el sistema ha alcanzado su régimen permanente.

$$\lim _{t \to \infty } f(t) = \lim _{s \to 0} sF(s)$$

## Error en estado estacionario
Para calcular el error en estado estacionario se considera el tipo de entrada al sistema. Las más comunes son:
### Entrada escalón

$$R(s)=\frac{1}{s}$$

$$E=\lim_{s \to 0} \frac{s*\frac{1}{s}}{{1+G(s)}}=E=\lim_{s \to 0}\frac{1}{{1+G(s)}}$$

Tambien llamado Error de posicion 
### Entrada rampa

$$R(s)=\frac{1}{s^{2}}$$

El error en estado estacionario es:

$$E=\lim_{s \to 0} \frac{s*\frac{1}{s^{2}}}{{1+G(s)}}=E=\lim_{s \to 0}\frac{1}{{sG(s)}}$$

Tambien llamado Error de velocidad
### Entrada Parabólica

$$R(s)=\frac{1}{s^{3}}$$

El error en estado estacionario es:

$$E=\lim_{s \to 0} \frac{s*\frac{1}{s^{3}}}{{1+G(s)}}=E=\lim_{s \to 0}\frac{1}{{s^{2}G(s)}}$$

Tambien llamado Error de aceleracion 
## Tipos de sistema
| Tipo de Sistema | Error para Escalón | Rampa  | Parabólica |
| --------------- | ------------------ | ------ | ---------- |
| Tipo 0          | k                  | ∞      | ∞          |
| Tipo 1          | 0                  | k      | ∞          |
| Tipo 2          | 0                  | 0      | k          |

## Correccion error
Por medio de una ganancia proporcional es posible reducir el error pero con este tipo de accion de control no es posible eliminarlo completamente.

$$G(s)=\frac{10}{s^{2}+2s+1}=G_{0}(s)\frac{10k_{p}}{s^{2}+2s+1+10k_{p}}$$

$$Essp=\frac{1}{1+\frac{10k_{p}}{0^{2}+2(0)+1+10k_{p}}}$$

$$Essp=\frac{(0)^{2}+2(0)+1}{0^{2}+2(0)+1+10k_{p}}=0$$

$$\frac{1}{1+10k_{p}}=\frac{{1+10k_{p}}}{1} $$

$$k_{p}=\frac{1}{0}=\infty $$

## Ejemplos
### Ejemplo 1.
sistema tipo 1 con entrada escalon:

$$G(s)=\frac{10}{s(s+2)}=\lim _{s \to 0} s\frac{1}{1+\frac{10}{s(s+2)}}*1/s$$

$$\lim _{s \to 0} \frac{1}{1+\frac{10}{s(s+2)}}=\frac{1}{1+\frac{10}{0}}=\frac{1}{\infty }=0$$

Es un error de posicion 

### Ejemplo 2.
Sistema tipo 0 con entrada rampa:

$$G(s)=\frac{5}{s+1}$$

$$\lim _{s \to 0} \frac{1}{s\frac{5}{s+1}}=\frac{1}{\frac{5(0)}{0+1}}=\frac{1}{0}=\infty $$

## Sensibilidad
La sensibilidad en control automático mide qué tanto afecta una perturbación o cambio en los parámetros del sistema a la respuesta del mismo, especialmente al error en estado estacionario. 

## Conclusiones
La función de sensibilidad refleja la capacidad del sistema para rechazar perturbaciones y adaptarse a cambios, y se relaciona directamente con el error en estado estacionario.

Un sistema de control bien diseñado debe minimizar el error garantizando así una respuesta precisa, estable y robusta frente a incertidumbres, variaciones en los parámetros del sistema o perturbaciones externas.

El error en estado estacionario es una herramienta esencial para evaluar el desempeño de un sistema de control en régimen permanente, ya que permite determinar cuán precisa es la respuesta del sistema ante entradas constantes como escalón, rampa o parábola.

