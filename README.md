<style>
  body { font-family: 'Segoe UI', sans-serif; max-width: 860px; margin: auto; }
  h1, h2 { color: #2c3e50; border-bottom: 2px solid #3498db; padding-bottom: 6px; }
  blockquote { background: #f0f7ff; border-left: 4px solid #3498db; padding: 10px 16px; border-radius: 4px; }
  table { border-collapse: collapse; width: 100%; }
  td, th { border: 1px solid #ddd; padding: 8px 12px; }
  th { background: #3498db; color: white; }
</style>

<div align="center">
  <h1>Seminar Blog</h1>
  <h2>Recent Applications of Machine Learning</h2>
  <strong>Summer Semester 2026</strong>
  <br><br>
  <h3>Authors</h3>
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

### Background and Problem

Current LLM or detection models are unable to handle multi-round interactive conversations. 

For example, when a user requests a segmentation task such as:

> “Highlight the man with the white hoodie.”

most existing models cannot process follow-up queries based on the previously generated mask output, such as:

> “Mask the bike behind the man from the previous prompt.”

This limitation makes interactive segmentation difficult in real-world conversational scenarios.

---

### Method

Unlike other state-of-the-art approaches, SegLLM feeds previous segmentation outputs from the mask decoder back into the LLM. 

At the same time, the conversation context is integrated into the query input of the mask decoder. This enables the model to maintain contextual understanding across multiple interaction rounds.

---

### Experiment

