# Sentence-Similarity

 I have used 2 approaches, The first being finding similarity based on the Word2Vec feaatures. For that I have used word mover distance , cosine similarity and some other diatance metrics.You can see there results in the notebook named `Word2Vec Features using Gensim.ipynb`.

Clearly we can see that the model predicted similarity between the sentence `I am going to India` and `I am going to bharat` is less than that of the sentences `I will be eating coffee` and `I will be drinking coffee`. But the reality is that first pair of sentence is identical and the second pair is quient  different in terms of semantic understanding. This is a problem due the the way word2vec model is trained. Its trained using negative sampling on an English Corpora which rarely has the word `bharat`. Basically Word2Vec converts every word into a 300 dimensional representation in the vector space. The problem is although `drinking` and `eating` means different things but they have certain similar features like related to food,etc. The word `bharat` is treated as an 'UNK' labeled word i.e. its treated as unknown. So the Word2Vec model is not able to capture the synonymous meaning of `bharat` to  `India`. So the similarity in the first pair of sentence is less than the second pair.

Another Approach that I have used is a model that I trained for one of my projects `Quora Question Similarity`.For this I extracted around 30 features from the sentence pair and vectorized it as a reresentation of the pair of sentences.After this I predicted the similarity of the sentence. My trined model was a binary classification problem so it predicts `1` if similar and `0` if different. This model was trained on quora question pair dataset from kaggle.This model also used word2vec for certain features son the prediction of this model also remains the same as that of the previous approach.The same reason that I stated above  can be attributed to this wronfg prediction.The files are as follows:

- `Quora Question Pair.ipynb` --- Feature Extraction Pipeline
- `Model Training.ipynb ` --- Training Pipeline
- ` Testing Model.ipynb` --- Testing Pipeline on the given sentences 

