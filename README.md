# amWRit

# CS50AI 2020
## Week 6 (Language) || Parser

Developed upon the original distro code provided by CS50AI team.

### Parser

Write an AI to parse sentences and extract noun phrases.
````
$ python parser.py
Sentence: Holmes sat.
        S
   _____|___
  NP        VP
  |         |
  N         V
  |         |
holmes     sat

Noun Phrase Chunks
holmes
````

#### Background
A common task in natural language processing is parsing, the process of determining the structure of a sentence. This is useful for a number of reasons: knowing the structure of a sentence can help a computer to better understand the meaning of the sentence, and it can also help the computer extract information out of a sentence. In particular, it’s often useful to extract noun phrases out of a sentence to get an understanding for what the sentence is about.

In this problem, we’ll use the context-free grammar formalism to parse English sentences to determine their structure. Recall that in a context-free grammar, we repeatedly apply rewriting rules to transform symbols into other symbols. The objective is to start with a nonterminal symbol S (representing a sentence) and repeatedly apply context-free grammar rules until we generate a complete sentence of terminal symbols (i.e., words). The rule S -> N V, for example, means that the S symbol can be rewritten as N V (a noun followed by a verb). If we also have the rule N -> "Holmes" and the rule V -> "sat", we can generate the complete sentence "Holmes sat.".

Of course, noun phrases might not always be as simple as a single word like "Holmes". We might have noun phrases like "my companion" or "a country walk" or "the day before Thursday", which require more complex rules to account for. To account for the phrase "my companion", for example, we might imagine a rule like:

NP -> N | Det N
In this rule, we say that an NP (a “noun phrase”) could be either just a noun (N) or a determiner (Det) followed by a noun, where determiners include words like "a", "the", and "my". The vertical bar (|) just indicates that there are multiple possible ways to rewrite an NP, with each possible rewrite separated by a bar.

To incorporate this rule into how we parse a sentence (S), we’ll also need to modify our S -> N V rule to allow for noun phrases (NPs) as the subject of our sentence. See how? And to account for more complex types of noun phrases, we may need to modify our grammar even further.

#### Output
````
$ python parser.py sentences/10.txt

              S
  ____________|______________________
 |                                   VP
 |    _______________________________|____
 |   |                                    NP
 |   |                          __________|____________________
 |   |                         NP                              |
 |   |                _________|______________                 |
 |   |               NP                       |                |
 |   |    ___________|_______________         |                |
 |   |   |          AdjP             |        |                |
 |   |   |     ______|____           |        |                |
 |   |   |    |          AdjP        |        PP               PP
 |   |   |    |       ____|____      |     ___|___          ___|___
 NP  |   |    |      |        AdjP   |    |       NP       |       NP
 |   |   |    |      |         |     |    |    ___|___     |    ___|___
 N   V  Det  Adj    Adj       Adj    N    P  Det      N    P  Det      N
 |   |   |    |      |         |     |    |   |       |    |   |       |
 i  had  a  little moist      red  paint  in the     palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
the palm
my hand
              S
  ____________|______________________
 |                                   VP
 |    _______________________________|____
 |   |                                    NP
 |   |                ____________________|___________
 |   |               NP                               PP
 |   |    ___________|_______________      ___________|____
 |   |   |          AdjP             |    |                NP
 |   |   |     ______|____           |    |        ________|___
 |   |   |    |          AdjP        |    |       |            PP
 |   |   |    |       ____|____      |    |       |         ___|___
 NP  |   |    |      |        AdjP   |    |       NP       |       NP
 |   |   |    |      |         |     |    |    ___|___     |    ___|___
 N   V  Det  Adj    Adj       Adj    N    P  Det      N    P  Det      N
 |   |   |    |      |         |     |    |   |       |    |   |       |
 i  had  a  little moist      red  paint  in the     palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
the palm
my hand
````

#### Keywords
````
Language
Natural Language Processing (NLP)
Syntax and Semantics
Context Free Grammar (CFG)
Formal Grammar
nltk
n-grams
Tokenization
Markov Models
Bag-of-Words Model
Naive Bayes
Information Retrieval
tf-idf (Term Frequency - Inverse Document Frequency)
Word Net
Word Representation
word2vec


````

#### References
````
https://cs50.harvard.edu/ai/2020/notes/6/
https://stackoverflow.com/a/29423080
http://www.nltk.org/api/nltk.html#nltk.tree.ParentedTree
http://www.tfidf.com/#:~:text=Example%3A,in%20one%20thousand%20of%20these.
````
