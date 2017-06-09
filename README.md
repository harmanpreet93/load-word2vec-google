## Load Google's pre-trained Word2Vec model using gensim

This repo describes how to load Google's pre-trained Word2Vec model and play with them using gensim. 

Before we start, download word2vec pre-trained vectors published by Google from [here](https://drive.google.com/file/d/0B7XkCwpI5KDYNlNUTTlSS21pQmM/edit?usp=sharing). It’s 1.5GB!

The published pre-trained vectors are trained on part of Google News dataset on about 100 billion words. The model contains 300-dimensional vectors for about 3 million words and phrases. 

#### Loading model using gensim
```
path = 'path/to/GoogleNews-vectors-negative300.bin.gz'
model = KeyedVectors.load_word2vec_format(path, binary=True)
```

Limit model size while loading
```
model = KeyedVectors.load_word2vec_format(path, binary=True, limit=20000)
```

Word2Vec supports several word similarity tasks out of the box:
```
model.most_similar(positive=['woman', 'king'], negative=['man'], topn=1)
[('queen', 0.50882536)]
model.doesnt_match("breakfast cereal dinner lunch";.split())
'cereal'
model.similarity('woman', 'man')
0.73723527
```
