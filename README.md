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
![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/835ba892-7d29-40d9-8e51-d04e1a2d8712)

### Self-Attention
#### Encoder
Encode sequence to numbers with word similarity calculations.\
For **each word**, the encoding steps follow:
1. Calculate *Query* using positional encoded numbers and $W_q$
2. Calculate *Key* for each word using positional encoded numbers and $W_k$
3. Calcuate similarities for each Key and the Query (eg. dot product similarity)
4. Put dot product similarities through a SoftMax
5. Calculate *Value* for each word using positional encoded numbers
6. Scale Values using SotMax similarities and add them together to get the Self-Attention values for one word (the word generates Query)


The Self-Attention values contain similarities between one word and the other words.\
Notes:
1. Weights ($W_q, W_k, W_v$)for all words in the input sequence are the same.
2. Transformer can calculate Q,K,V for each word at the same time. (parallel computing)

![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/ae173a46-3709-4787-9c58-331827b7da8e)

After calculating self-attention values of tokens, add the word and position encoded values to self-attention values to get the residual connection values.

![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/dbbde7e6-150d-4f6d-81b5-937d0022e9c4)

*Conclusion:* \
Transformer encoder has 4 features:
1. Word Embedding: encode words into numbers
2. Positional Encoding: encode the positions of the words
3. Self-Attention: encode the relationships among the words

#### Decoder
Use the <EOS> token as an example. Usually, we use the <EOS> token to start the decoding. 
1. word embedding for the <EOS> token
   Create embedding values from the output vocabulary. eg. Spanish words.
   
 ![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/74c13519-b8be-4e51-89ab-bb21a7f0f9fb)

2. positional encoding for the <EOS> token
   use the same sine and cosine squiggles used when encoding the input.
   ![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/77ef0515-18ba-400a-a8fc-12fb8a5529a0)

3. calculate the self-attention values for the <EOS> token
   Calculate the Query, Key, Value for the <EOS> token. Then calculate the Self-Attention values like before.
   Note：The sets of weights ($W_q, W_k, W_v$) are different from weights in the Encoder.
   ![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/6b39ebc0-e360-4952-8b37-835707c19717)

4. add Residual Connections\
from step 5-10, we are calculating the Encoder-Decoder Attention values.\
5. calculate the Query for the residual connection values (<EOS> token)
6. use the residual connections in encoder to generate keys. one key for each token.
7. calculate the dot similarities using the query and the keys.
8. put the similarity through a softmax function
![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/5f6a3f58-d3c7-4293-836a-c5bfcb1e03a9)

9. calculate values for encoder residual connections.
10. scale values using softmax output to get the encoder-decoder attention values.
![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/e370a6fb-583b-47dc-b288-e8c9750f38c0)

11. add residual connections
    ![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/45f8a74d-517d-41ee-9db2-ddcf072055ac)

12. pass the residual connections values through a fully connected layer, then use the output of the FFN network to select words from the output vocabulary. 
    ![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/6809bba3-bcf8-41a0-916e-a124e3e3e2b2)

13. now we get our first translated word 'vamos'. Then plug 'vamos' into a copy of the decoding layer.
14. Repeat the above steps until it outputs a <EOS> token.
![image](https://github.com/YummyPancake/Transformer-notes/assets/50786300/44e5ea38-4559-4c53-924d-b1f9be5921e8)

### Something that you can add to transformer
1. layer normalization
2. use other methods to calculate similarities in attention layers.
   for example, you can scale the dot-product: $ similarity=/frac{dot_product}{/sqrt(# embedding_values)}$
