# Semana 1: Mapa de conceptos y caso de uso delimitado

## 1. Mapa de conceptos

IA ⊃ ML ⊃ DL ⊃ IA generativa (casi toda la IA generativa actual usa aprendizaje profundo)

- **Inteligencia artificial (IA):** la gran familia. Incluye tanto reglas escritas a mano como sistemas que aprenden de datos.
  - **Reglas escritas a mano (algoritmo clásico):** una persona escribe la condición ("si la compra supera $100.000, aplica el descuento"). Es predecible, pero solo resuelve lo que alguien previó. Automatizar una condición no la convierte en IA.
  - **Aprendizaje automático (ML):** el sistema encuentra patrones en datos. En el aprendizaje supervisado, cada ejemplo trae la respuesta esperada (por ejemplo, un correo etiquetado como deseado o no deseado). Con pocos datos o poca variedad, aprende atajos y falla con casos nuevos.
    - **Aprendizaje profundo (DL):** ML con redes neuronales de muchas capas. Funciona bien con imágenes, voz y texto, pero necesita muchos datos y sus decisiones son difíciles de explicar.
      - **IA generativa:** produce contenido nuevo (texto, imágenes, código). Puede sonar segura y equivocarse, por eso una persona debe revisar lo importante.

**Cómo se conectan en la práctica:** los sistemas reales combinan reglas (R) para lo predecible, un modelo (M) donde ayuda y una persona (H) que revisa lo dudoso o importante. Usar IA no elimina los algoritmos.

**Conceptos de trabajo con LLMs (Semana I):**
- **Token:** unidad mínima de texto que procesa el modelo (palabra completa, parte de palabra, signo o espacio).
- **Contexto:** toda la información que el modelo "ve" al responder (system prompt, historial, mensaje actual, documentos adjuntos). Tiene un límite de tokens.
- **Temperatura:** controla creatividad frente a precisión. Valores bajos para código y datos; valores altos para brainstorming.
- **Prompt engineering:** zero-shot (pedir sin ejemplos), few-shot (dar ejemplos antes de la tarea) y chain of thought (pedir razonamiento paso a paso).
- **Alucinación:** información plausible pero falsa. Se reduce con contexto específico, RAG, temperatura baja y prompts claros.
- **Otros límites:** sin acceso a internet en tiempo real (salvo con herramientas), corte de conocimiento, sin memoria de conversaciones pasadas (salvo memoria explícita), posibles sesgos y mejor rendimiento en inglés.

## 2. Caso de uso delimitado: Pasaporte del primer asistente

*(Ejemplo guiado por el material de clase; adáptalo con tus propias palabras antes de entregar.)*

- **Usuario:** coders de mi clan.
- **Problema:** dudas repetidas sobre horarios, temas y entregas del entrenamiento.
- **Alcance:** responde solo preguntas sobre horarios, temas y entregas. No cubre notas, decisiones de coach ni temas fuera del entrenamiento.
- **Datos:** únicamente los documentos oficiales que yo le entregue (cronograma, guía de temas, calendario de entregas). No usa información inventada ni de internet.
- **Regla (R):** si la pregunta es sobre una fecha, hora o entrega, buscar esa fecha en el documento oficial. Si no aparece, no responder.
- **Modelo (M):** redacta la respuesta en lenguaje claro a partir del documento encontrado.
- **Humano (H):** el coach revisa cualquier duda sobre evaluación, excepciones o cambios de fecha.
- **Mensaje de límite:** "Solo puedo responder sobre horarios, temas y entregas que estén en los documentos oficiales. Para notas, excepciones o cambios, consulta con tu coach."

## 3. Flujo de consulta (para el boceto)

1. Llega la pregunta del coder.
2. R: ¿es sobre horario, tema o entrega? Si no, aplicar el mensaje de límite.
3. R: buscar la información en los documentos oficiales.
4. M: redactar la respuesta con esa información.
5. H: si la pregunta toca evaluación o excepciones, el coach revisa antes de responder.
6. Mostrar la respuesta junto con el mensaje de límite visible.
