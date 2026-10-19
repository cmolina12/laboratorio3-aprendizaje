# Guion — Video Laboratorio 3
Audiencia: el equipo de Ruta Alpes (personas de negocio, no necesariamente técnicas).
Límite del enunciado: **máximo 3 minutos**.

Igual que en el Lab 2, el guion trae más material del que cabe en 3 minutos, para que puedan
escoger qué decir con sus palabras. Cada bloque tiene una marca:

- 🟢 **NÚCLEO** — responde a lo que pide el enunciado. Va sí o sí.
- 🟡 **DETALLE** — enriquece la explicación, pero es lo primero que se recorta si se pasan
  de tiempo.

Al final está la versión recortada solo con los bloques 🟢, que cabe en ~3 minutos.

---

## 1. Intro y problema (0:00–0:20)

🟢 **[Natalia o Camilo]**
"Hola, somos Camilo Molina y Natalia Erazo. Ruta Alpes nos pidió responder una pregunta
concreta: ¿cuándo es más probable que un conductor acepte un cupón de cafetería o de
restaurante económico, de menos de 20 dólares por persona? La idea es dejar de enviar la
misma oferta a todos, porque eso tiene poca efectividad y a veces molesta al conductor."

🟡 **[Detalle]**
"Trabajamos con escenarios reales de conducción: el destino, la hora, el clima, quién va en el
carro, qué tan lejos queda el establecimiento, junto con el perfil y los hábitos de cada
conductor. Para cada escenario sabemos si la persona aceptó o no el cupón."

---

## 2. Cómo lo abordamos (0:20–0:45)

🟢 **[Camilo]**
"Construimos un modelo para cada cupón y comparamos tres algoritmos: regresión logística,
árboles de decisión y Random Forest. Buscamos la mejor configuración de cada uno con
validación cruzada y los evaluamos al final con un 20 % de datos que nunca vieron, usando
principalmente el F1."

🟡 **[Detalle]**
"Antes de modelar limpiamos los datos: eliminamos una variable que estaba vacía en más del
99 % de los registros, otra que siempre tenía el mismo valor, otra que repetía exactamente la
información de la dirección, y algunos registros duplicados. También encontramos que en
cafetería las clases están balanceadas, mitad acepta y mitad no, pero en restaurante el 71 %
acepta, lo que después fue importante."

---

## 3. Resultados: qué modelo funciona mejor (0:45–1:20)

🟢 **[Natalia]**
"En los dos cupones el mejor modelo fue Random Forest. En cafetería la diferencia es clara:
un F1 de 0.77 frente a 0.70 de los otros modelos. En restaurante obtiene 0.86, pero ojo: como
el 71 % acepta, un modelo que le dijera 'sí' a todos ya sacaría 0.83. Lo difícil ahí es
detectar a quienes van a rechazar, y el modelo solo identifica cerca de 4 de cada 10."

🟡 **[Detalle]**
"El árbol de decisión de restaurante es casi tan bueno como el Random Forest, a solo 0.02 de
F1, y tiene apenas 8 reglas. Si para Ruta Alpes fuera importante tener reglas fáciles de
explicar y de auditar, sería una buena alternativa para ese cupón."

---

## 4. Qué hace que un conductor acepte (1:20–2:00)

🟢 **[Camilo]**
"Lo más interesante es que los dos cupones funcionan muy distinto. En cafetería pesa el
hábito: si la persona ya va a cafeterías, acepta; si nunca va, casi siempre rechaza. También
influyen no tener prisa y la hora, porque la aceptación baja a medida que avanza el día. En
restaurante decide el contexto del viaje: si queda a más de 25 minutos, el conductor lo
rechaza; si queda cerca y el cupón dura un día, lo acepta."

🟡 **[Detalle]**
"Una forma de verlo: un restaurante económico le interesa a casi todo el mundo, entonces la
pregunta no es a quién mostrarlo, sino cuándo. El café, en cambio, depende más de la persona.
Por eso en cafetería el Random Forest le saca más ventaja a los otros modelos: puede aprender
las preferencias de cada conductor."

---

## 5. Balanceo de clases en restaurante (2:00–2:25)

🟢 **[Natalia]**
"Para detectar más rechazos en restaurante probamos SMOTE, que balancea las clases creando
ejemplos sintéticos. En la regresión logística ayudó mucho: pasó de detectar el 38 % de los
rechazos al 64 %. Pero en Random Forest la mejora fue mínima, de 41 % a 44 %, así que no lo
recomendamos para el modelo final."

🟡 **[Detalle]**
"Ninguna técnica de balanceo mejora todo al mismo tiempo: si se detectan más rechazos, se
dejan de mostrar algunos cupones que sí se habrían aceptado. Si a Ruta Alpes le importa más no
molestar al conductor, es mejor ajustar el umbral con el que el modelo decide mostrar el
cupón. Es una decisión de negocio que depende de qué error le cuesta más a la empresa."

---

## 6. Riesgos y recomendación (2:25–3:00)

🟢 **[Camilo o Natalia]**
"Recomendamos usar el modelo en la aplicación para calcular, durante el viaje, la
probabilidad de aceptar cada cupón cercano y mostrar solo el más probable si supera un umbral.
Pero hay que tener cuidado con variables como edad, género o ingreso: el modelo puede tratar
distinto a dos personas solo por su perfil. En cupones el riesgo es bajo, pero en precios
dinámicos podría terminar cobrándole más a ciertos grupos. Por eso recomendamos priorizar el
contexto y los hábitos, y revisar el desempeño por grupos."

🟡 **[Detalle, si sobra tiempo]**
"También hay que tener en cuenta que los datos vienen de una encuesta con respuestas
hipotéticas de unas 565 personas, y que el modelo se evaluó con conductores que ya conocía. Con
usuarios nuevos el desempeño probablemente sería menor, así que conviene reentrenarlo con las
aceptaciones y rechazos reales de la aplicación."

---

## Versión recortada a ~3 minutos (solo bloques 🟢)

1. Intro y problema (0:00–0:20)
2. Cómo lo abordamos (0:20–0:45)
3. Resultados, qué modelo funciona mejor (0:45–1:20)
4. Qué hace que un conductor acepte (1:20–2:00)
5. Balanceo de clases en restaurante (2:00–2:25)
6. Riesgos y recomendación (2:25–3:00)

Total ≈ 394 palabras en los bloques 🟢. A ritmo normal (140–150 palabras/min) eso da cerca
de 3 minutos. Practíquenlo cronometrado: si se pasan, recorten antes que hablar más rápido.

---

## Notas de producción
- Sugerido mostrar en pantalla mientras hablan:
  - (a) la distribución de acepta_cupon por cupón (sección 1.6 del notebook);
  - (b) la gráfica comparativa de los modelos en test (Actividad 7);
  - (c) el árbol de decisión de Restaurante(<20) (sección 4.5), que se entiende muy bien
    para explicar las reglas;
  - (d) la importancia por permutación de las variables (sección 8.1);
  - (e) la gráfica del efecto del balanceo (sección 6.3).
- El video es para Ruta Alpes, así que eviten términos muy técnicos sin explicarlos (por
  ejemplo, "recall" se puede decir como "qué porcentaje de los rechazos detecta").
- No hace falta memorizar el texto: lo importante es cubrir qué modelo recomiendan y por
  qué, qué factores influyen en cada cupón, si conviene o no el balanceo, y los riesgos de
  usar datos demográficos.
