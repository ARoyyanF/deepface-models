
# [Notebook](https://github.com/ARoyyanF/deepface-models/blob/main/facial_recognition_model_comparison%20asian_celeb%202000%20pairs.ipynb) explanation
## 1. The Core Task: Face Verification
The fundamental method being tested is face verification, which answers the question: "Do these two pictures belong to the same person?" To test this, the system needs pairs of images with known outcomes (ground truth).

The notebook uses the "Asian Celebrity" dataset, which is structured with one folder for each person. From this, two types of test pairs are dynamically created:

Positive Pairs (Match): Two different images are randomly selected from the same person's folder. The ground truth label for this pair is 1 (or "Same").

Negative Pairs (No-Match): Two images are randomly selected from two different people's folders. The ground truth label for this pair is 0 (or "Different").

In this notebook, 2,000 such pairs (1,000 positive and 1,000 negative) were generated to form a balanced test set.

## 2. The Evaluation Process
For every model being tested (like VGG-Face, ArcFace, Facenet, etc.), the notebook performs the following evaluation loop:

Iterate Through Pairs: The model processes each of the 2,000 image pairs one by one.

Verification Function: For each pair, it uses the DeepFace.verify() function. This function analyzes both images, calculates a distance score (typically using 'cosine' similarity) to determine how similar the faces are, and returns a verified result (True or False) based on a pre-defined threshold for that specific model. This True/False output is the model's prediction.

Measure Speed: The time it takes for the model to process each pair is recorded. This is later averaged to determine the model's processing speed.

## 3. Calculating Performance Metrics
After all 2,000 pairs have been processed by a model, its performance is calculated by comparing its predictions against the ground truth labels created in the first step. This results in the following key metrics:

Accuracy: What percentage of the 2,000 pairs did the model classify correctly (both matches and non-matches)? This gives a general score of its overall performance.

Precision: Of all the pairs the model predicted as a "match," what percentage was correct? This measures the reliability of the model's positive predictions, answering "When it says it's a match, how often is it right?"

Recall: Of all the actual "match" pairs that existed in the test set, what percentage did the model successfully find? This measures the model's ability to identify all true matches.

F1-Score: This is the harmonic mean of Precision and Recall. It provides a single, balanced score that is especially useful when there's an uneven class distribution or when both false positives and false negatives are important.

## 4. Compiling the Final Results
This entire process is repeated for every model listed in the notebook's configuration. The calculated metrics (Accuracy, Precision, Recall, F1-Score) and the average processing time for each model are compiled into a single table (a pandas DataFrame).

This final table is the direct input for Section 6: Results Comparison and Visualization of the [notebook](https://github.com/ARoyyanF/deepface-models/blob/main/facial_recognition_model_comparison%20asian_celeb%202000%20pairs.ipynb). The charts and graphs in that section are simply visual representations of this compiled data, making it easy to compare the models' trade-offs between accuracy, reliability, and speed.

<img width="1490" height="985" alt="image" src="https://github.com/user-attachments/assets/f7042c64-dc7c-411a-8b9f-fb7947eae39e" />
<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/b93973b1-9b86-4647-bc6f-61ab519d4303" />
<img width="983" height="790" alt="image" src="https://github.com/user-attachments/assets/f33c7d7a-7757-4aeb-8469-abdd12b067cd" />
<img width="1477" height="1475" alt="image" src="https://github.com/user-attachments/assets/71ad004e-566e-4d89-8218-17787baed3ac" />
<img width="1750" height="555" alt="image" src="https://github.com/user-attachments/assets/b0ae6333-1180-47de-b34b-456f33bad35d" />




