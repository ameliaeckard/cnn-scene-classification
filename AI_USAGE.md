# AI Usage Disclosure

## AI Coding Tool Used

I used **ChatGPT by OpenAI** as a code assistance and debugging tool during this project.

AI was not used to generate or alter the experimental results reported in this project, and it was not used to choose the original experiment ideas. All validation accuracies, losses, and other results came directly from running my own experiments.

## How AI Was Used

| Area | AI Assistance |
|---|---|
| Debugging | Helped explain why sections of the training code were not behaving as expected and suggested possible fixes. |
| Code modification | Helped show how existing code could be changed to support different model or training configurations. |
| Training interpretation | Helped interpret changes in training loss, validation loss, and validation accuracy across epochs. |
| Experiment comparison | Helped compare the results of completed experiments and explain what the differences in validation accuracy suggested. |

## Representative Examples

Some representative ways I used ChatGPT during the project were:

1. I asked how to modify sections of my existing training code when I wanted the program to behave differently.
2. I provided training output and asked what the training and validation loss trends suggested about the model.
3. I asked for help comparing the results of two completed experiments and interpreting why one performed better or worse.
4. I used ChatGPT to help debug code when a section was not producing the output I expected.
5. After completing the experiments, I used ChatGPT to help organize the results into a concise experiment table and documentation.

## Example of a Questionable or Ineffective AI Suggestion

One AI-assisted experiment involved aggressive image transformations. I tested four-way flip augmentation using the original image, a horizontal flip, a vertical flip, and a horizontal-plus-vertical flip.

I initially thought increasing the effective size and spatial variety of the training set might reduce overfitting. Instead, validation accuracy decreased from the 49.79% baseline to 47.08%.

The result showed that not every augmentation is appropriate for scene recognition. In particular, vertical flips can create unrealistic orientations for natural and indoor scenes. I rejected this augmentation rather than keeping it simply because it increased the amount of training data.

## How I Verified AI Assistance

I did not assume that AI-generated code or explanations were correct. When ChatGPT suggested a code change, I compared it with my existing implementation, made any necessary modifications, and then ran the code myself. I used the resulting training logs, validation losses, and validation accuracies to determine whether the change actually worked.

For interpretation questions, I compared ChatGPT's explanation against the numerical results from my experiments. If a suggestion did not match the behavior I observed when running the model, I relied on the experimental output rather than the AI response.

All reported results came directly from my own program runs.

## Decision I Made Independently

An important experimental decision I made was to use **RGB input and a pretrained ResNet18 for the final model** after examining the results of my earlier experiments.

The RGB experiment improved validation accuracy from the 49.79% baseline to 51.88%, showing that color contained useful information. However, that improvement was still relatively small. My final model used RGB input with transfer learning through a pretrained ResNet18 and reached a best validation accuracy of 89.79%.

I made the decision based on the actual results of my experiments rather than simply accepting an AI recommendation.

## Summary

AI was used as a support tool for coding, debugging, interpreting results, and helping with documentation. I remained responsible for choosing the experiments, running the models, evaluating their results, deciding which changes to keep, and verifying that the final implementation worked.
