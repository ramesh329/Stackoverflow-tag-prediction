# Stack Overflow: Tag Prediction

<h2> 1. Problem Statemtent </h2>
Predicting the tags based on the content in the question and description posted on StackOverflow

**Why tags** :
Based on tags ,stackoverflow sends the questions to concerned persons who have answered similar questions in the past

 <h2> 1.1 Real World / Business Objectives and Constraints </h2>

1. Predict as many tags as possible with high precision and recall.
2. Incorrect tags could impact customer experience on StackOverflow.
3. No strict latency constraints,can take couple of minutes to predict the tags

<h2>1.2 Data-Overview </h2>

__Data Field Explaination__

Dataset contains 6,034,195 rows. The columns in the table are:<br />
<pre>
<b>Id</b> - Unique identifier for each question<br />
<b>Title</b> - The question's title<br />
<b>Body</b> - The body of the question<br />
<b>Tags</b> - The tags associated with the question in a space-seperated format (all lowercase, should not contain tabs '\t' or ampersands '&')<br />
</pre>

<br />


<h2>1.3 Mapping the real-world problem to a Machine Learning Problem </h2>

<p> It is a multi-label classification problem  <br>

<h3>Performance metric </h3>
<b>Micro-Averaged F1-Score (Mean F Score) </b>: 
The F1 score can be interpreted as a weighted average of the precision and recall, where an F1 score reaches its best value at 1 and worst score at 0. The relative contribution of precision and recall to the F1 score are equal. The formula for the F1 score is:

<i>F1 = 2 * (precision * recall) / (precision + recall)</i><br>

In the multi-class and multi-label case, this is the weighted average of the F1 score of each class. Micro-Averaged F1-Score takes class-imbalance into consideration.It gives more weightage to the frequency of occurence of tags<br>

<b>'Micro f1 score': </b><br>
Calculate metrics globally by counting the total true positives, false negatives and false positives. This is a better metric when we have class imbalance.

<b> Hamming loss </b>: In simplest of terms, Hamming-Loss is the fraction of labels that are incorrectly predicted, i.e., the fraction of the wrong labels to the total number of labels.. <br>


**Note** : Here we are taking only 500000 data-points for this assignment with more weightage for the feature "Title" and using only top-500 tags for building classification models
