# 🔢 EDO Lineal a Coeficientes Constantes (Orden 1-3)


Resolver de Ecuaciones Diferenciales Ordinarias lineales con coeficientes constantes de hasta tercer orden. Implementa métodos analíticos completos incluyendo variación de parámetros para soluciones particulares.

---

## 🚀 Características Principales

- **Soporte hasta orden 3:** Resuelve EDOs lineales de primer, segundo y tercer orden con coeficientes constantes.
- **Detección automática de raíces:** Identifica y clasifica raíces del polinomio característico (reales, repetidas, complejas).
- **Dos modos de salida:**
  - **Modo "a" (Answer):** Muestra únicamente las soluciones finales.
  - **Modo "p" (Process):** Desglose paso a paso del método completo.
- **Método de variación de parámetros:** Calcula soluciones particulares usando Wronskiano para EDOs no homogéneas.
- **Transformación automática:** Convierte la EDO en polinomio característico mediante sustitución de derivadas.

---

## 💻 Instalación y Configuración

### 1. Transferencia a la Calculadora

1. Conecta tu TI-Nspire a la PC mediante el software **TI-Nspire CX Student Software** o **Computer Link**.
2. Copia el archivo `.tns` que contiene la función `edo_lineal` a la carpeta **MyLib** de tu dispositivo.
3. En la calculadora, presiona la tecla **doc**, selecciona **6: Refresh Libraries** (Refrescar bibliotecas).

---

## 🛠️ Modo de Uso y Sintaxis

### Sintaxis General

```ti-basic
edo_coef\edo_coef(ecuación, modo)
```

**Parámetros:**
- `ecuación`: EDO lineal en formato estándar (ej: `y'''+2y''-y'=x^2`)
- `modo`: 
  - `"a"` - Muestra solo resultados finales (Answer)
  - `"p"` - Muestra proceso completo paso a paso (Process)

---

## 📚 Ejemplos de Uso

### Ejemplo 1: EDO de Segundo Orden (Modo Resultados)

**EDO:** `y'' - 5y' + 6y = 0`

```ti-basic
edo_coef\edo_coef(y''-4*y'+4*y=^(2*x),a)
```

**Salida esperada:**
- Polinomio característico: `r² - 5r + 6 = 0`
- Raíces: `r₁ = 3, r₂ = 2`
- Solución general: `y(x) = c₁·e^(3x) + c₂·e^(2x)`

---

### Ejemplo 2: EDO de Tercer Orden con Raíces Repetidas (Modo Proceso)

**EDO:** `y''' - 3y'' + 3y' - y = 0`

```ti-basic
edo_coef\edo_coef(y''' - 3*y'' + 3*y' - y = 0, p)
```

**Salida esperada (modo "p"):**
1. EDO original
2. Polinomio característico
3. Raíces (r₁ = r₂ = r₃ = 1)
4. Clasificación: raíces reales repetidas
5. Solución general con términos x y x²
6. Proceso completo de derivación

---

### Ejemplo 3: EDO No Homogénea con Variación de Parámetros

**EDO:** `y'' - 4y' + 4y = e^(2x)`

```ti-basic
edo_coef\edo_coef(y'' - 4*y' + 4*y = e^(2*x),p)
```

**Salida esperada:**
- Solución homogénea (raíces repetidas)
- Cálculo del Wronskiano
- Sistema de ecuaciones para variación de parámetros
- Solución particular
- Solución total (homogénea + particular)

---

### Ejemplo 4: EDO con Raíces Complejas

**EDO:** `y'' + 4y' + 13y = 0`

```ti-basic
edo_coef\edo_coef(y'' + 4*y' + 13*y = 0,a)
```

**Salida esperada:**
- Raíces complejas: `r = -2 ± 3i`
- Transformación a forma trigonométrica
- Solución: `y(x) = e^(-2x)(c₁·cos(3x) + c₂·sin(3x))`

---

## 🔍 Métodos Implementados

### 1. Polinomio Característico

Transforma la EDO lineal:
```
aₙy⁽ⁿ⁾ + aₙ₋₁y⁽ⁿ⁻¹⁾ + ... + a₁y' + a₀y = f(x)
```

En polinomio característico:
```
aₙrⁿ + aₙ₋₁rⁿ⁻¹ + ... + a₁r + a₀ = 0
```

### 2. Clasificación de Raíces

- **Raíces reales distintas:** Solución con exponenciales simples
- **Raíces reales repetidas:** Solución con términos x, x², etc.
- **Raíces complejas:** Transformación a cos/sin con parte real exponencial

### 3. Variación de Parámetros

Para EDOs no homogéneas:
- Calcula el Wronskiano W[y₁, y₂, ...]
- Resuelve el sistema para v'₁, v'₂, ...
- Integra para obtener v₁, v₂, ...
- Construye solución particular yₚ(x)

---

## 📊 Estructura de Salida (Modo "p")

El modo proceso muestra:

**(₀)** EDO original  
**(₁)** Polinomio característico  
**(₂)** Raíces del polinomio  
**(₃)** Solución general (homogénea)  
**(₄)** Solución particular (si aplica)  
  - (₄.₁) Sistema de ecuaciones  
  - (₄.₂) Cálculo del Wronskiano  
**(₅)** Solución total  

---

## ⚠️ Notas Importantes

- La ecuación debe estar en formato estándar con coeficientes constantes
- Para EDOs no homogéneas, el término derecho puede ser cualquier función de x
- El modo "p" es ideal para aprendizaje y verificación paso a paso
- El modo "a" es más rápido para obtener resultados directos

---

## 🔮 Roadmap: Posibles Extensiones

- [ ] Soporte para EDOs de orden superior (4+)
- [ ] Método de coeficientes indeterminados como alternativa
- [ ] Condiciones iniciales para encontrar constantes c₁, c₂, c₃
- [ ] Gráficas de soluciones
- [ ] Exportación de soluciones a formato CAS

---

## 🎯 Posibles Usos

Este proyecto está diseñado para diversos escenarios:

- **Estudiantes de ingeniería:** Herramienta práctica para resolver y verificar EDOs lineales en cursos de matemáticas aplicadas.
- **Aprendizaje autodidacta:** Ideal para quienes estudian ecuaciones diferenciales por cuenta propia y necesitan ver el proceso paso a paso.
- **Validación de ejercicios:** Verifica rápidamente tus soluciones manuales y comprende dónde pudiste haber cometido errores.
- **Apoyo en enseñanza:** Profesores pueden usarlo para demostrar métodos de resolución en clase con ejemplos interactivos.

---

## 📢 Contribuciones

¿Quieres mejorar el proyecto?

Este es un proyecto de código abierto y bienvenimos cualquier tipo de contribución:

- **Reporta bugs:** Si encuentras algún error en el cálculo o comportamiento inesperado.
- **Propón mejoras:** Ideas para nuevas funcionalidades, optimizaciones o mejoras en la interfaz.
- **Extiende nuevos métodos:** Añade soporte para otros métodos de resolución de EDOs (coeficientes indeterminados, transformadas de Laplace, etc.).

---

## ⚖️ Licencia

Proyecto de código abierto. Este software es libre de usar y modificar para fines educativos y académicos.

---

## 👨‍💻 Autor

Proyecto desarrollado por Jose V. Jimenez. Este software es de código abierto y está diseñado para potenciar el aprendizaje y la 
resolución de problemas en el ámbito de ecuaciones diferenciales lineales.

---


