# Strategies for Extracting Audience-relevant Insights from the Content They Consume

If we want to design messages and content that resonate with specific audiences, we need to meet their needs as information consumers. To do this, we start with the audience instead of the message or story. I call this "audience-centered design." Since message and content development are inherently creative processes, we encapsulate our own goals as advocates as well as what we know about our audience in the creative brief. Anyone who has worked with an ad agency knows this document well. At its heart, it is framework meant for creators to translate organization and audience needs into a creative product.

For Red Hook Media Lab, I've  been developing a novel framework for translating audience insights and behavior change strategies into compelling and effective narrative content. This process combines mixed-methods research with co-creation strategies. Specifically, we pursue multiple sources of insight -- ethnographic, audience-centered research to understand our audience's context; quantitative demographic, socioeconomic, and cultural analysis to identify the "30,000 foot" trends and patterns that define an audience; and media artifact analysis to understand the narratives, stories, characters and themes audiences find compelling as well as their preferred channels. 

The New York Times created a compelling media artifact analysis in 2016, when they identified major cultural splits by analyzing television show preferences across the United States. https://www.nytimes.com/interactive/2016/12/26/upshot/duck-dynasty-vs-modern-family-television-maps.html

This type of work provides interesting audience insights based on their entertainment preferences. But, as content creators, how can we translate the knowledge that `audience A` prefers `show b` over `audience c`, who prefers `show d`, into actionable inputs to inform our own content creation? Qualitative content analysis is certainly one important input.

But, for this work, I seek to leverage natural language tools to surface useful insights that can be translated into meaningful creative strategies. Of course, there is always the fear that perhaps using math and data spells the end of creativity. These were the types of headlines that circulated when Netflix announced back in 2013 that it had used audience data to greenlight $100 million to produce the American version of House of Cards without ever seeing a pilot.  
However, I would argue that using data from both qualitative and quantitative sources can augment creative work while ensuring that our message is more likely to resonate with a particular audience.

This repository represents an exploration of tools and strategies to extract meaningful insights from content that inform strategy and creative messaging for prosocial behavior change.

## The Data

I used a political news dataset I developed for a number of previous projects. It contains roughly 200,000 artiles published in 2019 from 12 sources. Download the entire lightly processed dataset [here](https://politicalnews.nyc3.digitaloceanspaces.com/domain_stop_removed_bias_text.csv)

While news may not be the useful corpus for creating advocacy messages, the techniques should apply to any corpus we can analyze. Further, news stories are inherently abstractions (in the best case scenario) of reality. 

To try and identify meaningful distinction, I segmented my analysis based on the publisher and the political affiliation of each source (left, right, center). 

One caveat: I fundamentally disagree that news outlets can be ranked on a single political-bias continuum. Journalist standards fundamentally differ between organizations like the New York Times and Reuters, which make efforts to apply best practices, and organizations like Fox News and Breitbart, which make little, if any effort, to do so. Nevertheless, these distinctions provide a quick and dirty way to segment news and compare content patterns.

## The Tools and Methods

#### [LDA with Gensim and pyLDAvis](https://nbviewer.jupyter.org/github/AschHarwood/text_explorer/blob/main/analysis/notebooks/genism_full_corpus_3.8.21.ipynb)

This notebook uses Latent Dirichlet Allocation to cluster similar documents and returns unigrams for each cluster. The models can be explored using an interactive visualization created pyLDAvis.

#### [Moral Foundations Analysis of Right, Center, and Left Political News](https://nbviewer.jupyter.org/github/AschHarwood/text_explorer/blob/main/analysis/notebooks/moral_foundations_analysis.ipynb)

This notebooks applies moral foundation theory by using a bag-of-words approach and counting the usage of "morally-loaded" language. It uses a dictionary derived from moral foundations theory


#### [Applying BERT for Topic Modeling with Bigrams](https://nbviewer.jupyter.org/github/AschHarwood/text_explorer/blob/main/analysis/notebooks/Bertopic_vis_3.9.21.ipynb)

This notebook utilizes BERT transformers to cluster similar documents based on bigrams. It contains a visual tool for exploring those clusters. 

You can also view the visual tool to explore right topics [here](https://htmlpreview.github.io/?https://github.com/AschHarwood/text_explorer/blob/main/analysis/right_bertopic_model.html)


#### [Analyzing Emotional Language in Center, Left, and Right News](https://nbviewer.jupyter.org/github/AschHarwood/text_explorer/blob/main/analysis/notebooks/NRCLex_analysis.ipynb)

The following notebook uses a bag of words approach and the NRCLex package to calculate the percentage of words in each news corpus that are associated with the following emotions: `fear, anger, trust, surprise, positive, negative, sadness, disgust, joy, anticipation`.

View the interactive chart [here](https://htmlpreview.github.io/?https://github.com/AschHarwood/text_explorer/blob/main/analysis/html_files/right_bertopic_model.html)

#### [Applying Transformers and Explainable AI to Identify Partisan Keywords](https://nbviewer.jupyter.org/github/AschHarwood/text_explorer/blob/main/analysis/notebooks/BERT_Explain%20%281%29.ipynb)

The following notebook uses a fine-tuned BERT transformer model to predict the partisan lean of the publisher of a news article, and then derive keyword insights from model using explainable AI.