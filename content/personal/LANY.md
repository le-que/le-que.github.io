+++
title = "Lany Song Analysis"
date = "2023-12-24"
tags = [
    "python",
    "machine-learning",
]
+++
This project focuses on analyzing Lany songs using various natural language processing (NLP) and machine learning (ML) techniques.
<!--more-->
**[code](https://github.com/le-que/LANY-EDA-Song-Generator/blob/main/README.md)**

### Markov.ipynb - Markov Chain-based Text Generator
This notebook implements a text generator using a Markov Chain model. It utilizes a probabilistic model to predict the next word in a sequence based on the previous words.

```python
generate_property = Markov(corpus= ' '.join(df))
generate_property.gen_song(lines=5, length_range=[5, 15])
```
```markdown
"time you realized you're the only way to get past this feeling is to tell when everything \n don't know with who i'm sorry i get jealous or if i got \n no more no more be right back i'm gonna go can't take it back is it \n do is let you in the midst of your insecure winds breakin' us down \n your mind i can't promise you that i'll be next week or we could"
```
```python
generate_property.gen_song(lines=5, length_range=[5, 15], startswith='love you')
```
```markdown
"need her i know you're out the door every time \n your loss i really mean it and whatever we \n voice sorry for the nights when i kiss your lips i hope you always regret and i \n it in 'cause i've been on the line \n the bone but sometimes you just tell me where we should talk about"
```
### Next_Word_Prediction.ipynb - LSTM-based Next Word Prediction
This notebook employs a sequential model for next word prediction using deep learning. The model architecture includes an Embedding layer, an LSTM layer, and a Dense layer with softmax activation. It is trained on a dataset created from Lany song lyrics.

```python  
seed_text = "Up all night on my mind got me thinking "
next_words = 8

for _ in range(next_words):
    token_list = tokenizer.texts_to_sequences([seed_text])[0]
    token_list = pad_sequences(
        [token_list], maxlen=max_sequence_len-1, padding='pre')
    predicted_probs = model.predict(token_list)
    predicted_word = tokenizer.index_word[np.argmax(predicted_probs)]
    seed_text += " " + predicted_word

print("Next predicted words:", seed_text)
```
```markdown
Next predicted words: Up all night on my mind got me thinking  the own phone is quiet walls town bare
```
![static](/img/acc.png)
![static](/img/loss.png)

### Sentiment.ipynb - Sentiment Analysis and EDA
This notebook focuses on analyzing the sentiment of each song's lyrics and performing feature engineering to extract meaningful insights. Sentiment scores are computed for each song. Various features are engineered to enhance the understanding of the lyrical content including: # of words, num of lines, average Word Length Per Line, num of uniq_words, lexical_density, views per album.

![static](/img/coord.svg)

![static](/img/hist.svg)

![static](/img/common.svg)

![static](/img/LongerCommon.svg)

![static](/img/2word.svg)

![static](/img/3word.svg)

![static](/img/numSong.svg)

![static](/img/verses.svg)

![static](/img/chorus.svg)

![static](/img/AlbCnV.svg)

![static](/img/AlbViews.svg)

![static](/img/AlbWord.svg)










