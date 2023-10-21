# Transformer-notes
### References:
https://www.youtube.com/watch?v=zxQyTK8quyY
### Word embedding
To convert each word in a sequence to numbers. \
Notes: 
1. Each word uses the same word embedding framework.
2. The weights of each word are randomly generated at first. Then updated by backpropagation.
![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/beb20816-9407-4081-a8b1-36a8112646e6)


### Positional Encoding
Word position comes from Sine and Cosine squiggles.


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



*Conclusion:* \
Transformer encoder has 4 features:
1. Word Embedding: encode words into numbers
2. 


