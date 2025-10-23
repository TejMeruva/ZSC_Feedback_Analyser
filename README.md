# Zero Shot Classification Based Feedback Analyser

This is a ramework to get numerical, comparable metrics for abstract information like interest in a particular service (Robotics Workshop in this case). E.g: Interest, Satsifaction, Knowledge Gain etc.

### Background
My client had rolled out 13 google forms for getting feedback from students attending his robotics workshops. The questions from one worksheet were repeated in the next but the method of answering was not consistent. the answer was given as a rating out of 10 in some and as a textual feedback in other. The numebr of form-takers was 872. The large volume of input and the irregular structure of the data made analysis difficult. 

This framework was developed to combine non-numerical and numerical answers to similar but non-identical questions and get a comparable numerical values for a particular metric (say satisfaction with the workshop) to facilitate analysis.

### Process Description.
- 82 unique questions were asked through 13 unique google forms. Multiple questions were assessing the same metric. E.g.: 8 questions assessed interest in robotics before the workshop commenced. 
- such questions were grouped together. 
- Using these sets of questions derived quantities like `interest_before`, `interest_after`, `satisfaction`, `knowledge_gain` were generated. Each category/set of questions was used to generate one derived quantity. The 8 mentioned questions pertaining to assessing interest in robotics before the workshop was used to derive the numerical value of `interest_before`
- depending on the answer (textual or numerical rating out of 10) given to a question belonging to particular category (say interest), the *FaceBook-BART-mnli* LLM was used for *zero-shot-classification* into 2 or more classes (say interested or not interested). In terms of the  `interest_before` example, the prediction confidence of the person being interested is taked as the `interest_before` score. Similarly, for other classes, correspoding prediction scores are used.
- In practice the score is very sensitive to tone and also interjection int eh case of textual feedback

### Advantages 
- both numerical data and textual data could be compared!
- cohesive way to integrate data from multiple incompatible worksheets into a common worksheet for analysis.