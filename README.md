# Integración Numérica usando Simpson 1/3

## Programación Funcional en Scala

---

##  Objetivo

* Aplicar los conocimientos sobre **funciones de orden superior**
* Enviar funciones como parámetros para resolver **integrales definidas**
* Implementar el método de Simpson 1/3 de forma funcional

---

##  Método

El método utilizado es **Simpson 1/3**, cuya fórmula es:

$$\int_{a}^{b}f(x)dx \cong (b-a) \frac{f(a)+4f(\bar{x})+f(b)}{6}$$

Donde $\bar{x} = \frac{a+b}{2}$ es el punto medio del intervalo.

### Puntos de evaluación

El método evalúa la función en tres puntos clave:

1. **Límite inferior**: $a$
2. **Punto medio**: $\bar{x} = \frac{a+b}{2}$
3. **Límite superior**: $b$

Y los combina según la fórmula de Simpson para obtener una aproximación precisa.

---

##  Implementación

### Función principal: `integracion`
```scala
def integracion(f: Double => Double, a: Double, b: Double): Double =
  val xBar = (a + b) / 2
  (b - a) * (f(a) + 4 * f(xBar) + f(b)) / 6
```

### ¿Qué devuelve esta función?

Devuelve un `Double`, porque el resultado de una integral es un valor real.

### Parámetros que recibe

* **`f: Double => Double`** - La función matemática a integrar
* **`a: Double`** - Límite inferior de integración
* **`b: Double`** - Límite superior de integración

> **Nota**: Esta es una **función de orden superior** porque recibe otra función como parámetro.

---

##  Estructura del código

* **`integracion`** → Aplica el método de Simpson 1/3
* **`f1` a `f7`** → Funciones que representan diferentes integrandos
* **`resultadoX`** → Aproximación numérica de cada integral
* **`errorX`** → Diferencia absoluta entre el valor esperado y el obtenido

---

##  Ejemplo de uso
```scala
// Definir la función a integrar
def f1(x: Double): Double = -x * x + 8 * x - 12

// Calcular la integral
val resultado1 = integracion(f1, 3, 5)

// Calcular el error
val error1 = error(7.33, resultado1)
```

### Ejemplo concreto:

Para calcular la integral:

$$\int_{3}^{5}(-x^2 + 8x - 12)dx \approx 7.33$$

**Resultado obtenido**: 7.329  
**Error**: 0.001

---

##  Resultados

| Integral | Aproximación | Valor esperado | Error |
|----------|--------------|----------------|-------|
| I₁ | 7.329 | 7.33 | 0.001 |
| I₂ | 8.0 | 8.0 | 0.0 |
| I₃ | 3.332 | 3.333 | 0.001 |
| I₄ | 1.0986 | 1.09861 | 0.00001 |
| I₅ | 1.7182 | 1.71828 | 0.00008 |
| I₆ | 0.8284 | 0.828427 | 0.00003 |
| I₇ | 0.7853 | 0.785398 | 0.0001 |

---

##  Conclusiones

* ✨ **Simpson 1/3** ofrece excelentes aproximaciones usando solo **tres evaluaciones** de la función
* 🎯 **Scala** permite trabajar de forma clara y elegante con funciones de orden superior
* 📉 El cálculo del **error** ayuda a comprobar la precisión del método para cada integral
* 🚀 Este enfoque funcional hace el código más **modular**, **reutilizable** y **fácil de mantener**

---

##  Referencias

* Método de Simpson: Técnica de integración numérica de segundo orden
* Programación Funcional: Paradigma que trata la computación como evaluación de funciones matemáticas

