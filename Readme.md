# Background

When the Conversation AI team first built toxicity models, they found that the models incorrectly learned to associate the names of frequently attacked identities with toxicity. Models predicted a high likelihood of toxicity for comments containing those identities (e.g. "gay"), even when those comments were not actually toxic (such as "I am a gay woman"). This happens because training data was pulled from available sources where unfortunately, certain identities are overwhelmingly referred to in offensive ways. Training a model from data with these imbalances risks simply mirroring those biases back to users.

In this competition, we were challenged to build a model that recognizes toxicity and minimizes this type of unintended bias with respect to mentions of identities. You'll be using a dataset labeled for identity mentions and optimizing a metric designed to measure unintended bias. Develop strategies to reduce unintended bias in machine learning models, and you'll help the Conversation AI team, and the entire industry, build models that work well for a wide range of conversations.

Disclaimer: The dataset for this competition contains text that may be considered profane, vulgar, or offensive.

## Data

In the data supplied for this competition, the text of the individual comment is found in the `comment_text` column. You can find the dataset [here](https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/data) Each comment in Train has a toxicity label (`target`), and models should predict the `target` toxicity for the Test data. This attribute (and all others) are fractional values which represent the fraction of human raters who believed the attribute applied to the given comment. For evaluation, test set examples with `target >= 0.5` are considered to be in the positive class (toxic).

The data also has several additional toxicity subtype attributes. Models do not need to predict these attributes for the competition, they are included as an additional avenue for research. Subtype attributes are:

- severe_toxicity
- obscene
- threat
- insult
- identity_attack
- sexual_explicit

Additionally, a subset of comments have been labelled with a variety of identity attributes, representing the identities that are mentioned in the comment. The identites that are used for evaluation is given below

- male
- female
- homosexual_gay_or_lesbian
- christian
- jewish
- muslim
- black
- white
- psychiatric_or_mental_illness

More about the data can be found [here](https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/data).

## Evaluation

To know more about evaluation refer [here](https://arxiv.org/abs/1903.04561) and [here](https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/overview/evaluation)

## Approach

The data was divided into 5 folds and on each fold , Bert cased, uncased and open ai gpt2 models were trained with each `comment_text` that are tokenized with `maximum_length = 250`. open ai gpt2 models were not used in the final blend and the best submission was weighted blend of bert cased and bert uncased. My team got 89th position out of 2646 teams in the competition. The scores of some models are recorded in the file `jigsaw models scores.xlsx`.
The weights for the final blend are `0.6` for bert uncased and `0.4` for bert cased.
