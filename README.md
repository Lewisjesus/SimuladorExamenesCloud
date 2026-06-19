# Cert Lab · Ing. Lewis Reinoso

Simulador web de exámenes para certificaciones de **AWS**, **Microsoft Azure** y **Google Cloud Platform**. Inspirado en el simulador de Julián Rodríguez, pero con identidad propia, soporte multi-proveedor y carga de bancos de preguntas en JSON.

## Características

- **9 certificaciones precargadas** con preguntas de ejemplo:
  - AWS: CLF-C02, SAA-C03, AIF-C01, DVA-C02
  - Azure: AZ-900, AZ-104, AI-900
  - GCP: Cloud Digital Leader, Associate Cloud Engineer
- **Dos modos**:
  - **Estudio**: feedback inmediato + explicación tras cada respuesta.
  - **Simulacro**: sin ayudas, con cronómetro, resultados al final.
- **Carga JSON personalizada**: agrega tus propios bancos sin tocar el código.
- **Diseño propio** (tema oscuro, tipografía Space Grotesk + Inter + JetBrains Mono).
- **100% estático**: un único archivo HTML, listo para GitHub Pages.
- **Mobile friendly** y respeta `prefers-reduced-motion`.

---

## Cómo desplegar en GitHub Pages

1. Crea un repositorio en tu cuenta, por ejemplo `SimuladorExamenCloud`.
2. Sube el archivo `index.html` a la raíz del repositorio.
3. En GitHub, ve a **Settings → Pages**.
4. En **Source**, selecciona la rama (`main`) y la carpeta raíz (`/root`).
5. Guarda. En ~1 minuto tu sitio estará disponible en:

   ```
   https://TU-USUARIO.github.io/SimuladorExamenCloud/
   ```

Si quieres una URL más bonita, crea el repo con el nombre `tu-usuario.github.io` y se publicará en `https://tu-usuario.github.io/`.

---

## Formato del archivo JSON

El simulador acepta varios formatos para máxima compatibilidad. El más simple:

```json
{
  "title": "Mi banco de preguntas AWS SAA-C03",
  "questions": [
    {
      "q": "¿Qué servicio usarías para almacenar objetos con alta durabilidad?",
      "options": [
        "Amazon EBS",
        "Amazon S3",
        "Amazon EFS",
        "Amazon RDS"
      ],
      "a": [1],
      "e": "Amazon S3 ofrece durabilidad de 11 nueves (99.999999999%)."
    }
  ]
}
```

### Campos aceptados (varios alias)

| Campo                 | Alias aceptados                                       | Descripción                                                       |
| --------------------- | ----------------------------------------------------- | ----------------------------------------------------------------- |
| `q`                   | `question`, `pregunta`, `text`                        | Enunciado de la pregunta.                                         |
| `options`             | `opciones`, `choices`, `respuestas`                   | Array de opciones (strings).                                      |
| `a`                   | `answer`, `correct`, `correcta`                       | Índice(s) de la respuesta correcta (0-based) o letras `"A"`, `"B"`. |
| `e`                   | `explanation`, `explicacion`, `feedback`              | Explicación opcional que se muestra en modo estudio.              |

### Múltiple respuesta

Si una pregunta tiene varias respuestas correctas, pasa un array:

```json
{
  "q": "¿Qué pilares forman parte del AWS Well-Architected Framework? (Elige 2)",
  "options": ["Operational Excellence", "Marketing Optimization", "Security", "Brand Awareness"],
  "a": [0, 2],
  "e": "Los pilares oficiales incluyen Operational Excellence y Security, entre otros."
}
```

### También acepta un array directo

```json
[
  { "q": "...", "options": ["A", "B"], "a": [0], "e": "..." },
  { "q": "...", "options": ["A", "B"], "a": [1], "e": "..." }
]
```

---

## Cómo personalizar la marca

Abre `index.html` y busca estas líneas (al inicio del CSS y HTML):

- Color principal: variable `--accent` (línea ~15, valor `#00D4FF`).
- Nombre: busca `Ing. Lewis Reinoso` y reemplázalo.
- Iniciales del logo: busca `<div class="brand-mark">LR</div>` y cámbialo.
- Título de pestaña: `<title>...</title>`.

---

## Cómo agregar más certificaciones precargadas

En el bloque `CERTIFICATIONS` (cerca del final del archivo, dentro del `<script>`) añade entradas como:

```javascript
'mi-cert-id': {
  provider: 'aws', // 'aws' | 'azure' | 'gcp'
  code: 'XYZ-C01',
  name: 'Mi Nueva Certificación',
  level: 'associate', // 'foundational' | 'associate' | 'professional' | 'specialty'
  desc: 'Descripción corta para la tarjeta.',
},
```

Y en `QUESTION_BANKS` añade las preguntas:

```javascript
'mi-cert-id': [
  { q: '...', options: ['A','B','C','D'], a: [0], e: '...' },
  ...
],
```

---

## Aviso

Las preguntas incluidas son originales y de ejemplo educativo. Este simulador **no reproduce exámenes oficiales** ni "dumps". Úsalo como apoyo para practicar conceptos, no como sustituto de la preparación oficial (AWS Skill Builder, Microsoft Learn, Google Cloud Skills Boost).

---

**Hecho con cuidado por Ing. Lewis Reinoso · Material de estudio gratuito.**
