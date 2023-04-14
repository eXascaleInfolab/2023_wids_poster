# Demonstrating the Power of the Crowd for Explainable AI

## Introduction

There is a need for explainability for machine learning models. Interpretability is a prerequisite for trust. With pre-trained language models and complex NLP tasks such as information extraction, it is particularly difficult to understand the reasoning behind the model prediction. While automatic explainability methods do exist, they are again machine learning models making predictions. So, why not ask humans to provide information on how they reason? In this research, I present a scenario of asking a crowd of human annotators to explain their decision in a text classification task by annotating the words in the sentence as important and not important. I explain the design of the project and the tools that I use for managing the crowd to ensure the good quality of produced annotations. Automatic evaluation of crowd annotations shows a high agreement between annotators on both classification and explainability tasks. Ultimately, the goal of my research is to compare explanations of the model against human explanations and predict the model errors assuming that model reasoning should be similar to the reasoning of humans.

## Task: Relation Extraction

Given a sentence and a pair of entities, identify the relation between these entities. This task is essential for transforming unstructured textual data written by humans into structured data which is readable by machines.

**Example**

**Anna Fischer-Dückelmann** was one of the first women to receive a medical degree in the German-speaking countries, received from the **University of Zurich**.

Resulting relation: `Person: Schools Attended`

**Main challenges**
  * heterogeneity of natural language
  * large number of classes (up to 100, depending on the dataset)
  * class imbalance (the classes are not equally distributed in the data)

State-of-the-art models show high performance (85% F1). However, the explainability of these models is often overlooked. As ML becomes more widely used, explainability is increasingly important: 
  * it increases trust and understanding of the results
  * helps people debug and improve the models
  * ensures that models are fair and non-discriminatory.


## Crowdsourcing Task Design
To ensure the good quality of annotations, we need to take into account the specific aspects of working with anonymous, online crowd annotators, for instance considering:
  * the diversity of the crowd in terms of spoken languages and education level
  * the online nature of our task, where the means to explain the task to workers and motivate them are limited

For our task, we applied the following filters of the annotators:
  * **Language.** we only select workers who know English and passed a language test on the platform
  * **Top annotators.** we use a built-in adjust bar to select the top 10% of the annotators based on their overall performance on the platform
  * **Skill.** we only select workers who show that they understood the task

### Example of the task along with the annotations

![alt text][task]

[task]: https://github.com/eXascaleInfolab/2023_wids_poster/blob/main/task.png "Crowdsourcing Task Design"

## Approach

**What a model should know?**

Hypothesis: model reasoning should be similar to human reasoning. 

Idea: ask crowd annotators to annotate the words in the sentence as important or not important. I use [Toloka crowdsourcing platform](https://toloka.ai) to eploy crowd annotators.

How: first ask annotators to “do” the task of judging on type of relation between two given entities in the sentence if any. By doing so, they are exercising their rationales instead of imagining that can potentially make their rationales annotation more reliable.

**What a model knows?**

Idea: apply model-agnostic explainability method called [LIME](https://arxiv.org/abs/1602.04938) to automatically extract the words’ weights.

![alt text][pipeline]

[pipeline]: https://github.com/eXascaleInfolab/2023_wids_poster/blob/main/Model%20interpret%20pipeline.png "Model Explainability Pipeline"
