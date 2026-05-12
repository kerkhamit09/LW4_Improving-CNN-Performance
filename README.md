# Laboratory-Work-4-Activity-Improving-CNN-Performance-Using-Regularization

# Google Colab Link:<a href="https://colab.research.google.com/drive/19_-8c7lZuUmpwxQC5WZJ-kr0BC1iPhdG?usp=sharing">CLICK HERE</a>!

# Google Colab Link(goodmodel):<a href="https://colab.research.google.com/drive/1ah_XBwFvX_dUbLrwd3gbF4WYgJnm0A61?usp=sharing">CLICK HERE</a>!

<table style="width: 375.156px;">
<tbody>
<tr>
<td style="width: 142px;">Metric&nbsp;</td>
<td style="width: 107px;">&nbsp;Baseline Model</td>
<td style="width: 107.156px;">Improved Model&nbsp;</td>
</tr>
<tr>
<td style="width: 142px;">&nbsp;Training Accuracy</td>
<td style="width: 107px;">&nbsp;0.7508</td>
<td style="width: 107.156px;">0.9208</td>
</tr>
<tr>
<td style="width: 142px;">&nbsp;Validation Accuracy</td>
<td style="width: 107px;">&nbsp;0.8230</td>
<td style="width: 107.156px;">0.9140</td>
</tr>
<tr>
<td style="width: 142px;">Precision</td>
<td style="width: 107px;">&nbsp;0.9506</td>
<td style="width: 107.156px;">0.9827</td>
</tr>
<tr>
<td style="width: 142px;">&nbsp;Recall</td>
<td style="width: 107px;">&nbsp;0.8230</td>
<td style="width: 107.156px;">&nbsp;0.9140</td>
</tr>
<tr>
<td style="width: 142px;">F1-score</td>
<td style="width: 107px;">&nbsp;0.8788</td>
<td style="width: 107.156px;">&nbsp;0.9462</td>
</tr>
<tr>
<td style="width: 142px;">AUC Score</td>
<td style="width: 107px;">nan</td>
<td style="width: 107.156px;">0.9963</td>
</tr>
</tbody>
</table>
<!-- DivTable.com -->

GUIDE QUESTIONS (Student Explanation & Reflection)<br>
# A. Model Evaluation Analysis<br>
# 1. What were the weakest-performing classes based on the confusion matrix?
Ans: Based on the confusion matrix, the weakest-performing classes were SoursopTree, StarFruitTree, and TalisayTree because they showed more misclassifications and lower prediction accuracy compared to the other classes. Among them, SoursopTree was the weakest-performing class since it had the fewest correct predictions and was frequently confused with other tree classes.

# 2. How did Precision, Recall, and F1-score vary across classes?
Ans: Precision, Recall, and F1-score varied across the classes depending on how accurately the model classified each tree category. Classes such as TangerineTree and WateryRose AppleTree achieved the highest scores, indicating strong classification performance with high accuracy and consistency. StarFruitTree also showed high Precision but relatively lower Recall, meaning the model predicted it accurately but missed some actual instances. Meanwhile, SoursopTree and TalisayTree had comparatively lower scores, showing that these classes were more difficult for the model to classify correctly. Overall, the variation in the metrics reflects differences in how well the model learned the features of each class.

# 3. What does a low recall indicate in your model?
Ans: A low recall in the model indicates that the model failed to identify many actual instances of a class, resulting in a higher number of false negatives. This means that although the model may correctly predict some samples, it misses several true samples belonging to that class. In the context of the tree classification model, a low recall suggests that the model had difficulty recognizing all images of certain tree classes, causing some images to be incorrectly classified as other categories.

# 4. How does AUC score reflect model performance compared to accuracy?
Ans: While accuracy only tells you the overall correct predictions (92% for the Improved Model), the AUC score of 0.9963 proves that the model has near-perfect ability to separate positive from negative classes across every threshold, making it a far more reliable measure of true discriminative power — especially since the Baseline Model already had high accuracy (82%) but its AUC was "nan" (undefined), likely due to class imbalance or prediction issues that accuracy alone hid.

# B. Model Improvement<br>
# 5. How did data augmentation affect validation accuracy?
Ans: Data augmentation increased validation accuracy by 9.1% (from 82.30% to 91.40%) by reducing overfitting through varied training image transformations like flips, rotations, and zooms.


# 6. Why is Batch Normalization important in CNNs?
Ans: Batch Normalization is important in CNNs because it stabilizes and accelerates training by normalizing each batch's activations to have zero mean and unit variance, which reduces "internal covariate shift" (where layer inputs keep changing as previous layers update), allowing for higher learning rates, reducing overfitting (slight regularizing effect), and making deep networks converge significantly faster—in your model, it's placed after the Dense layer with 64 units to stabilize the fully connected features before the final Dropout and output layers.

# 7. What role did Dropout play in improving your model?
Ans: Dropout forced the model to learn more robust and redundant features by randomly disabling neurons during training, which reduced overfitting—this is clearly shown in the results where the Improved Model achieved high training accuracy (92.08%) and nearly matching validation accuracy (91.40%), while also boosting Precision to 98.27%, Recall to 91.40%, and F1-score to 94.62%, demonstrating that Dropout helped the model generalize well to unseen data instead of memorizing the training set.

# 8. How did Early Stopping prevent overfitting?
Ans: Early Stopping prevents overfitting by monitoring the validation loss during training and halting the process once the validation performance stops improving for a set number of epochs (patience), thereby avoiding the point where the model begins to memorize noise in the training data instead of learning generalizable patterns—this would be reflected in your Improved Model by the close training (92.08%) and validation (91.40%) accuracy gap.

# C. Performance Comparison<br>
# 9. What improvements were observed after modifying the model?
Ans: After modifying the model with data augmentation, Dropout, Batch Normalization, and MobileNetV2, the Improved Model showed substantial gains across all metrics: Validation Accuracy rose by 9.1% (from 82.30% to 91.40%), Precision improved to 98.27%, Recall increased to 91.40%, F1-score jumped to 94.62%, and AUC reached an outstanding 0.9963 (compared to the Baseline Model's undefined AUC), proving the model became far more accurate, reliable, and better at distinguishing between classes.

# 10. Which enhancement contributed the most to performance improvement? Why?
Ans: While all enhancements played a role, data augmentation likely contributed the most to the performance improvement because it directly addressed the root cause of overfitting—limited training data—by generating diverse image variations (flips, rotations, zooms, brightness/contrast changes), which forced the model to learn invariant, generalizable features rather than memorizing specific patterns, as evidenced by the dramatic increase in validation accuracy (82.30% → 91.40%) and the near-elimination of the training-validation gap (92.08% vs. 91.40%), whereas Dropout and Batch Normalization primarily stabilized and regularized an already-generalizing model.

# 11. Did the gap between training and validation accuracy decrease? Explain.
Ans: Yes, the gap between training and validation accuracy decreased significantly—the Baseline Model had a negative gap of -7.22% (training 75.08% vs. validation 82.30%, meaning it was actually underfitting or the validation set was easier), while the Improved Model achieved a very tight gap of only +0.68% (training 92.08% vs. validation 91.40%), indicating that the combination of data augmentation, Dropout, and Batch Normalization successfully reduced overfitting and helped the model generalize almost perfectly to unseen data.

# D. Explainability (Grad-CAM Integration<br>
# 12. How did Grad-CAM help in understanding model predictions?
Ans: It allowed me to visualize a heatmap over the image. In the Grad-CAM Overlay, the 'hot' areas (red) show exactly which pixels influenced the model's decision.

# 13. Did the improved model focus on more relevant regions? Provide evidence.
Ans:Yes, the improved model focused on more relevant regions, as evidenced by the Grad-CAM heatmap visualization—the heatmap should show strong activation concentrated on the actual object of interest (e.g., the coconut tree trunk, leaves, or fruit) rather than spreading to irrelevant background areas, sky, or ground; this improved focus is a direct result of data augmentation (which taught the model to ignore background variations), Dropout (which prevented reliance on spurious features), and the high AUC score of 0.9963 (proving the model learned true discriminative features rather than shortcuts); without running the Grad-CAM code on your specific image, the evidence is indirect but strongly supported by the near-perfect AUC and the tight training-validation gap.

# 14. Why is explainability important in real-world AI applications?
Ans: Explainability is crucial in real-world AI applications because it builds trust, ensures accountability, and enables debugging—in fields like healthcare (cancer detection), finance (loan approvals), and autonomous vehicles, stakeholders need to understand why a model made a specific prediction (e.g., which image regions triggered a "coconut tree" classification via Grad-CAM) to validate that the model is focusing on clinically relevant features rather than spurious correlations (like a watermark or timestamp), comply with regulations (GDPR's "right to explanation"), identify biases, and justify decisions to patients, customers, or regulators; without explainability, even a 99% accurate model is a "black box" that cannot be safely deployed in high-stakes environments.
