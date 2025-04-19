# **¿Qué comemos hoy?**

## **Resumen**

Este proyecto desarrolla un **Proof of Concept (POC)** para una herramienta que genera recetas personalizadas e imágenes ilustrativas a partir de ingredientes disponibles en casa. Utiliza la API de **TheMealDB** para generar recetas (modelo texto-texto) y la API de **Hugging Face** con **Stable Diffusion XL** para crear imágenes hiperrealistas (modelo texto-imagen). Implementado en **Google Colab**, el proyecto emplea técnicas de **Fast Prompting** para optimizar resultados, es completamente gratuito, y se entrega en un repositorio público de **GitHub** con un notebook funcional. La solución aborda la problemática de la planificación de comidas, promoviendo la sostenibilidad y la economía doméstica.

## **Enlace al Notebook**

**Ejecutar en Google Colab**\
https://colab.research.google.com/drive/1udYiKEZKMw0kWHqwIR5xUgck5J2vNxCi?usp=sharing.

## **Contenido**

- `Quécomemoshoy.ipynb`: Notebook de Jupyter con el código funcional que genera recetas e imágenes.
- `README.md`: Este archivo, con la descripción del proyecto y las instrucciones.

## **Descripción del Proyecto**

### **Nombre del proyecto**

**¿Qué comemos hoy?**

### **Presentación del problema**

Cada día, millones de personas se enfrentan a la pregunta: **"¿Qué comemos hoy?"**. Al revisar la heladera, encuentran ingredientes que parecen no combinar, lo que lleva a desperdiciar comida, tiempo y dinero. Además, la falta de ideas fomenta la repetición de comidas o compras innecesarias. Este problema es relevante porque afecta la **economía doméstica** y la **sostenibilidad**, y una solución tecnológica podría transformar esta experiencia cotidiana en algo creativo, eficiente y accesible.

### **Desarrollo de la propuesta de solución**

La solución utiliza dos modelos de **IA**:

- **Generación de recetas (texto-texto)**: A través de la API de **TheMealDB**, se buscan recetas basadas en un ingrediente principal ingresado por el usuario (ej. "pollo"). La respuesta se traduce al español para mayor accesibilidad.
- **Generación de imágenes (texto-imagen)**: Usando **Stable Diffusion XL** de **Hugging Face**, se crea una imagen realista del plato propuesto (ej. "pollo con espinaca y queso gratinado").
- Los **prompts** se diseñaron con técnicas de **Fast Prompting** para minimizar consultas a las APIs (una por receta, una por imagen), optimizando recursos y cumpliendo con los límites gratuitos.

### **Justificación de la viabilidad**

El proyecto es viable porque:

- **Técnica**: Usa APIs gratuitas (**TheMealDB** y **Hugging Face**), accesibles sin costo y con documentación clara. No requiere infraestructura propia.
- **Tiempo**: El **POC** se desarrolló en pocos días usando **Google Colab**, demostrando que una implementación básica es rápida.
- **Recursos**: Solo se necesita un navegador, una cuenta en **Hugging Face** para el token, y **GitHub** para el repositorio. Los límites de las APIs gratuitas (100-200 solicitudes/día en **Hugging Face**) son suficientes para pruebas.
- **Limitaciones**: **TheMealDB** no genera recetas nuevas ni siempre coincide con todos los ingredientes ingresados, pero esto se compensa con la imagen personalizada de **Stable Diffusion**.

## **Objetivos**

- Demostrar que la **IA** puede sugerir recetas útiles a partir de ingredientes disponibles.
- Generar imágenes ilustrativas que complementen las recetas.
- Optimizar el uso de APIs gratuitas, limitando las consultas a dos por ejecución.
- Crear un **POC** funcional y replicable en **Google Colab**.
- Documentar el proceso en un repositorio de **GitHub**.

## **Metodología**

- **Identificación del problema**: Analizar las dificultades para encontrar recetas y visualizar platos.
- **Selección de herramientas**: Elegir **TheMealDB** (texto-texto) y **Hugging Face** (texto-imagen) por su gratuidad y robustez.
- **Diseño de prompts**: Usar **Fast Prompting** para crear prompts específicos (ej. incluir "hiperrealista", "8K" en el prompt de imagen).
- **Implementación**: Desarrollar un notebook en **Colab** que integre ambas APIs.
- **Pruebas y optimización**: Iterar sobre los prompts y el código, probando combinaciones como "carne, papa, cebolla" para validar la flexibilidad.
- **Documentación**: Crear un repositorio en **GitHub** con el notebook, prompts, y resultados.

**Justificación**: Este enfoque modular simplifica el desarrollo y reduce consultas innecesarias, alineándose con la consigna de optimización.

## **Herramientas y Tecnologías**

- **Google Colab**: Plataforma gratuita para ejecutar el código en la nube.
- **TheMealDB API**: Fuente gratuita de recetas estructuradas (texto-texto).
- **Hugging Face Stable Diffusion**: API gratuita con el modelo **stabilityai/stable-diffusion-xl-base-1.0** (texto-imagen).
- **Fast Prompting**: Técnica para optimizar prompts, usando descripciones específicas (ej. "iluminación suave", "fondo de cocina moderna") y parámetros como `negative_prompt`.
- **Python**: Lenguaje usado con bibliotecas como `requests` y `IPython.display`.

**Justificación**: Estas herramientas son gratuitas, fáciles de usar, y adecuadas para un **POC** académico. **Fast Prompting** maximiza la calidad sin requerir recursos adicionales.

## **Instrucciones**

1. Abre el notebook `Quécomemoshoy.ipynb` en **Google Colab** usando el enlace proporcionado.
2. Asegúrate de tener un token válido de **Hugging Face** (incluido en el código: `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`, pero verifica su validez).
3. Instala las dependencias (`requests`, `IPython`) ejecutando `!pip install requests IPython` en Colab.
4. Ejecuta las celdas en orden para:
   - Generar una receta basada en una lista de ingredientes (ej. `["pollo", "espinaca", "queso"]`).
   - Crear una imagen hiperrealista del plato (ej. "pollo con espinaca y queso gratinado").

## **Ejemplo de Uso**

El código toma una lista de ingredientes (ej. `["pollo", "espinaca", "queso"]`) y:

- Genera una receta detallada (título, ingredientes, pasos) usando **TheMealDB**, traducida al español.
- Crea una imagen hiperrealista del plato con un prompt optimizado:\
  **"Imagen hiperrealista de {nombre_plato}, servido en un plato blanco, con iluminación suave, fondo de cocina moderna, 8K, altamente detallado"**.

**Ejemplo de código**:

```python
ingredientes = ["pollo", "espinaca", "queso"]
print("Generando receta...")
receta = buscar_receta(ingredientes)
print(receta)
print("\nGenerando imagen...")
generar_imagen("pollo con espinaca y queso gratinado")
```

## **Prompts Utilizados**

- **Texto-texto (TheMealDB)**: La lista de ingredientes (ej. `["pollo", "espinaca", "queso"]`) se traduce al inglés ("chicken" para "pollo") y se envía a la API. No se usa un prompt explícito, pero la entrada es optimizada para coincidir con los términos de la API.
- **Texto-imagen (Hugging Face)**:\
  **"Imagen hiperrealista de {nombre_plato}, servido en un plato blanco, con iluminación suave, fondo de cocina moderna, 8K, altamente detallado"**, con parámetros:
  - `negative_prompt`: **"borroso, baja calidad, distorsionado, caricatura"**
  - `num_inference_steps`: **50**
  - `guidance_scale`: **7.5**

**Optimización con Fast Prompting**:

- **Especificidad**: Detalles como "hiperrealista", "8K", y "fondo de cocina moderna" guían al modelo hacia resultados realistas.
- **Negativos**: El `negative_prompt` evita resultados no deseados.
- **Parámetros**: Los valores de `num_inference_steps` y `guidance_scale` aumentan la calidad.

## **Resultados**

- **Recetas**: La función `buscar_receta` genera recetas detalladas basadas en el ingrediente principal (ej. "Chicken Alfredo" para `["pollo", "espinaca", "queso"]`), traducidas al español para mayor accesibilidad.
- **Imágenes**: La función `generar_imagen` produce imágenes hiperrealistas, cumpliendo con el requisito de visualización atractiva.
- **Cumplimiento de objetivos**: La solución es gratuita, accesible en **Colab**, y usa prompts optimizados, resolviendo la problemática de planificación de comidas.
- **Limitaciones**: **TheMealDB** solo usa el primer ingrediente, lo que limita la personalización. Las imágenes dependen de los límites gratuitos de **Hugging Face** (100-200 solicitudes/día).

## **Conclusiones**

El proyecto logró demostrar que la **IA** puede facilitar la cocina diaria al generar recetas e imágenes realistas de forma gratuita. La optimización con **Fast Prompting** mejoró la calidad de las imágenes, y el uso de **Google Colab** aseguró accesibilidad. Los cambios realizados (documentados en `informe.md`) corrigieron errores y optimizaron el rendimiento, alineándose con la consigna. En el futuro, se podría integrar traducción automática más robusta o usar APIs como **Flux.1** para imágenes aún más realistas.

## **Referencias**

- **TheMealDB API**: www.themealdb.com
- **Hugging Face API**: huggingface.co
- **Documentación de Stable Diffusion XL**: huggingface.co/stabilityai/stable-diffusion-xl-base-1.0
- **Fast Prompting**: Técnicas vistas en el curso para optimizar prompts de IA.

## **Notas**

- El proyecto es **gratuito**, cumpliendo con la consigna de usar herramientas accesibles.
- Los **prompts** están optimizados para minimizar consultas a las APIs (una por receta, una por imagen).
- Consulta `informe.md` para una explicación completa de la **problemática**, **solución**, y **cambios realizados** en el código.
