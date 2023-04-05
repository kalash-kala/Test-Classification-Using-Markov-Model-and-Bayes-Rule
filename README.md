# Text Classification Using Markov Model and Bayes Decision Rule

### Introduction :

This project is about creating a basic text classification program which doesn’t use any inbuilt functions from libraries like scikit learn. Rather, we have used the concept of Markov Model and Bayes Rule and created the model from scratch.

### What are Markov Processes :

- The processes which follow this Markov property are called Markov Process
- The Markov Property states that the probability of the current event only depends on the probability of the preceding timestamp
- Markov property in mathematical terms means the following :
    
    ![Screenshot 2023-04-01 at 2.47.52 PM.png](Text%20Classification%20Using%20Markov%20Model%20and%20Bayes%20D%203fe8816ce7714941aee4fa78916a9f1d/Screenshot_2023-04-01_at_2.47.52_PM.png)
    

### Is it correct to assume Markov Property in sequence of textual data :

NO !! logically it is incorrect to assume this property as this property states that the current word is only dependent on the word that is just preceding to the current one, but in reality the current word depends upon the context produced by all the words that come before it. 

### So why do we assume it :

- It makes the computation much faster, lighter and simpler
- Easier to code and the outcome serves the purpose, even if it is not the optimal solution

### Process :

1. Create a DataFrame containing the text and corresponding class labels
2. Clean the text by removing empty texts, ‘\n’ character, punctuations and make the entire text lower case
3. Do a train test split on this data
4. Create a vocabulary using the text present in the training set irrespective of which class they belong to
    1. Basically create a word to index mapping for all the unique words in the training set
    2. Store the total number of unique words = total_states
5. Create State transition matrix and initial state distribution for all the classes :
    1. State transition matrix size will be $total\_states\times total\_states$
    2. Initial State Distribution array size will be $total\_states$
6. Create a function to fill the above matrices and arrays
7. Apply probability smoothing on the values of the arrays and matrices, and then take log probabilities of these values (check notebook for better understanding)
    
    ![Screenshot 2023-04-01 at 7.55.25 PM.png](Text%20Classification%20Using%20Markov%20Model%20and%20Bayes%20D%203fe8816ce7714941aee4fa78916a9f1d/Screenshot_2023-04-01_at_7.55.25_PM.png)
    
8. Calculate prior log probabilities of the classes
9. Using Markov property create an evaluate function which uses Bayes Decision Rule
10. Apply it on the test data and use metrics like F1 score to gauge the performance

### So is this project based on supervised learning or unsupervised ?

- Classification problem is a supervised learning problem and we also have labeled data
- But creating a markov model is an unsupervised method, we are basically creating a vocabulary using all the words in the corpus without caring about which class it belongs to
- So how are are we solving a supervised learning problem using Unsupervised learning ? The answer lies in Bayes Rule