# Seminar Blog: Recent Applications of Machine Learning

**Authors:** Aran Moradi and Qianyu Bu  
**Semester:** 2026SS

---

## Author Information

| Name | Student ID | Email |
|---|---|---|
| Aran Moradi | xxx | xxx |
| Qianyu Bu | 3730364 | st188433@stud.uni-stuttgart.de |

---

# Blog Post 1

## SegLLM: Multi-round Reasoning Segmentation

### Background and Problem
Current LLM models or detection models, are inable to handle multi-round, interactive conversations. For instance, if there is a request on a segmentation (e.g.: “highlight the man with the white hoodie”), current models can not handle additional queries based on the previous mask output (e.g.: “mask the bike behind the man from the previous prompt).

### Method
Unlike other state-of-the-art model, SegLLM feeds previous segmentation outputs of the mask decoder into the LLM, and the conversation context into the input query of the mask decoder. 

### Experiment
