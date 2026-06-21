# Cert Lab · Ing. Lewis Reinoso — v2.0

Simulador web de certificaciones cloud (AWS, Azure y Google Cloud) en español, con cronómetro regresivo y banco propio de 450 preguntas originales.

## ✨ Novedades v2.0

- 🎨 **Tema claro** — fondo blanco, paleta profesional.
- ⏱️ **Cronómetro regresivo de 1h 30m** — empieza en `1:30:00` y va bajando hasta `0:00:00`.
- 🛑 **Auto-finalización** — cuando el cronómetro llega a `0`, el simulacro termina solo y muestra resultados.
- 📚 **450 preguntas originales** — 50 por cada una de las 9 certificaciones, en español, con explicaciones.
- 🟡 **Avisos visuales** — el cronómetro se pone amarillo al quedar < 10 min y rojo (parpadeo) al quedar < 1 min.

## 🚀 Despliegue en GitHub Pages

1. Sube **todos los archivos** (incluyendo la carpeta `data/`) al repo `Lewisjesus/SimuladorExamenesCloud`.
2. En `Settings → Pages`, branch `main`, folder `/(root)` → Save.
3. URL: `https://lewisjesus.github.io/SimuladorExamenesCloud/`

> ⚠️ **Importante:** debes subir la carpeta `data/` con sus 9 archivos JSON, sino el sitio cargará vacío.

## 📁 Estructura de archivos

```
SimuladorExamenesCloud/
├── index.html                  (UI, estilos, lógica — sin preguntas adentro)
├── README.md
└── data/
    ├── aws-clf-c02.json        (50 preguntas — Cloud Practitioner)
    ├── aws-saa-c03.json        (50 preguntas — Solutions Architect Associate)
    ├── aws-aif-c01.json        (50 preguntas — AI Practitioner)
    ├── aws-dva-c02.json        (50 preguntas — Developer Associate)
    ├── azure-az-900.json       (50 preguntas — Azure Fundamentals)
    ├── azure-az-104.json       (50 preguntas — Azure Administrator)
    ├── azure-ai-900.json       (50 preguntas — Azure AI Fundamentals)
    ├── gcp-cdl.json            (50 preguntas — Cloud Digital Leader)
    └── gcp-ace.json            (50 preguntas — Associate Cloud Engineer)
```

## 🎯 Certificaciones incluidas

| Proveedor | Código   | Nombre                                    | Nivel        | Preguntas |
|-----------|----------|-------------------------------------------|--------------|-----------|
| AWS       | CLF-C02  | Cloud Practitioner                        | Foundational | 50        |
| AWS       | SAA-C03  | Solutions Architect Associate             | Associate    | 50        |
| AWS       | AIF-C01  | AI Practitioner                           | Foundational | 50        |
| AWS       | DVA-C02  | Developer Associate                       | Associate    | 50        |
| Azure     | AZ-900   | Azure Fundamentals                        | Foundational | 50        |
| Azure     | AZ-104   | Azure Administrator                       | Associate    | 50        |
| Azure     | AI-900   | Azure AI Fundamentals                     | Foundational | 50        |
| GCP       | CDL      | Cloud Digital Leader                      | Foundational | 50        |
| GCP       | ACE      | Associate Cloud Engineer                  | Associate    | 50        |
| **TOTAL** |          |                                           |              | **450**   |

## 📝 Formato de banco propio (.json)

Si quieres cargar tu propio banco con el botón "Cargar banco propio":

```json
{
  "title": "Mi banco custom",
  "questions": [
    {
      "q": "¿Pregunta aquí?",
      "options": ["Opción A", "Opción B", "Opción C", "Opción D"],
      "a": [0],
      "e": "Explicación de la respuesta correcta."
    }
  ]
}
```

- `a` acepta índices base-0 (0=A, 1=B, 2=C, 3=D) o letras ("A", "B", etc.).
- Para múltiple respuesta, usa array: `"a": [0, 2]`.
- Acepta sinónimos: `question`/`pregunta`, `opciones`/`choices`, `correct`/`correcta`, `explanation`/`explicacion`.

## 💡 Cómo agregar más preguntas

Para añadir, por ejemplo, preguntas a `aws-clf-c02.json`, simplemente edita el archivo en GitHub y agrega más objetos al array `questions`. El sitio se actualiza automáticamente en 1-2 minutos.

---

Hecho con cuidado por **Ing. Lewis Reinoso**.
