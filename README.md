
# Deep learning project


## The Socratic questioning

The Socratic questioning or Socratic maieutics is a conversation style used by the philosopher Socrate (470BC-399BC) in the Ancient greek. It is well illustrated in the writings of Plato (428/427BC-348/347BC) such as *Theaetetus*.

In a word, the Socratic questionning can be summarised as birthing of spirits, which means that thanks to questioning, the respondent manages to find truths in himself or herself.

This is what we aim at performing in our project: creating a chatbot which asks questions to the patient just as if Socrat was asking the questions.

Partie brève nlp / nltk

## NLP

Natural Language Processing (NLP) is a field obtained by mixing three disciplines: Linguistics, Computer Science and Artificial Intelligence. It is based on the interaction between machines and human languages. The basis of NLP is thus that the computer understands, manipulates but also generates natural language elements. To do so, the NLTK (which stands for Natural Language Toolkit) library is one of the most powerful ones in Python.

### spaCy

spaCy is a Python library designed for advanced NLP. It is trained for more than 60 languages. It is able to perform all the tasks related to NLP: string reading, sentence detecting, removing stop words, tokenization, lemmatization, Part of Speech tagging (detecting usage of words in a sentence),...

### NER

Our chatbot is based on NER: Named Entity Recognition. NER is the process of Natural Language Processing that identifies and classifies named entities. Basically, the text in natural language is read by the algorithm and this latter classifies elements of the sentences: places, dates, people, organisations, events, quantities,...

The three main methods to perform NER in Python are SpaCy, nltk and Google's NLP API. We chose to use SpaCy because it is the most common one, but still very efficient. SpaCy is trained on a large corpus of texts of several types (news, talk shows, speeches, blogs on the web,...), which is OntoNotes5.0. It thus proves its ability to analyse all kinds of text documents.

## Chatbot

Our chatbot works as follows.

At the beginning of the conversation, the Socratic chatbot introduces itself and asks the patient about him/her current problem. In our view, there can be two types of response:
- a rather vague and general answer, of the grammatical type [subject] [verb of feeling (to be, to feel...)] [adjective]. Example: *I feel sad.*
- a more precise answer directly indicating the reason for the discomfort. Example: *I lost my glasses.*

Our chatbot detects the kind of sentence that the user made. For the first possibility of answer, the chatbot answers to know the exact source of unhappiness. Example: *I lost my glasses*. Once the answer has been obtained, the questioning is therefore at the same level as for the second possible answer.

Then, for both cases, the chatbot asks if it is the first time the patient encounters such a situation, or not.

If the answer is rather positive (*yes* or an equivalent),

If the answer is rather negative (*no* or an equivalent), 

Finally, our chatbot can be summarised as follows.

![Chatbot functionning](https://github.com/helenelechene/Deep-learning-/blob/main/Sch%C3%A9ma%203.png)
