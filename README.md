# SMILE-College: A Dataset for Sentiment Analysis of Student Mental Health Support in Colleges

[![image](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)

- This repository is an implementation of the SMILE-College (SentiMent analysis of students' mental health support in Colleges) dataset for Sentiment Prediction and Limitation Analysis tasks.

- In this work, we are releasing a publicaly available dataset SMILE-College for Sentiment Prediction task on students mental health support in colleges. The SMILE-College dataset is provided in folder [SMILE-College Dataset](https://github.com/LEAF-Lab-Stevens/SMILE-College/tree/main/SMILE-College%20Dataset) in this repository. More details are provided below.

- Links related to this work:
  - Dataset and codes: https://github.com/LEAF-Lab-Stevens/SMILE-College


## Dataset
The SMILE-College dataset is designed for sentiment analysis of student responses regarding mental health support in colleges. It is created using the responses of a survey question, Student Voice Survey by College Pulse (https://reports.collegepulse.com/current-state-of-mental-health). This dataset is annotated through a meticulous human-machine collaboration process, ensuring comprehensive sentiment categorization and accuracy. The dataset comprises of ```school name, comments and validated_labels```. The sentiment labels include four categories: ```Satisfied, Dissatisfied, Mixed, and Neutral```, providing a nuanced understanding of students' emotional expressions.

```Survey Question:``` What mental health or wellness services and supports provided by your college are working well? What aspects of mental health and wellness need more attention?

Three Steps involved during annotations:
- ```Sentiment Annotation with LLMs```
Utilizes large language models (LLMs) with a coarse prompt to categorize sentiments into Satisfied, Dissatisfied, and Neutral. This step serves as a preliminary assessment of students' sentiment spectrum.
- ```Sentiment Category Identification```
Multiple LLMs are evaluated and findings indicate limitations in the standard three-category framework, leading to the introduction of the "Mixed" category for nuanced sentiment expressions.
- ```Human Annotation and Validation```
A two-stage annotation process is employed, involving initial annotation by one annotator and validation by another.

<!-- 

## Results

Here we provide the results on the new version of natural language questions provided in `mimicsql_data/mimicsql_natual_v2`.

<table>
  <thead>
    <tr>
      <th>Dataset</th>
      <th colspan="2">Overall Evaluation</th>
      <th colspan="6">Breakdown Evaluation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td></td><td>Acc_LF</td><td>Acc_EX</td><td>Agg_op</td><td>Agg_col</td><td>Table</td><td>Con_col+op</td><td>Con_val</td><td>Average</td>
    </tr>
    <tr>
      <td>Testing</td><td>0.482</td><td>0.611</td><td>0.993</td><td>0.970</td><td>0.954</td><td>0.857</td><td>0.630</td><td>0.881</td>
    </tr>
    <tr>
      <td>Testing+recover</td><td>0.547</td><td>0.690</td><td>0.992</td><td>0.969</td><td>0.953</td><td>0.863</td><td>0.729</td><td>0.901</td>
    </tr>
    <tr>
      <td>Development</td><td>0.432</td><td>0.636</td><td>0.997</td><td>0.988</td><td>0.956</td><td>0.845</td><td>0.524</td><td>0.862</td>
    </tr>
    <tr>
      <td>Development+recover</td><td>0.526</td><td>0.741</td><td>0.997</td><td>0.988</td><td>0.956</td><td>0.837</td><td>0.639</td><td>0.883</td>
    </tr>
  </tbody>
</table> -->