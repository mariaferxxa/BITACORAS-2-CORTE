# Estabilidad en Sistemas de Control

## Introducción

El análisis de estabilidad es fundamental en el diseño de sistemas de control. Un sistema estable garantiza que, ante una entrada acotada, la salida permanezca acotada y eventualmente tienda a un valor constante. Existen distintos métodos para evaluar la estabilidad de un sistema lineal e invariante en el tiempo (LTI), como el análisis de polos, el teorema del valor final y el criterio de Routh-Hurwitz.

## Palabras Clave
> 🔑 **Estabilidad asintótica:** Cuando la salida del sistema tiende a cero ante una entrada nula.
> 
> 🔑 **Polos del sistema:** Raíces del denominador de la función de transferencia. Su ubicación determina la estabilidad.
> 
> 🔑 **Criterio de Routh-Hurwitz:** Método algebraico que permite determinar la estabilidad de un sistema sin resolver la ecuación característica.
> 
> 🔑 **Teorema del valor final:** Herramienta que permite calcular el valor final de la salida en régimen permanente si el sistema es estable.

## Fundamento Teórico

### Teorema del Valor Final

Si los polos de \( sY(s) \) están en el semiplano izquierdo (salvo tal vez un polo en el origen), entonces:

$$
\lim_{t \to \infty} y(t) = \lim_{s \to 0} sY(s)
$$

**Ejemplo:**

Dado:

$$
Y(s) = \frac{10}{s(s+2)}
$$

Aplicamos el teorema:

$$
\lim_{t \to \infty} y(t) = \lim_{s \to 0} \left( s \cdot \frac{10}{s(s+2)} \right) = \frac{10}{2} = 5
$$

## Análisis por Ubicación de Polos

La estabilidad puede determinarse observando los polos de la función de transferencia:

- Polos en el semiplano izquierdo (parte real negativa): **estable**
- Polos en el eje imaginario (parte real cero): **marginalmente estable**
- Polos en el semiplano derecho (parte real positiva): **inestable**

**Ejemplo:**

Dado:

$$
G(s) = \frac{5}{s^2 + 6s + 5}
$$

Sus polos son las raíces de:

$$
D(s) = s^2 + 6s + 5 \Rightarrow s = -1,\, -5
$$

Ambos polos están en el semiplano izquierdo → sistema **estable**.

$$G(s)=\frac{5}{s^{2}+4}$$

Polos en s=±2j → parte real cero.
Sistema **marginalmente estable** 
## Criterio de Routh-Hurwitz

Permite determinar la estabilidad observando la primera columna de la tabla de Routh sin calcular los polos.

**Ejemplo:** Sea la ecuación característica:

$$
D(s) = s^3 + 2s^2 + 3s + 5
$$

La tabla de Routh es:

| Fila     | Coeficientes                                   |
|----------|------------------------------------------------|
| \( s^3 \) | 1            | 3                              |
| \( s^2 \) | 2            | 5                              |
| \( s^1 \) | $\( \frac{(2)(3)-(1)(5)}{2} = \frac{1}{2} \)$ | 0 |
| \( s^0 \) | 5                                              |

Todos los elementos de la primera columna son positivos → sistema **estable**.

## Aplicación en Diseño de Controlador Proporcional (P)

Dado un sistema con:

$$
G(s) = \frac{K}{s^2 + 2s + 5}
$$

Queremos determinar para qué valores de \( K \) el sistema en lazo cerrado es estable. La función de transferencia de lazo cerrado es:

$$
T(s) = \frac{KG(s)}{1 + KG(s)} = \frac{K}{s^2 + 2s + 5 + K}
$$

La ecuación característica es:

$$
D(s) = s^2 + 2s + (5 + K)
$$

Para que el sistema sea estable, todos los coeficientes deben ser positivos:

\( K > -5 \) → Para cualquier \( K > -5 \), el sistema es **estable**.

## Ejercicios
### Ejercicio 1.
Dada la funcion de transferencia, analizar si el sistema es estable o no

$$G(s)=\frac{10}{s^{2}+2s+10}$$

#### Paso 1.
los polos del sistema se obtienen del polinomio caracteristico

$$s^{2}+2s+10=0$$

$$s=\frac{-2\pm \sqrt{2^{2}-4(1)(10)}}{2(1)}=\frac{-2\pm \sqrt{-36}}{2}=-1\pm 3j$$

#### Paso 2.
Al analizar los polos, se tiene que tienen parte real negativa y parte imaginaria de 3, lo que indica una respuesta oscilatoria amortiguada. lo que nos indica que el sistema es estable

### Ejercicio 2.
Diseñar un controlador proporcional que vuelva estable el sistema en lazo cerrado

$$G(s)=\frac{1}{s^{3}+4s^{2}+3s-2}$$

#### Paso 1.
El sistema en lazo cerrado es:

$$Go(s)=\frac{k_{p}}{s^{3}+4s^{2}+3s-2+k_{p}}$$

#### Paso 2.
Usamos el criterio de Routh-Hurwitz

$${s^{3}+4s^{2}+3s+(-2+k_{p})}$$


| Grado | Coeficientes                                                            |
| ----- | ----------------------------------------------------------------------- |
| s³    | 1     3                                                                 |
| s²    | 4     K - 2                                                             |
| s¹    | $\frac{14 - K}{4}$                                                      |
| s⁰    | $K - 2$                                                                 |

#### Paso 3.
Ahora debemos despejar kp

$$\frac{14-k_{p}}{4}\gt 0\longrightarrow k_{p}\lt 14$$

$$k_{p}-2\gt 0    \longrightarrow   k_{p}\gt 2$$

Tenemos que el sistema sera estable si:

$$2\lt k_{p}\lt  14$$

## Conclusión

- La estabilidad puede evaluarse mediante ubicación de polos, análisis del valor final o criterio de Routh-Hurwitz.
- El criterio de Routh es útil en análisis de diseño sin necesidad de calcular raíces.
- Estas herramientas permiten establecer condiciones para la estabilidad y guiar el ajuste de parámetros como la ganancia \( K \).
