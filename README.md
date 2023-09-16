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
1. Calculate Query using 

