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
Utilizes large language models (LLMs) with a **coarse prompt** to categorize sentiments into Satisfied, Dissatisfied, and Neutral. This step serves as a preliminary assessment of students' sentiment spectrum.
- ```Sentiment Category Identification```
Multiple LLMs are evaluated and findings indicate limitations in the standard three-category framework, leading to the introduction of the "Mixed" category for nuanced sentiment expressions.
- ```Human Annotation and Validation```
A two-stage annotation process is employed, involving initial annotation by one annotator and validation by another.


## Sentiment Prediction
We designed **fine-grained** prompts for LLMs to predict sentiment labels of student responses. GPT-3.5 outperformed other models, particularly in F1 scores, with Orca 2 showing the best results among the 7 billion-parameter models.

<table>
  <thead>
    <tr>
      <th></th>
      <th colspan="3">Satisfied</th>
      <th colspan="3">Dissatisfied</th>
      <th colspan="3">Mixed</th>
      <th colspan="3">Neutral</th>
      <th colspan="3">Overall</th>
    </tr>
    <tr>
      <th></th>
      <th>Precision</th>
      <th>Recall</th>
      <th>F1</th>
      <th>Precision</th>
      <th>Recall</th>
      <th>F1</th>
      <th>Precision</th>
      <th>Recall</th>
      <th>F1</th>
      <th>Precision</th>
      <th>Recall</th>
      <th>F1</th>
      <th>Precision</th>
      <th>Recall</th>
      <th>F1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Mistral</td>
      <td>0.88</td>
      <td>0.28</td>
      <td>0.43</td>
      <td>0.95</td>
      <td>0.46</td>
      <td>0.62</td>
      <td>0.61</td>
      <td>0.64</td>
      <td>0.62</td>
      <td>0.26</td>
      <td><strong>0.99</strong></td>
      <td>0.41</td>
      <td>0.77</td>
      <td>0.54</td>
      <td>0.57</td>
    </tr>
    <tr>
      <td>Orca 2</td>
      <td>0.94</td>
      <td><strong>0.30</strong></td>
      <td><strong>0.45</strong></td>
      <td>0.86</td>
      <td><strong>0.70</strong></td>
      <td><strong>0.77</td>
      <td>0.58</td>
      <td>0.65</td>
      <td>0.62</td>
      <td><strong>0.83</strong></td>
      <td>0.61</td>
      <td><strong>0.71</strong></td>
      <td><strong>0.79</strong></td>
      <td>0.62</td>
      <td><strong>0.68</strong></td>
    </tr>
    <tr>
      <td>Llama 2</td>
      <td><strong>1.00</strong></td>
      <td>0.06</td>
      <td>0.11</td>
      <td>0.89</td>
      <td>0.58</td>
      <td>0.70</td>
      <td>0.51</td>
      <td><strong>0.93</strong></td>
      <td><strong>0.66</td>
      <td>0.54</td>
      <td>0.86</td>
      <td>0.66</td>
      <td>0.76</td>
      <td><strong>0.64</strong></td>
      <td>0.61</td>
    </tr>
    <tr>
      <td>GPT-3.5</td>
      <td>0.78</td>
      <td><strong>0.76</strong></td>
      <td><strong>0.77</strong></td>
      <td><strong>0.96</strong></td>
      <td><strong>0.71</strong></td>
      <td><strong>0.82</strong></td>
      <td><strong>0.66</strong></td>
      <td>0.90</td>
      <td><strong>0.76</strong></td>
      <td>0.77</td>
      <td>0.92</td>
      <td><strong>0.84</strong></td>
      <td><strong>0.83</strong></td>
      <td><strong>0.80</strong></td>
      <td><strong>0.80</strong></td>
    </tr>
  </tbody>
</table>


## Limitation Analysis

Using GPT-3.5, we identified and extracted limitations from "Dissatisfied" responses in the SMILE-College dataset, revealing significant areas for improvement in college mental health services. These limitations were clustered into ten categories, such as quality of counseling, accessibility, and awareness, highlighting key areas for enhancing student well-being.

<table>
  <thead>
    <tr>
      <th colspan="3">Frequency of Identified Limitations in Mental Health Services by Cluster</th>
    </tr>
    <tr>
      <th>Cluster</th>
      <th>Limitations</th>
      <th>Freq</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Quality of Counseling Services</td>
      <td>157</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Availability and Accessibility</td>
      <td>76</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Challenges in accessing the services</td>
      <td>76</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Awareness and Education</td>
      <td>73</td>
    </tr>
    <tr>
      <td>5</td>
      <td>Issues with Therapist Matching</td>
      <td>65</td>
    </tr>
    <tr>
      <td>6</td>
      <td>Inadequacies in support, communication, community connection</td>
      <td>64</td>
    </tr>
    <tr>
      <td>7</td>
      <td>Personal Experiences and Preferences</td>
      <td>52</td>
    </tr>
    <tr>
      <td>8</td>
      <td>Financial and Administrative Concerns</td>
      <td>48</td>
    </tr>
    <tr>
      <td>9</td>
      <td>Diversity and Inclusivity</td>
      <td>22</td>
    </tr>
    <tr>
      <td>10</td>
      <td>Issues with Referrals and Redirection</td>
      <td>13</td>
    </tr>
  </tbody>
</table>


## Analysis

- ```Difference between the outcomes of coarse prompt and fine-grained prompt```

![image](https://github.com/LEAF-Lab-Stevens/SMILE-College/blob/main/images/comparison_example1_.png)

![image](https://github.com/LEAF-Lab-Stevens/SMILE-College/blob/main/images/comparison_example1.png)