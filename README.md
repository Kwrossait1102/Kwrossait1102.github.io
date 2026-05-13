<style>
  @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=IBM+Plex+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&display=swap');

  body {
    font-family: 'IBM Plex Sans', sans-serif;
    max-width: 780px;
    margin: 0 auto;
    padding: 2.5rem 1.5rem;
    color: #24292e;
    line-height: 1.8;
    font-size: 14.5px;
    background: #fff;
  }

  /* ── Top meta ── */
  .blog-meta { margin-bottom: 2.5rem; }
  .blog-meta .eyebrow {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: #8b949e;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }
  .blog-meta .eyebrow span { color: #57606a; }
  .blog-meta h1 {
    font-size: 28px;
    font-weight: 600;
    color: #24292e;
    border: none;
    margin: 0 0 4px;
    padding: 0;
    line-height: 1.2;
  }
  .blog-meta h2 {
    font-size: 17px;
    font-weight: 300;
    color: #57606a;
    border: none;
    margin: 0 0 1.5rem;
    padding: 0;
  }
  .blog-meta .authors {
    display: flex;
    gap: 2.5rem;
    flex-wrap: wrap;
    padding-bottom: 2rem;
    border-bottom: 0.5px solid #d0d7de;
  }
  .blog-meta .author { display: flex; flex-direction: column; gap: 3px; }
  .blog-meta .author .name { font-size: 13px; font-weight: 500; color: #24292e; }
  .blog-meta .author .sid {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: #8b949e;
  }
  .blog-meta .author .email {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: #57606a;
  }

  /* ── Section headings ── */
  h1 {
    font-size: 22px; font-weight: 600; color: #24292e;
    border-bottom: 0.5px solid #d0d7de;
    padding-bottom: 8px; margin-top: 3rem;
  }
  h2 {
    font-size: 16px; font-weight: 600; color: #24292e;
    border-bottom: 0.5px solid #eaecef;
    padding-bottom: 5px; margin-top: 0.3rem;
  }
  h3 {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    font-weight: 500;
    color: #8b949e;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-top: 2.8rem;
    margin-bottom: 0.8rem;
    border: none;
    padding: 0;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  h3::after {
    content: '';
    flex: 1;
    height: 0.5px;
    background: #d0d7de;
    display: inline-block;
  }
  h4 {
    font-size: 14px;
    font-weight: 600;
    color: #24292e;
    margin-top: 1.8rem;
    margin-bottom: 0.4rem;
    border: none;
    padding: 0;
  }

  /* ── Body ── */
  p { margin: 0.7rem 0; color: #57606a; }

  /* ── Blockquote ── */
  blockquote {
    margin: 1.2rem 0;
    padding: 12px 16px;
    background: #f6f8fa;
    border-left: 2px solid #d0d7de;
    border-radius: 0;
    font-style: italic;
    color: #57606a;
    font-size: 14px;
  }

  /* ── Inline code ── */
  code {
    font-family: 'IBM Plex Mono', monospace;
    background: #f6f8fa;
    padding: 2px 6px;
    border-radius: 3px;
    font-size: 12.5px;
    color: #B07D48;
    border: 0.5px solid #d0d7de;
  }

  /* ── HR ── */
  hr {
    border: none;
    border-top: 0.5px solid #d0d7de;
    margin: 2rem 0;
  }
</style>

<div class="blog-meta">
  <div class="eyebrow">Seminar Blog &nbsp;/&nbsp; <span>Recent Applications of Machine Learning</span> &nbsp;/&nbsp; Summer Semester 2026</div>
  <h1>Blog Post 1</h1>
  <h2>SegLLM: Multi-round Reasoning Segmentation</h2>
  <div class="authors">
    <div class="author">
      <span class="name">Aran Moradi</span>
      <span class="sid">ID: xxx</span>
      <span class="email">xxx</span>
    </div>
    <div class="author">
      <span class="name">Qianyu Bu</span>
      <span class="sid">ID: 3730364</span>
      <span class="email">st188433@stud.uni-stuttgart.de</span>
    </div>
  </div>
</div>

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

Second, a large language model (LLM), such as Llama, is used to process the input text, combine it with the visual information, and generate an output sequence. Importantly, the model is trained to produce a special token `[SEG]` when a segmentation output is required.

The third component is the projection layer, which aligns the image embeddings with the text embedding space. This allows the LLM to process both modalities jointly.

When the LLM generates the `[SEG]` token in its output, this token acts as a trigger for a segmentation module. A separate mask decoder then uses the internal visual features to generate the final segmentation mask.

---

### 3. Experiment

#### 3.1 Data Set

#### 3.2 Pipeline

#### 3.3 Training

---

### 4. Results

SegLLM outperforms the previous state-of-the-art method LISA by 18~30% on the multi-round MRSeg benchmark, and also achieves a 5.5% improvement in cIoU and 4.5% improvement in Acc@0.5 on the standard single-round RefCOCO benchmark.

#### 4.1 Evaluation Metrics

#### 4.2 Ablation Study

#### 4.3 Conclusions

Overall, SegLLM does a great job at bringing image segmentation into a multi-round conversation setting, beating existing methods by a large margin while also getting better results on single-round tasks.

But it still has some weak spots: it can get confused when the conversation order changes, it tends to rely a lot on positional words in queries, and it has trouble when there are multiple similar objects in the same image or when the question is not very clear.

---

### 5. Our Opinion

We find SegLLM to be a genuinely interesting piece of work, as it solves a real limitation in existing segmentation models — the inability to follow up on previously segmented objects. This significantly raises the ceiling for this type of task.

However, we do have two concerns. First, if the model makes a wrong segmentation in the first round, that error could potentially carry forward into all subsequent rounds, since each round builds on top of previous outputs. This raises the question of how robust the model is to early-stage mistakes.

Second, the model appears to be sensitive to the order of conversation history, which could be a practical issue in real-world use. Drawing from practices in NLP evaluation, where it is common to not only test on the original input, but also reverse the option order or paraphrase the query to test stability, a similar approach should be applied here. Testing SegLLM with reordered or paraphrased conversation histories would give a more reliable picture of how robust the model actually is in practice.

---

### Reference
