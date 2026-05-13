<style>
  /* ── Reset & base ── */
  body {
    font-family: 'Georgia', serif;
    max-width: 860px;
    margin: auto;
    color: #2c3e50;
    line-height: 1.75;
  }

  /* ── Header block ── */
  .blog-header {
    text-align: center;
    padding: 2.5rem 1.5rem 2rem;
    background: #f8fbff;
    border: 1px solid #d0e8ff;
    border-radius: 10px;
    margin-bottom: 2.5rem;
  }
  .blog-header h1 {
    font-size: 2rem;
    font-weight: 700;
    color: #1a2e4a;
    border: none;
    margin: 0 0 4px;
    padding: 0;
  }
  .blog-header h2 {
    font-size: 1.1rem;
    font-weight: 400;
    color: #5a7a9a;
    border: none;
    margin: 0 0 12px;
    padding: 0;
  }
  .blog-header .semester {
    display: inline-block;
    background: #3498db;
    color: white;
    font-size: 0.8rem;
    font-family: 'Segoe UI', sans-serif;
    padding: 4px 14px;
    border-radius: 20px;
    margin-bottom: 1.5rem;
    letter-spacing: 0.04em;
  }

  /* ── Author table ── */
  .blog-header table {
    margin: 0 auto;
    width: auto;
    min-width: 420px;
    border-collapse: collapse;
    font-family: 'Segoe UI', sans-serif;
    font-size: 0.88rem;
  }
  .blog-header th {
    background: #3498db;
    color: white;
    padding: 8px 16px;
    font-weight: 500;
    letter-spacing: 0.03em;
  }
  .blog-header td {
    padding: 7px 16px;
    border-bottom: 1px solid #e0edf8;
    color: #2c3e50;
  }
  .blog-header tr:last-child td { border-bottom: none; }

  /* ── Post headings ── */
  h1 {
    font-size: 1.9rem;
    color: #1a2e4a;
    border-bottom: 3px solid #3498db;
    padding-bottom: 8px;
    margin-top: 2rem;
  }
  h2 {
    font-size: 1.4rem;
    color: #185a8a;
    border-bottom: 1.5px solid #b8d9f5;
    padding-bottom: 6px;
    margin-top: 0.4rem;
  }
  h3 {
    font-size: 1.05rem;
    font-family: 'Segoe UI', sans-serif;
    font-weight: 600;
    color: #1a2e4a;
    margin-top: 2rem;
    padding-left: 10px;
    border-left: 3px solid #3498db;
  }

  /* ── h4 subheading ── */
  h4 {
    font-size: 0.95rem;
    font-family: 'Segoe UI', sans-serif;
    font-weight: 600;
    color: #185a8a;
    margin-top: 1.5rem;
    padding-left: 10px;
    border-left: 2px solid #b8d9f5;
  }

  /* ── Blockquote ── */
  blockquote {
    background: #f0f7ff;
    border-left: 4px solid #3498db;
    border-radius: 0 6px 6px 0;
    padding: 10px 18px;
    margin: 14px 0;
    color: #1a5080;
    font-style: italic;
  }

  /* ── Divider ── */
  hr {
    border: none;
    border-top: 1px solid #d0e8ff;
    margin: 2rem 0;
  }

  /* ── Body text ── */
  p { margin: 0.7rem 0; }
</style>

<div class="blog-header">
  <h1>Seminar Blog</h1>
  <h2>Recent Applications of Machine Learning</h2>
  <div class="semester">Summer Semester 2026</div>
  <table>
    <thead>
      <tr>
        <th align="left">Name</th>
        <th align="center">Student ID</th>
        <th align="left">Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Aran Moradi</td>
        <td align="center">xxx</td>
        <td>xxx</td>
      </tr>
      <tr>
        <td>Qianyu Bu</td>
        <td align="center">3730364</td>
        <td>st188433@stud.uni-stuttgart.de</td>
      </tr>
    </tbody>
  </table>
</div>

---

# Blog Post 1
## SegLLM: Multi-round Reasoning Segmentation

---

### 1. Background and Problem

Current LLM or detection models are unable to handle multi-round interactive conversations.

For example, when a user requests a segmentation task such as:

> "Highlight the man with the white hoodie."

most existing models cannot process follow-up queries based on the previously generated mask output, such as:

> "Mask the bike behind the man from the previous prompt."

This limitation makes interactive segmentation difficult in real-world conversational scenarios.

---

### 2. Method

Unlike other state-of-the-art approaches, SegLLM feeds previous segmentation outputs from the mask decoder back into the LLM.

At the same time, the conversation context is integrated into the query input of the mask decoder. This enables the model to maintain contextual understanding across multiple interaction rounds.

#### 2.1 Model Structure

First, there is an image encoder such as CLIP or DINOv2. The encoder transforms the input image into patch representations, which are then converted into embeddings.

Second, a large language model (LLM), such as Llama, is used to process the input text, combine it with the visual information, and generate an output sequence. Importantly, the model is trained to produce a special token [SEG] when a segmentation output is required.

The third component is the projection layer, which aligns the image embeddings with the text embedding space. This allows the LLM to process both modalities jointly.

When the LLM generates the [SEG] token in its output, this token acts as a trigger for a segmentation module. A separate mask decoder then uses the internal visual features to generate the final segmentation mask.

---

### 3. Experiment

#### 3.1 Data Set

#### 3.2 Pipeline

#### 3.3 Traning

---

### 4. Results
