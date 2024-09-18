# ResNet-50 Image Classification Explanation using LIME and SHAP

## Project Overview
This project uses **ResNet-50** to classify images and explain the predictions made by the model. The explanations are generated using two popular model explanation techniques: **LIME (Local Interpretable Model-agnostic Explanations)** and **SHAP (SHapley Additive exPlanations)** with the partition explainer. These methods help to understand the reasons behind the model's classification decisions by highlighting important features in the images.

## Key Techniques
- **LIME**: Generates local explanations for individual predictions by perturbing the input and observing changes in the model's output.
- **SHAP (Partition Explainer)**: Uses a game theory approach to distribute the importance of features among different parts of the input, making it easier to understand the global impact of features on predictions.

---

## Results
Given Inputs:
|Input 1|Input 2|
|-----|----|
|![1](https://github.com/user-attachments/assets/6f4e88c9-8e32-486e-a367-fdfcee816530)| ![2](https://github.com/user-attachments/assets/7e5a9287-915c-45cc-a736-aced5f420ba3)|

### LIME Explanations
![1_lime](https://github.com/user-attachments/assets/a25362a4-bb34-43fd-8697-14adab57b79f)
![2_lime](https://github.com/user-attachments/assets/45660d0d-6152-4976-8d8e-ebbca5a46c35)


The model shows that the head and neck of the bird were the most important parts of the image that positively guided the model to predict the image as `American_egret` class. However, parts of the background have negatively affected its decision.

For the second image, certain parts of the boat and water contributed positively to the classification as a `lifeboat`, while other parts had a negative impact. Notably, the `lifeboat` class was the model’s fourth prediction, with a confidence of `0.039%`. This suggests that the large white section of the boat which resembles a real lifeboat, may have contributed to this prediction.

### SHAP Explanation (Partition Explainer)
![1_2_shap](https://github.com/user-attachments/assets/eb19ab5b-81f6-4615-9c31-6aaca475c03b)

As shown in the figure, in the first image, regions including parts of the neck and the back of the bird have positively contributed to the correct classification as `American_egret`, while the bird's eyes and beak have undermined the possibility of the first class and strengthened the likelihood of belonging to other classes like `crane` or `little_blue_heron`.

For the second image, most parts of the boat, in addition to part of the background, led to the decision to classify this input as a `speedboat`. However, similar to the LIME result, big white parts of the boat led the model to classify it in other classes like `lifeboat`.

---

## Code Details
