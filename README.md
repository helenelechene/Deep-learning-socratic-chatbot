
# Deep learning project - A Socratic chatbot 

## Hélène LECHÊNE and Romane SOLER 


## 1. The Socratic questioning

The Socratic questioning or Socratic maieutics is a conversation style used by the philosopher Socrates (470BC-399BC) in the Ancient greek. It is well illustrated in the writings of Plato (428/427BC-348/347BC), Socrates' student, such as *Gorgias*.

In a word, the Socratic questionning can be summarised as birthing of spirits, which means that thanks to questioning, the respondent manages to find truths in himself or herself by himself or herself. Socrates will not directly give the answer to a question, but will ask proper questions that will allow the interlocutor to find the answer by himself or helself. 

For example in that extract of *Gorgias*, we see that Socrates hardly asserts anything but rather makes Gorgias question himself about his beliefs:

![Conversation 1](https://github.com/helenelechene/Deep-learning-/blob/main/Image/gorgias.png)

This is what we aim at performing in our project: creating a chatbot which asks questions to somebody just as if Socrates were asking the questions.


## 2. NLP and packages

Natural Language Processing (NLP) is a field obtained by mixing three disciplines: Linguistics, Computer Science and Artificial Intelligence. It is based on the interaction between machines and human languages. The basis of NLP is thus that the computer understands, manipulates but also generates natural language elements. To do so, the NLTK (which stands for Natural Language Toolkit) library is one of the most powerful ones in Python.

### 2.1. NER

Our chatbot is based on NER: Named Entity Recognition. NER is the process of Natural Language Processing that identifies and classifies named entities. Basically, the text in natural language is read by the algorithm and this latter classifies elements of the sentences: places, dates, people, organisations, events, quantities... Or more specifically in the context of our project, grammatical elements such as verb, noun, adjective etc.


### 2.2. spaCy library

spaCy is a Python library designed for advanced NLP. It is trained for more than 60 languages. It is able to perform all the tasks related to NLP: string reading, sentence detecting, removing stop words, tokenization, lemmatization, Part of Speech tagging (detecting usage of words in a sentence),...


The three main methods to perform NER in Python are SpaCy, nltk and Google's NLP API. We chose to use SpaCy because it is the most common one, but still very efficient. SpaCy is trained on a large corpus of texts of several types (news, talk shows, speeches, blogs on the web,...), which is OntoNotes5.0. It thus proves its ability to analyse all kinds of text documents.

### 2.3. pattern library

Pattern is another Python NLP library. From our experience throughout this project, it works well and it is simple to use for grammatical purposes, making conjugation as well as determining the grammatical person and number (singular or plural) of words. Also from our experience, it is not really efficient for doing sentiment analysis on small sentences (without modelling and optimizing, using only the function 'sentiment').  

## 3. Chatbot

A chatbot try to reproduce a conversation between humans. The aim of chatbot is usually to appear as humanly as possible, in other words, to try to pass the Turing test. A simple form of chatbot is Artificial Intelligence Markup Language (AIML) that is based on pattern and templates, the pattern is the usual form of the question and the template the proper answer to this question. Thus, a chatbot relies largely on NLP.

### 3.1. Building the questions ###

In our chabtot the main issue was to transform affirmative sentences into questions. For simplicity's sake, our chatbot, or Socrate, only asks indirect questions:

*- User : I am sad* 

*- Socrate: Could you think of any reason why you are sad ?* 

Thus, the main issue is to **conjugate the verb** and to **transforms the subject as well as the pronouns** (*I* becomes *you*, *my* becomes *your*...). Our chatbot speaks in English (not in Greek hopefully) and it is relatively easy to conjugate in English. 

We have used two methods to convert our affirmation into questions:

- For the pronouns and the nouns: we have replaced all pronouns and nouns we could think about by directly changing the string that the user typed. Basically, we had to change all pronouns and nouns of the 1st person to the 2nd person. 

- For the conjugation, we used NER. Indeed, we wanted to change the tense of the verb in order to ask the following question: 

*- User : I broke my car* 

*- Socrate: Is it the first time you break your car ?* 

Thus, we had to find the subject as well as the verb. Thank to spaCy and NER, we could identify easily the verbs. The subject was more difficult to identify, especially when there are two subjects in the sentence ex: *User : I broke my computer and my parents are mad*. We defined the subject as the first world before the verb (gerund (-ing) and past participle forms are not considered as verbs here). Then, we conjugate the verbs using the present tense thanks to the function 'conjugate' from the library 'pattern'. If the subject is "I" or plural, we conjugate the verb at the second person, otherwise, we conjugate the verb at the third person.


Finally, our chatbot can be summarised as follows.

![Chatbot](https://github.com/helenelechene/Deep-learning-/blob/main/Image/tree.png)


Here are some examples of conversations between a user and Socrate using our algorithm:


![Conversation 1](https://github.com/helenelechene/Deep-learning-/blob/main/Image/ex1.png)

![Conversation 2](https://github.com/helenelechene/Deep-learning-/blob/main/Image/ex2.png)

![Conversation 3](https://github.com/helenelechene/Deep-learning-/blob/main/Image/ex3.png)

## References

1. Moppel J., Bachelor's thesis: Socratic chatbot, University of Tartu, (2018).
2. https://github.com/janmoppel/socratic-chatbot/tree/master/SocraticChatbot
3. https://towardsdatascience.com/how-to-build-your-own-chatbot-using-deep-learning-bb41f970e281
4. https://spacy.io
5. https://stackabuse.com/python-for-nlp-introduction-to-the-pattern-library/
6. https://www.nltk.org/
