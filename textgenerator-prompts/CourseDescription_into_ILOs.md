---
PromptInfo:
  promptId: genILO
  name: 🧑‍🏫 Create active learning objectives from course description
  description: Takes course info from note and generates ILOs
  author: Vincent Tijms
  tags: writing, education
  version: 0.0.1
share: true
---
Take {{content}} and generate good learning objectives for this course. Note that good learning objectives start with a verb at the desired level of knowledge or skills, using Bloom's taxonomy. Make sure each objective is an outcome. Keep each objective as succinct and clear as possible. Output the new list as a series of bullet points, preceded by the sentence 'After successfully completing this course, the student is able to:' Use an h2 header titled 'LLM-generated learning objectives'.