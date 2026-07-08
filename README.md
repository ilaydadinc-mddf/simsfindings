# simsfindings
MDDF SS26 Comp-Sci Final Assignment by Ilayda Dinc, taught by Prof. Moritz Schwind, supervised by Christopher Kopic

## 📂 Corpus Statement

### Collection Identity
[The Sims 4 - Gameplay Collection]

### Intent & Selection
This specific collection was intentionally selected to challenge a joint text-image embedding model's capacity to distinguish subtle compositional changes, weather types and landscapes, human or animal figures, color dominations without relying on explicit metadata tags or generated descriptive captions. Each image is a 3D render of own creations.

### Curation Process
The 87 individual assets were systematically compiled, deduplicated, and unified into standardized high-resolution formats. The visual distribution was strictly audited to maintain balanced variation across colors, lighting, and structural configurations, tricky similarities (i.e. moon vs. white circle objects, animals vs. curved nude tone objects) providing a rigorous environment for testing retrieval boundaries.

---

# Level 1 Showcase: Semantic Image Search Engine

A joint text–image embedding model search platform built over a custom archive. This system maps text queries and images into a shared vector space, utilizing strict cosine similarity matrices for high-speed, pure retrieval with zero generation dependencies.

---

## 🛠️ System Architecture

* **Framework Backbone:** Native OpenAI CLIP (`clip-vit-base-patch32`) implemented via Hugging Face Transformers.
* **Vector Execution:** Vectorized on T4 hardware using tensor dot-product matching.
* **Interface Matrix:** Real-time sandboxed Gradio panel.
* **Persistence Layer:** Fast-loading JSON tensor cache map optimized for seamless Level 2 portability.

---

## 🗺️ Retrieval Atlas (10-Query Diagnostic Evaluation)

### 🟢 Target Successes

#### 1. Query: "a cat"
* **Result Metrics:** Top-1 Hit Score: `0.270`
* **Embedding-Space Analysis:** CLIP successfully recognized the top 3 cat images in the curation. It included a dog render with a ranking of 0.233 on the 4th place. The dog image was expected as an error. The 5th place was an unexpected image of a guitar, that resembled the shape of a cat.
#### 2. Query: [Insert Query 2]
* **Result Metrics:** Top-1 Hit Score: `0.289`
* **Embedding-Space Analysis:** [Explain briefly why the model matched this query to the specific visual elements of the image].

*... [Repeat this structure for your 7 successful queries] ...*

### 🔴 System Failures

#### 8. Query: [Insert Counting/Spatial Constraint Query, e.g., "Exactly three red elements"]
* **Result Metrics:** Returned asset with multiple objects or a single large object. Score: `0.241`
* **Embedding-Space Analysis:** A known limitation of CLIP-based architectures is the struggle with exact counting and complex compositionality. The text encoder heavily weights individual tokens like "red", shifting the query vector toward any cluster matching that color profile while disregarding the numerical constraint.

*... [Repeat this structure for your 3 failure queries] ...*
