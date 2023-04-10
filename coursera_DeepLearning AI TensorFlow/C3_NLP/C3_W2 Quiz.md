# Question 1
What is the purpose of the embedding dimension?

* It is the number of letters in the word, denoting the size of the encoding
* It is the number of words to encode in the embedding
* It is the number of dimensions required to encode every word in the corpus
* ~~It is the number of dimensions for the vector representing the word encoding~~

# Question 2
When tokenizing a corpus, what does the num_words=n parameter do?

* ~~It specifies the maximum number of words to be tokenized, and picks the most common ‘n-1’ words~~
  * 토근화할 최대 단어 수를 지정하고 가장 일반적인 'n-1' 단어를 선택합니다.
* It errors out if there are more than n distinct words in the corpus
* It specifies the maximum number of words to be tokenized, and picks the first ‘n’ words that were tokenized
* It specifies the maximum number of words to be tokenized, and stops tokenizing when it reaches n

# Question 3
When using IMDB Sub Words dataset, our results in classification were poor. Why?

* We didn’t train long enough
* ~~Sequence becomes much more important when dealing with subwords, but we’re ignoring word positions~~
  * Sequence 하위 단어를 다룰 때 훨씬 더 중요하지만 단어 위치를 무시하고 있습니다.
* Our neural network didn’t have enough layers
* The sub words make no sense, so can’t be classified
