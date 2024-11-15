<H3>ENTER YOUR NAME : Vinush CV</H3>
<H3>ENTER YOUR REGISTER NO. 212222230176</H3>
<H3>EX. NO.7</H3>
<H3>DATE:</H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim: to perform automatic text summarization using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1 :
Import necessary libraries for natural language processing tasks.<BR>
Step 2:
Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3:
Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: 
Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: 
Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
<H3>Program:</H3>

```Python

import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize,sent_tokenize
from nltk.stem import PorterStemmer
nltk.download( 'punkt' )
nltk.download( 'stopwords' )
```

```Python
def preprocess_text(text):
	# Tokenize the text into words
	words = word_tokenize(text)
	# Remove stopwords and punctuation
	stop_words= set(stopwords.words( 'english'))
	filtered_words= [word for word in words if word. lower() not in stop_words and word.isalnum()]

	# Stemming
	stemmer = PorterStemmer()

	stemmed_words= [stemmer. stem(word) for word in filtered_words]
	return stemmed_words
```
```Python
def generate_summary(text,num_sentences=3):

	sentences= sent_tokenize(text)
	preprocessed_text = preprocess_text(text)
	# Calculate the frequency of each word
	word_frequencies =nltk. FreqDist (preprocessed_text)

	# Calculate the score for each sentence based on word frequency
	sentence_scores ={}
	for sentence in sentences:
		for word, freq in word_frequencies.items():
			if word in sentence.lower():
				if sentence not in sentence_scores:
					sentence_scores[sentence] = freq
				else:
					sentence_scores[sentence]+= freq
	# Select top N sentences with highest scores
	summary_sentences= sorted(sentence_scores, key=sentence_scores.get,reverse=True) [ : num_sentences]

	return ' '. join(summary_sentences)
```
```Python
if __name__=="__main__":
	input_text ="""
	Natural language processing (NLP) is a subfield of artificial intelligence.
	It involves the development of algorithms and models that enact NLP.
	NLP is used in various applications, including chatbots, language Understanding, and language generation.
	This program demonstrates a simple text summarization using NLP"""
summary = generate_summary(input_text)
print("Origina1 Text: ")
print (input_text )
print( " \nSummary : " )
print(summary)
```


<H3>Output</H3>

![image](https://github.com/user-attachments/assets/ab504947-255d-43c3-a44a-76c116ce9185)


![image](https://github.com/user-attachments/assets/d0990a7b-5a90-418a-8bad-aba2270986cc)

<H3>Result:</H3>
Thus ,the program to perform the Text summarization is executed sucessfully.


