# Demonstrating the Power of the Crowd for Explainable AI

## Introduction

There is a need for explainability for machine learning models. Interpretability is a prerequisite for trust. With pre-trained language models and complex NLP tasks such as information extraction, it is particularly difficult to understand the reasoning behind the model prediction. While automatic explainability methods do exist, they are again machine learning models making predictions. So, why not ask humans to provide information on how they reason? In this research, I present a scenario of asking a crowd of human annotators to explain their decision in a text classification task by annotating the words in the sentence as important and not important. I explain the design of the project and the tools that I use for managing the crowd to ensure the good quality of produced annotations. Automatic evaluation of crowd annotations shows a high agreement between annotators on both classification and explainability tasks. Ultimately, the goal of my research is to compare explanations of the model against human explanations and predict the model errors assuming that model reasoning should be similar to the reasoning of humans.

## Task: Relation Extraction

Given a sentence and a pair of entities, identify the relation between these entities. This task is essential for transforming unstructured textual data written by humans into structured data which is readable by machines.

**Main challenges**
  * heterogeneity of natural language
  * large number of classes (up to 100, depending on the dataset)
  * class imbalance (the classes are not equally distributed in the data)

**State of the art**
State-of-the-art models show high performance (85% F1). 

### Example

**Anna Fischer-Dückelmann** was one of the first women to receive a medical degree in the German-speaking countries, received from the **University of Zurich**.

Resulting relation: `Person: Schools Attended`
