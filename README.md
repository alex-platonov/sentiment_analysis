# Sentiment analysis of the stock - related news articles and its effect on the next day price variation.

## 1. (Quasi) Scientific goal 
This personal project's ultimate goal is to explore the possibility of sentiment analysis usage in live stock market price variation prediction.


## 2. The honorable guinea pig
Flowing the release of the new Vision PRO VR headset Apple Inc. has received an increased amount of media attention and coverage. With this in mind APPL stock will be used for this experiment. Moreover, historically AAPL has demonstrated some drastic volatility thus making it quite representative from both statistical and descriptive perspective.

## 3. Exercise in un-automated pipeline construction
A semblance of a pipeline will be constructed to accommodate the process from start to finish. 

### Gathering of data
In order to collect enough data for analysis we will be scraping uk.investing.com - one of the most reputable source of financial information. Moreover, its EULA is quite forgiving to web-scraping. 
NB: Please be aware that not all recourses are that forgiving (e.g. Bloomberg). Before using this approach for you r project - please be sure to undertake a conscious effort to read the EULA to make sure it allows such activity. 

### Text preprocessing and classification
A number of steps need to be taken before the text is deemed ready for NLP processing, namely: text cleaning and preparation. 
- Normalization: the scraped text corpus needs to be transformed into a canonical standard text in order to reduce noise;
- Classification:  (aka assigning categories to text data according to its content). We are going to explore the following techniques to extract information from raw text data for training a classification model: 
	- Bag of Words; 
	- TF-IDF; 
	- Word Embedding.

### Topic modelling
Topic modelling - use of a quantitative algorithm to automatically derive the key topics that a body of text is about. One of the primary tasks of NLP is to cut through the noise (high dimensionality from large volumes of text) and identify the signal (extract the main topics). In this case Latent Dirichlet Allocation (LDA) algorithm will be used. 

### BERT long text analysis
BERT (Bidirectional Encoder Representations from Transformers) is a transfer learning technique for NLP developed by Google, a deeply bidirectional, unsupervised and contextual language representation, pre-trained using only a plain text corpus. 

For the supervised sentiment classification as positive (1) or negative (0) a pre-trained BERT model will be finetuned to give outputs for classification using the `BertForSequenceClassification` class. This adds a single untrained linear layer on top of the pooled output so that, as  data is added, the pre-trained BERT model and the additional untrained classification layer is trained on the article sentiment classification task.

### Sentiment analysis
A selection of machine learning classifier models will be used to predict whether the next day ACP (Adjusted Close price) of Apple stock will increase or decrease based on sentiment analysis of market news articles from 2014-2024 collected by web scraping from uk.investing.com.
