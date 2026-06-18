# TRANSFERENCIA DE ESTILO EN IMÁGENES USANDO VGG 19 

## Resumen

Este proyecto aborda el problema de Neural Style Transfer (NST), cuyo objetivo es combinar el contenido visual de una imagen con el estilo artístico de otra. 
Para ello, se implementa un sistema basado en VGG19 capaz de extraer representaciones de contenido y estilo a partir de características profundas.
Se realizan tres experimentos principales, en primer lugar, se compara el desempeño de una red VGG19 ajustada mediante fine-tuning sobre estilos 
artísticos con respecto a una VGG19 preentrenada convencional. En segundo lugar, se evalúan dos representaciones estadísticas del estilo, utilizando matrices de Gram
y matrices de covarianza para modelar las relaciones entre los mapas de características extraídos por la red. Finalmente, se explora la transferencia de múltiples estilos con el fin de analizar
la capacidad de generalización del modelo seleccionado. Los resultados son evaluados mediante métricas objetivas como SSIM y LPIPS, permitiendo cuantificar la preservación del contenido y la 
similitud perceptual de las imágenes generadas.

## Características

- Clasificador optimizado al estilo VGG19
- Implementación de transferencia de estilo neuronal (NSFT)
- Representación al estilo de la matriz de Gram
- Representación al estilo de la matriz de covarianza
- Evaluación SSIM
- Evaluación LPIPS
- Implementación en PyTorch

## Conjunto de datos

El clasificador se entrenó con un subconjunto de imágenes de WikiArt, seleccionando cuatro estilos artísticos:

- Impresionismo
- Cubismo
- Realismo
- Postimpresionismo

Las imágenes se redimensionaron a 224×224 píxeles y se normalizaron utilizando las estadísticas de ImageNet.

Base de datos reducida disponible en: https://www.kaggle.com/datasets/alejandropetit/wikiart-small?select=Art_Nouveau_Modern


## Architecture

Se presenta la estructura general empleada.

<img width="251" height="361" alt="image" src="https://github.com/user-attachments/assets/516d247b-e5a8-49ba-b621-753c352b2957" />


## Metodología

Primeramente se parte del diseño de un clasificador de estilos (4), y posteriormente el NST.

Dataset WikiArt
       │
       ▼
 Fine-Tuning VGG19
       │
       ▼
 Extracción de características
       │
       ├── Contenido (activaciones profundas)
       │
       └── Estilo (Gram / Covarianza)
                    │
                    ▼
        Neural Style Transfer
                    │
                    ▼
         Optimización iterativa
                    │
                    ▼
          Imagen estilizada
                    │
                    ▼
          SSIM y LPIPS
                    │
                    ▼
      Transferencia multiestilo

## Métricas

Se presentan métricas globales como:

Accuracy: 81%

F1-score por estilo:
• Impressionism: 0.90
• Cubism: 0.85
• Art Nouveau/Modern: 0.80
• Expressionism: 0.71

Al igual que la matriz de confusión del clasificador de los 4 estilos.

En cuanto al modelo completo, se emplea SSIM, LPIPS y distancia de estilo para evaluar la tarea de transferencia de estilo.


