# Intro

## Ngram models

N-gram models are simple probabilistic language models that generate words by selecting a new word from the last N-1 words of the sentence using the calculated conditional probability:

p(w(n) | w1 w2 .... w(n-1)) = p(w1 w2 ... w(n))/p(w1 w2 .... w(n-1)).

In layman terms, using the probability of a word being the nth word, given the previous n-1 words.

This means that the model chooses what word to generate based on the memory of the last N-1 words and its knowledge of all the words that can exist given these N-1 words exist before it in order and what is the probability of them existing in that order.

This knowledge of the n-gram model is achieved by modeling from the [Reuters](https://www.cs.bgu.ac.il/~elhadad/nlp19/ReutersDataset.html) dataset. The Reuters dataset is a Corpus contains 10,788 news documents totaling 1.3 million words.

## The trigram model

The trigram model as the name suggests generates a third word based on the memory of the last two words. The trigram model suffers from the extreme case of the disagvantage that all ngrams suffer, It doesnot have suffitient memory of the past words. All its decisions are made based on only the last two words but when it comes to human language this behaviour is far from the truth.

#### feed: "its name"

output: 

its name to allegis at its annual report . the company said . the company said . the company said .

#### feed: "The name"

output:

the name of company is not a very serious about negotiating until the end of the company said . the company said . the company said

### conclution:

We can clearly notice that the trigram model suffers to make any sence due to the limited memory of the past. The trigram also suffers from repetition because the two "words" : *"."* and *"the"* point to the next word being *"company"* then, *"the"* and *"company"* point to the next word being *"said"*, *"company"* and *"said"* ponit to *"."* but again, finishing the loop, *"said"* and *"."* point to *"the"*.

This bug can be easily removed by selecting a word randomly out of the pool of most probable 5 or 10 words instead of going to THE most probable. Or even selecting a word from a pool of words that all have probabilities more than x (x can be determined by trial and error) and if there is no word that satisfies this condition we can take this point as a good end point for the news.

## The pentagram model:

#### feed: "the future of the"

output:

the future of the industry which diplomats say it may be having problems marketing at official prices all the oil it wants to sell . opec agreed in december to cut its production ceiling by 7 . 25 pct to 15 . 8 mln bpd and all members were abiding by its agreements . " we ' re not thinking of issuing bonds ," she said . she said the surplus of 597 mln pesos , compared with a year - earlier profit of 7 . 9 mln shares . wall street traders said ual ' s stock soared in response to a question , tsai said american can ' s investment in the deltona corp is reported on the equity method beginning the fourth qtr of 1986 . amounts for 1985 and the first three qtrs of 1986 have been restated to reflect a six - for - five bonus issue replacing " b " shares of par value 20 cents each for every one share of par value two dlrs each , books close august 3 to 10.

#### feed: "The name of the"

output:

the name of the company is not yet at point in its cost - cutting drive to improve profit margins , it is " on the right track ." olson said att ' s cash flow was " very strong in the first two months of 1987 from about 260 , 000 barrels per day ( bpd ) of crude oil , well below its opec quota . saudi arabia , the world ' s largest oil exporter , will continue to restrain production as long as other opec members adhere to the program as devised in december , saudi arabia will continue to adhere to the agreement ," he said . " we have to be competitive . it ' s a very healthy development ," he added ." if you asked me about that a year or 18 months ago i would have said that it was too soon to say what the administration policy on oil tax incentives would be and indicated there would be opposition to tax changes . " of course , to move forward with these kinds of options would require reopening tax issues settled last year ( in the tax reform bill ) -- an approach which has not , in general , been favored by the administration . i think what we need is to debate this within the administration ," he said . " we have to be competitive . it ' s a very healthy development ," he added ." if you asked me about that a year or 18 months ago i would have said that it was too soon to say what the administration policy on oil tax incentives would be and indicated there would be opposition to tax changes . " of course , to move forward with these kinds of options would require reopening tax issues settled last year ( in the tax reform bill ) -- an approach which has not , in general , been favored by the administration .

#### feed: "the company said the"

output:

**the company said the offer** and withdrawal rights expire april 20 unless extended . the offer is conditioned on receipt of at least two years and stress retraining to help the long - term capital account surplus was 87 mln dlrs against 46 mln and 158 mln . the errors and omissions account left a surplus of 840 mln dlrs in february from 3 . 89 billion a year ago . **the company said the offer** and withdrawal rights expire april 20 unless extended . the offer is conditioned on receipt of at least two years and stress retraining to help the long - term capital account surplus was 87 mln dlrs against 46 mln and 158 mln . the errors and omissions account left a surplus of 840 mln dlrs in february from 3 . 89 billion a year ago . **the company said the offer** and withdrawal rights expire april 20 unless extended .

### conclution:

As denoted by the third case the pentagram model still suffers from the repetition problem but less so compared to the trigram model.
The pentagram model, even though makes sence relative to the trigram model, falls apart in the contex department because its memory capasity of 4 words is still way too low for natural language. When humans speak, what we are going to utter now depends on sentences that were uttered long before the present and this is why simple ngram models cannot cope up with the complexity of human language. To combat this problem we will have to use more complex models like **RNNs and LSTMs with attention** that can remember the past and certain highlights of it (like certain words of the past help us determine the future more so than other words like *and* , *or*, etc that have very low semantic value) and a representation of the distant and recent past can be used to determine the future. 
