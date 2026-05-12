<div align="center">

# Seminar Blog  
## Recent Applications of Machine Learning

**Summer Semester 2026**

<br>

### Authors

| Name | Student ID | Email |
|:---|:---:|:---|
| Aran Moradi | xxx | xxx |
| Qianyu Bu | 3730364 | st188433@stud.uni-stuttgart.de |

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

