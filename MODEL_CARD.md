# Model Card: Autoencoder (AE) y Variational Autoencoder (VAE)

## 1. Modelos y versiones

- **Autoencoder (AE):** Modelo determinista para compresión y reconstrucción de imágenes.
- **Variational Autoencoder (VAE):** Modelo generativo probabilístico con regularización mediante divergencia KL.
- **Framework:** TensorFlow / Keras.
- **Entorno:** Python 3.12.

## 2. Uso previsto

**Propósito:** Demostración educativa de las representaciones latentes, la reconstrucción de imágenes y la generación de muestras sintéticas.

**Usuarios:** Estudiantes de ciencia de datos, investigadores y desarrolladores interesados en comparar modelos AE y VAE.

### Usos fuera de alcance

- Generación de imágenes fotorrealistas o de alta resolución para producción comercial.
- Creación de diseños de moda definitivos para manufactura.
- Aplicaciones que requieren precisión estricta a nivel de píxel.

## 3. Dataset y licencia

- **Dataset:** Fashion-MNIST.
- **Características:** Imágenes en escala de grises de 28 × 28 píxeles.
- **Entrenamiento:** 60,000 imágenes.
- **Prueba:** 10,000 imágenes.
- **Preprocesamiento:** Normalización de píxeles al rango `[0, 1]`.
- **Licencia:** MIT.

## 4. Arquitectura y espacio latente

- **AE:** Codifica cada imagen en un vector latente de dimensiones fijas y utiliza un decodificador para reconstruirla. El espacio latente no está necesariamente organizado para generar nuevas muestras.
- **VAE:** Aprende una distribución probabilística representada mediante una media y una varianza. Utiliza el truco de reparametrización y la divergencia KL para regularizar el espacio latente y facilitar la generación e interpolación de imágenes.

## 5. Métricas y resultados

| Modelo | Entrenamiento | Métrica reportada |
|---|---:|---|
| AE | 6 épocas | Loss de validación: `0.3071` |
| VAE | 8 épocas | Divergencia KL: `6.2620` |
| VAE | 8 épocas | Pérdida de reconstrucción: `267.3499` |

Las métricas del AE y del VAE no son directamente comparables sin considerar sus funciones de pérdida y escalas. Los valores obtenidos deben interpretarse junto con las reconstrucciones y las muestras generadas.

## 6. Diversidad y vecinos cercanos

- **Diversidad:** El VAE generó muestras de distintas categorías de Fashion-MNIST al muestrear diferentes puntos del espacio latente.
- **Similitud:** Las muestras sintéticas pueden compartir características y siluetas con imágenes del conjunto de entrenamiento.
- **Originalidad:** La generación de nuevas muestras no garantiza originalidad absoluta ni ausencia de similitudes con los datos originales.

## 7. Hardware y costo computacional

- **Sistema operativo:** Windows 11.
- **Hardware de entrenamiento:** CPU.
- **Optimización:** oneDNN activada.
- **Tiempo de entrenamiento AE:** aproximadamente 6.1 segundos para 6 épocas.
- **Tiempo de entrenamiento VAE:** aproximadamente 11.2 segundos para 8 épocas.
- **Parámetros del AE:** 25,888.
- **Parámetros del decodificador del VAE:** 101,520.

Los tiempos corresponden a ejecuciones locales y pueden variar según el hardware, las versiones de las bibliotecas y las condiciones de ejecución.

## 8. Limitaciones y riesgos

- **Borrosidad:** Las reconstrucciones del VAE pueden presentar bordes difusos debido a la función de pérdida y a la naturaleza probabilística del modelo.
- **Sesgos:** El modelo puede reproducir las distribuciones y los sesgos presentes en Fashion-MNIST.
- **Generalización:** El rendimiento está limitado a las características del conjunto de datos utilizado.
- **Colapso modal:** La diversidad observada es una señal favorable, pero no basta por sí sola para descartar completamente el colapso modal.
- **Uso responsable:** Las imágenes sintéticas deben identificarse como generadas artificialmente y no presentarse como fotografías de artículos reales.

## 9. Supervisión y recomendaciones

Se recomienda inspeccionar visualmente las reconstrucciones, las interpolaciones y las muestras generadas, además de revisar las métricas de entrenamiento y validación.

Para aplicaciones reales, es necesario evaluar la calidad, la diversidad, los sesgos y las posibles similitudes con los datos de entrenamiento antes de utilizar las imágenes sintéticas.

## 10. Conclusión

El AE permite estudiar la compresión y reconstrucción determinista de imágenes, mientras que el VAE incorpora un espacio latente probabilístico que facilita la generación de nuevas muestras y las interpolaciones.

Los resultados obtenidos permiten comparar ambos enfoques en un contexto educativo, considerando sus diferencias arquitectónicas, su costo computacional y sus limitaciones visuales.
