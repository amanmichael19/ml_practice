# Machine Learning Practice

This repo contains [Jupyter](http://jupyter.org) notebooks for machine learning practice. Our overall goal is to learn how to use [`xgboost`](https://xgboost.readthedocs.io/en/latest/) to classify high vs low ratings and predict the actual ratings using the text plus any additional features (e.g., [fleishman-kincaid index](https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests), number of words) that we might want to add to the features.

## Getting Started

### 1. Clone the Repo

```sh
$ git clone https://github.com/coetic/machine-learning-practice
```

### 2. Install Anaconda/Jupyter

Follow [this link](http://jupyter.org/install) for instructions on installing Anaconda/Jupyter.

*Check out [this article](https://medium.com/codingthesmartway-com-blog/getting-started-with-jupyter-notebook-for-python-4e7082bd5d46) for getting started with Jupyter notebooks for Python.*

### 3. Run the Notebook

Run the following command to start a Jupyter notebook server locally (do this in the directory of the repository):

```sh
$ jupyter notebook
```

## Data

The practice data we're using is the [Amazon fine food reviews]() dataset which is located in the CoeticHR public S3 bucket at https://s3.amazonaws.com/coetichr/AmazonFoodReviews.

This folder contains the following files:

- `Reviews.csv`
- `database.sqlite`
- `hashes.txt`

The `Reviews.csv` file is in the following format

| ProductId | UserId | ProfileName | HelpfulnessNumerator | HelpfulnessDenominator | Score | Time | Summary | Text |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|

Since the data is too large to be committed to the repository, download it from the S3 bucket and place it in the `data` folder in your local repository version which is ignored by Git. The files can also be requested directly from S3 but will take slightly longer.

In the `scripts/amazon_food_reviews.ipynb` script, make the following change to use the remote version instead:

```py
DATA_LOCAL = False
```

## nltk

We're going to use the [`nltk`](https://www.nltk.org/) (Natural Language Toolkit) library to form a tokenized corpus of words. These are some standard settings that work well for `nltk`:

```py
tfv = TfidfVectorizer(min_df=3, max_features=None, strip_accents='unicode', analyzer='word', token_pattern=r'\w{1,}', ngram_range=(1,3), use_idf=1, smooth_idf=1, sublinear_tf=1, stop_words='english')
```

## Resources

- [Natural Language Processing Flowchart](https://developers.google.com/machine-learning/guides/text-classification/step-2-5)
- [Scikit-Learn for Text Analysis of Amazon Fine Food Reviews](https://datascienceplus.com/scikit-learn-for-text-analysis-of-amazon-fine-food-reviews/)
- [Exploratory visualization of Amazon fine food reviews](https://nycdatascience.com/blog/student-works/amazon-fine-foods-visualization/)
- [A Comprehensive Guide to Understand and Implement Text Classification in Python](https://www.analyticsvidhya.com/blog/2018/04/a-comprehensive-guide-to-understand-and-implement-text-classification-in-python/)
- [Metrics To Evaluate Machine Learning Algorithms in Python](https://machinelearningmastery.com/metrics-evaluate-machine-learning-algorithms-python/)
- [Story and Lessons Behind the Evolution of xgboost](https://homes.cs.washington.edu/~tqchen/2016/03/10/story-and-lessons-behind-the-evolution-of-xgboost.html)
- [Using xgboost in Python](https://www.datacamp.com/community/tutorials/xgboost-in-python)
- [xgboost oh GitHub](https://github.com/dmlc/xgboost)
- [Gradient Boosting](https://en.wikipedia.org/wiki/Gradient_boosting)
- [A Review of the Neural History of Natural Language Processing](http://blog.aylien.com/a-review-of-the-recent-history-of-natural-language-processing/#2018pretrainedlanguagemodels)
- [Pandas](https://pandas.pydata.org/)
- [Flesh-Kincaid readability tests](https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests)
