# SMILE-College: A Dataset for Sentiment Analysis of Student Mental Health Support in Colleges

[![image](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)

- In this repository, we are releasing the newly created SMILE-College (Sentiment analysis of students' mental health support in Colleges) dataset for sentiment prediction and limitation analysis tasks of mental health support in colleges. The SMILE-College dataset is provided in folder [SMILE-College Dataset](https://github.com/LEAF-Lab-Stevens/SMILE-College/tree/main/SMILE-College%20Dataset) in this repository. More details are provided below.

- Links related to this work:
  - Dataset and codes: https://github.com/LEAF-Lab-Stevens/SMILE-College
  - Student Voice Survery data: https://reports.collegepulse.com/current-state-of-mental-health

## Student Voice Survey (SVS)
This study uses Student Voice Survey response data by College Pulse (https://reports.collegepulse.com/current-state-of-mental-health) on the current state of mental health, designed by College Pulse, to examine the social and emotional well-being of students. Conducted in 2022, the survey included 20 questions and was completed by 2,000 undergraduate students from over 1,500 U.S. colleges and universities. The study focuses on text responses  of a survey question regarding the effectiveness and areas needing improvement in college mental health services. 

```Survey Question:``` What mental health or wellness services and supports provided by your college are working well? What aspects of mental health and wellness need more attention?

## Data Pre-processing
- **Examples of responses without necessary context for sentiment analysis**
In analyzing the mental health survey data, significant challenges emerged, particularly regarding respondent engagement and data quality. Minimalistic and off-topic responses reduced the dataset's reliability, and the subjective nature of the survey introduced substantial analytical challenges. Examples of such data points in the original SVS dataset are shown below:

![image](https://github.com/LEAF-Lab-Stevens/SMILE-College/blob/main/images/examples_rq2.png)


## Sentiment Annotations

This dataset is annotated through a meticulous human-machine collaboration process, ensuring comprehensive sentiment categorization and accuracy. 
**Three Steps involved during annotations:**
- ```Sentiment Annotation with LLMs```
Utilizes large language models (LLMs) with a coarse prompt to categorize sentiments into the standard three categories: Satisfied, Dissatisfied, and Neutral. This step serves as a preliminary assessment of students' sentiment spectrum. The coarse prompt includes task-specific instructions, survey questions with responses, and label-specific guidelines to guide the LLMs.
- ```Sentiment Category Identification```
Multiple LLMs are evaluated and findings indicate limitations in the standard three-category framework, leading to the introduction of the "Mixed" category for nuanced sentiment expressions.
- ```Human Annotation and Validation```
A two-stage annotation process is employed, involving initial annotation by one annotator and validation by another. Disagreements are resolved collaboratively through discussions among annotators and researchers to reach a consensus on the final sentiment labels.

## SMILE-College Dataset
The sentiment analysis of students' mental health support in Colleges (SMILE-College) dataset comprises of ```school name, comments and validated_labels```. The sentiment labels include four categories: ```Satisfied, Dissatisfied, Mixed, and Neutral```, providing a nuanced understanding of students' emotional expressions. The following table describes the basic statistics of this dataset:

<table>
    <caption>Statistics of the SMILE-College dataset.</caption>
    <thead>
        <tr>
            <th></th>
            <th><strong>Satisfied</strong></th>
            <th><strong>Dissatisfied</strong></th>
            <th><strong>Mixed</strong></th>
            <th><strong>Neutral</strong></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>No. of Records</td>
            <td>107</td>
            <td>376</td>
            <td>220</td>
            <td>90</td>
        </tr>
        <tr>
            <td>Average response length (in words)</td>
            <td>21.84</td>
            <td>33.01</td>
            <td>28.06</td>
            <td>18.15</td>
        </tr>
        <tr>
            <td>Min response length (in words)</td>
            <td>12</td>
            <td>12</td>
            <td>12</td>
            <td>12</td>
        </tr>
        <tr>
            <td>Max response length (in words)</td>
            <td>93</td>
            <td>199</td>
            <td>106</td>
            <td>46</td>
        </tr>
        <tr>
            <td>Average # of sentences in responses</td>
            <td>1.89</td>
            <td>2.51</td>
            <td>2.42</td>
            <td>2.03</td>
        </tr>
        <tr>
            <td>Min # of sentences in responses</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
        </tr>
        <tr>
            <td>Max # of sentences in responses</td>
            <td>7</td>
            <td>11</td>
            <td>8</td>
            <td>5</td>
        </tr>
    </tbody>
</table>



## Target Tasks
To evaluate the usability of the SMILE-College data, we investigated three tasks: Sentiment prediction, Prediction error analysis, and Support limitation identification.

- **Sentiment Prediction**

We designed **fine-grained** prompts with the four nuanced sentiment categories for LLMs to predict sentiment labels of student responses. GPT-3.5 outperformed other models, particularly in F1 scores, with Orca 2 showing the best results among the 7 billion-parameter models.

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

- **Prediction Error Analysis with Confusion Matrix**

The confusion matrices in below figure reveal that both GPT-3.5 and Orca 2 struggle to distinguish between "Mixed" and "Dissatisfied" sentiments, while Mistral tends to categorize many records as "Neutral." Llama 2 shows confusion between "Dissatisfied" and "Mixed" categories and often misclassifies "Satisfied" records as "Mixed" or "Neutral."

<div style="display: flex; justify-content: space-around; align-items: flex-start; flex-wrap: wrap;">
    <div style="flex: 1; min-width: 200px; text-align: center;">
        <img src="https://github.com/LEAF-Lab-Stevens/SMILE-College/blob/main/images/cf_mistral.png" alt="Mistral" style="width: 100%;">
        <p><strong>Mistral</strong></p>
    </div>
    <div style="flex: 1; min-width: 200px; text-align: center;">
        <img src="https://github.com/LEAF-Lab-Stevens/SMILE-College/blob/main/images/cf_orca.png" alt="Orca 2" style="width: 100%;">
        <p><strong>Orca 2</strong></p>
    </div>
    <div style="flex: 1; min-width: 200px; text-align: center;">
        <img src="https://github.com/LEAF-Lab-Stevens/SMILE-College/blob/main/images/cf_llama.png" alt="Llama 2" style="width: 100%;">
        <p><strong>Llama 2</strong></p>
    </div>
    <div style="flex: 1; min-width: 200px; text-align: center;">
        <img src="https://github.com/LEAF-Lab-Stevens/SMILE-College/blob/main/images/cf_gpt3.5.png" alt="GPT-3.5" style="width: 100%;">
        <p><strong>GPT-3.5</strong></p>
    </div>
</div>

<p><strong>Figure:</strong> Confusion metrics for the four models on SMILE-College dataset.</p>

- **Limitations Analysis of Mental Health Support in Colleges**

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




