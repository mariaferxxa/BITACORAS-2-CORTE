# Sistemas de Segundo Orden

## Introducción

Los sistemas de segundo orden aparecen con frecuencia en ingeniería y control automático, ya que modelan una gran variedad de comportamientos dinámicos, desde oscilaciones mecánicas hasta respuestas eléctricas en circuitos RLC. La caracterización y análisis de estos sistemas permiten predecir el comportamiento de un proceso ante distintos tipos de entrada, facilitando el diseño de controladores eficientes.

## Palabras Clave
- **Sistemas de segundo orden:** Sistemas cuya ecuación diferencial característica incluye una derivada de segundo orden, representados por funciones de transferencia con polinomios de segundo grado en el denominador.
> 🔑 **Función de transferencia:** Relación en el dominio de Laplace entre la salida y la entrada de un sistema lineal e invariante en el tiempo.

> 🔑 **Factor de amortiguamiento $(\zeta\)$**: Parámetro adimensional que indica el grado de amortiguamiento de la respuesta. Define si el sistema es subamortiguado, críticamente amortiguado o sobreamortiguado.

> 🔑 **Frecuencia natural $(\omega_n\)$**: Frecuencia con la que oscilaría el sistema si no existiera amortiguamiento.

> 🔑 **Sobreimpulso $(M_p\)$**: Porcentaje que la respuesta supera el valor en estado estacionario.

> 🔑 **Tiempo al pico $(t_p\)$**: Tiempo que tarda la respuesta en alcanzar su primer máximo.

> 🔑 **Tiempo de establecimiento $(t_s\)$**: Tiempo necesario para que la respuesta permanezca dentro de un margen específico (2% o 5%) respecto al valor final.

## Fundamento Teórico

La ecuación diferencial general de un sistema de segundo orden es:

$$
\ddot{y}(t) + a_1 \dot{y}(t) + a_0 y(t) = b_0 u(t)
$$

Aplicando la Transformada de Laplace (con condiciones iniciales nulas):

$$
s^2 Y(s) + a_1 s Y(s) + a_0 Y(s) = b_0 U(s)
$$

Despejando la función de transferencia:

$$
G(s) = \frac{Y(s)}{U(s)} = \frac{b_0}{s^2 + a_1 s + a_0}
$$

## Forma Canónica

Para facilitar el análisis, se utiliza la forma canónica:

$$
G(s) = \frac{K \omega_n^2}{s^2 + 2\zeta \omega_n s + \omega_n^2}
$$

Donde:
- $\( K \)$: Ganancia estática
- $\( \omega_n \)$: Frecuencia natural
- $\( \zeta \)$: Factor de amortiguamiento

## Parámetros Temporales

Para un sistema subamortiguado (\( \zeta < 1 \)):

| Parámetro                         | Fórmula                                                                 |
|----------------------------------|-------------------------------------------------------------------------|
| Tiempo al pico \(t_p\)            | $\( t_p = \frac{\pi}{\omega_n \sqrt{1 - \zeta^2}} \)$                     |
| Sobreimpulso \(M_p\)              | $\( M_p = e^{-\frac{\zeta \pi}{\sqrt{1 - \zeta^2}}} \times 100\% \)$     |
| Tiempo de estabilización (2%)    | $\( t_s \approx \frac{4}{\zeta \omega_n} \)$                             |
| Tiempo de estabilización (5%)    | $\( t_s \approx \frac{3}{\zeta \omega_n} \)$                             |

## Ejercicio 1: Sistema Subamortiguado

Dado el sistema:

$$
G(s) = \frac{36}{s^2 + 4.2s + 36}
$$

### Paso 1: Identificar parámetros del denominador

Comparando con la forma canónica:

$$
s^2 + 2\zeta \omega_n s + \omega_n^2 = s^2 + 4.2s + 36
$$

Se deduce que:
- $\( \omega_n = \sqrt{36} = 6 \)$
- $\( 2 \zeta \omega_n = 4.2 \Rightarrow \zeta = \frac{4.2}{2 \cdot 6} = 0.35 \)$

### Paso 2: Cálculo de parámetros temporales

- **Tiempo al pico:**
 
  $t_p = \frac{\pi}{\omega_n \sqrt{1 - \zeta^2}} = \frac{\pi}{6 \sqrt{1 - (0.35)^2}} \approx 0.56\,\text{s}$
  

- **Sobreimpulso:**

 $M_p = e^{-\frac{\zeta \pi}{\sqrt{1 - \zeta^2}}} \times 100\% = e^{-\frac{0.35 \pi}{\sqrt{1 - (0.35)^2}}} \times 100\% \approx 38\%$
  

- **Tiempo de estabilización (2%):**

  $t_s = \frac{4}{\zeta \omega_n} = \frac{4}{0.35 \cdot 6} \approx 1.90\,\text{s}$


## Ejercicio 2: Sistema Críticamente Amortiguado

Dado el sistema:

$$
G(s) = \frac{100}{s^2 + 20s + 100}
$$

**Solución:**
- $\( \omega_n = 10 \)$
- $\( \zeta = \frac{20}{2 \cdot 10} = 1 \)$

Respuesta a escalón unitario:

$$
Y(t) = 1 - e^{-10t}(1 + 10t)
$$

## Código en MATLAB

```matlab
% Sistema subamortiguado
wn = 6;
zeta = 0.35;
K = 1;
num = K * wn^2;
den = [1, 2*zeta*wn, wn^2];
sys = tf(num, den);
step(sys);
title('Respuesta al escalón - Sistema Subamortiguado');

% Sistema críticamente amortiguado
wn2 = 10;
zeta2 = 1;
num2 = wn2^2;
den2 = [1, 2*zeta2*wn2, wn2^2];
sys2 = tf(num2, den2);
figure;
step(sys2);
title('Respuesta al escalón - Sistema Críticamente Amortiguado');
```

## Conclusiones

- Los sistemas de segundo orden permiten predecir el comportamiento dinámico de múltiples procesos físicos.
- El factor de amortiguamiento \( \zeta \) y la frecuencia natural \( \omega_n \) determinan la forma de la respuesta.
- Mediante el análisis en el dominio de Laplace y herramientas como MATLAB, es posible visualizar y ajustar la respuesta deseada.
- Conocer los parámetros temporales clave permite diseñar controladores adecuados y mejorar el desempeño del sistema.
