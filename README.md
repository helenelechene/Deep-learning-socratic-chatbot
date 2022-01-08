
# Deep learning project - A Socratic chatbot 

## Hélène LECHÊNE and Romane SOLER 


## 1. The Socratic questioning

The Socratic questioning or Socratic maieutics is a conversation style used by the philosopher Socrates (470BC-399BC) in the Ancient greek. It is well illustrated in the writings of Plato (428/427BC-348/347BC) such as *Theaetetus*.

In a word, the Socratic questionning can be summarised as birthing of spirits, which means that thanks to questioning, the respondent manages to find truths in himself or herself by himself or herself.

This is what we aim at performing in our project: creating a chatbot which asks questions to the patient just as if Socrat was asking the questions.

Partie brève nlp / nltk

## 2. NLP

Natural Language Processing (NLP) is a field obtained by mixing three disciplines: Linguistics, Computer Science and Artificial Intelligence. It is based on the interaction between machines and human languages. The basis of NLP is thus that the computer understands, manipulates but also generates natural language elements. To do so, the NLTK (which stands for Natural Language Toolkit) library is one of the most powerful ones in Python.

### 2.1. NER

Our chatbot is based on NER: Named Entity Recognition. NER is the process of Natural Language Processing that identifies and classifies named entities. Basically, the text in natural language is read by the algorithm and this latter classifies elements of the sentences: places, dates, people, organisations, events, quantities... But more specifically grammatical elements: verb, noun, adjective....


### 2.2. spaCy

spaCy is a Python library designed for advanced NLP. It is trained for more than 60 languages. It is able to perform all the tasks related to NLP: string reading, sentence detecting, removing stop words, tokenization, lemmatization, Part of Speech tagging (detecting usage of words in a sentence),...


The three main methods to perform NER in Python are SpaCy, nltk and Google's NLP API. We chose to use SpaCy because it is the most common one, but still very efficient. SpaCy is trained on a large corpus of texts of several types (news, talk shows, speeches, blogs on the web,...), which is OntoNotes5.0. It thus proves its ability to analyse all kinds of text documents.

## 3. Chatbot

### 3.1. Building the questions ###

In our chabtot the main issue was to transform affirmative sentences into questions. For simplicity's sake, our chatbot, or Socrate, only asks indirect questions:

*- User : I am sad* 

*- Socrate: Could you think of any reason why you are sad ?* 

Thus, the main issue is **conjugate the verb** and to **transform the subject as well as the pronoun** (*I* becomes *you*, *my* becomes *your*...). Our chatbot speaks in English (not in Greek hopefully) and it is relatively easy to conjugate in English. 

We have used two methods to convert our affirmation into questions:

- For the pronouns and the nouns: we have replaced all pronouns and nouns we could think about by directly changing the string that the user typed. Basically, we had to change all pronouns and nouns of the 1st person to the 2nd person. 

- For the conjugation, we used NER. Indeed, we wanted to change the tense of the verb in order to ask the following question: 

*- User : I broke my car* 

*- Socrate: Is it the first time you break your car ?* 

Thus, we had to find the subject as well as the verb. Thank to spaCy and NER, we could identify easily the verbs. The subject was more difficult to identify, especially when there are two subjects in the sentence ex: *User : I broke my computer and my parents are mad*. We defined the subject as the first world before the verb (a -ing form and non past participle form is not considered as a verb here). Then we conjugate the verbs using the present tense.


Finally, our chatbot can be summarised as follows.

![Chatbot](https://github.com/helenelechene/Deep-learning-/blob/main/Image/tree.png)


Here are some examples of conversations between a user and Socrate:


![Conversation 1](https://github.com/helenelechene/Deep-learning-/blob/main/Image/ex1.png)

![Conversation 2](https://github.com/helenelechene/Deep-learning-/blob/main/Image/ex2.png)

![Conversation 3](https://github.com/helenelechene/Deep-learning-/blob/main/Image/ex3.png)
