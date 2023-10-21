# Transformer-notes
### References:
https://www.youtube.com/watch?v=zxQyTK8quyY
### Word embedding
To convert each word in a sequence to numbers. \
Notes: 
1. Each word uses the same word embedding framework.
2. The weights of each word are randomly generated at first. Then updated by backpropagation.
![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/0582fe22-115c-449d-9f41-415b1d8e8e1a)


### Positional Encoding
Word position comes from Sine and Cosine squiggles.

![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/8f881609-4377-4ccb-a312-b5782eb55eb3)
![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/2c99e430-2d0c-4491-9dac-97ce2b399324)
### Self-Attention
#### Encoder
Encode sequence to numbers with word similarity calculations.\
For each word, the encoding steps follow:
1. Calculate *Query* using positional encoded numbers and $W_q$
2. Calculate *Key* for each word using positional encoded numbers and $W_k$
3. Calcuate similarities for each Key and the Query (eg. dot product similarity)
4. Put dot product similarities through a SoftMax
5. Calculate *Value* for each word using positional encoded numbers
6. Scale Values using SotMax similarities and add them together to get the Self-Attention values for one word (the word generates Query)

The Self-Attention values contain similarities between one word and the other words.\
Notes:\
1. Weights ($W_q, W_k, W_v$)for all words in the input sequence are the same.
2. Transformer can calculate Q,K,V for each word at the same time. (parallel computing)

![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/3bd21ac9-c5c0-4094-93c4-37fd37243742)

![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/1f43bd9a-9ee7-4e52-9f1c-b18484e8daaf)

![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/3acf83b9-974d-47c2-824c-8e5da4e62cf1)

*Conclusion:* \
Transformer encoder has 4 features:
1. Word Embedding: encode words into numbers
2. 


