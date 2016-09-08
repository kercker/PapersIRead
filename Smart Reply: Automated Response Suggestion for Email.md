#Smart Reply: Automated Response Suggestion for Email

This paper explored the methods to suggest short responses to Email messages.
## Introduction
  * Challenges faced
    * Response quality: high quality in style, tone, diction, content
    * Utility: maximize the likelihood suggestted response is chosen
    * Scalability
    * Privacy
  * Method to tackle the challenges
    * Response selection: select the best reponses from response set
    * Response set generation: offline-generated reponse set
    * Diversity: responses not too likely
    * Triggering model: wether to auto-respond
    
## Selecting Responses
  * Given an original message, find the most likely response.
    * r* = argmax P(r|o) with repect to r belonging to R (response set)
  * Input token o is {o1, o2, ..., on}, response token r is {r1, r2, ..., rm}
    * P(r|o) = P(r1, r2, ..., rm| o1, o2, ..., on)
    * Factored as P(r1, r2, ..., rm| o1, o2, ..., on) = P(r1|o1,..,on)*..*P(rm|o1,..,on,r1...rm-1)
    * Similiar to HMM
    * Training
      * LSTM, with a recurrent projection layer
      * Use AdaGrad
      * TensorFlow
    * Inference
      * Draw a random sample from response distribution
      * Approximate most likely response: can use beam search (not that greedy)
        * Beam search: take top b bokens and feed them in, retain the b best response prefixes and repeat
      * Determine likelihood of a specific response candidate
  * Challenges
    * Response quality: construct response set
    * Utility
      * Favor common, unspecific responses
        * normalization like idf in tf-idf, that penalizes reponses that can be broadly applied
      * Have little diversity
        * Enforce diversity through semantic structure of response set
      * A triggering model
    * Scalability
      * Use beam search, complexity O(bl), where b is beam size, l maximum response length
    * Privacy
      * Encrepted data

## Response Set Generation
  * Target response space
    * Variability in language and intens
    * 1.Define a response space for response selection
    * 2.promote diversity
  * Canonicalizing email responses
    * dependency parser ???
  * Semantic intent clustering
    * funny cluster...
    * Semi-supervised ml problem, user graph algorithm, human-provided cluster seeds
  * Graph construction (similar to concept extraction from lab)
    * response nodes and feature nodes
      * if feature v belong to the feature set of reponse u, then there is an edge between v and u
      * Bipartie graph
  * Semi-supervised learning
    * Use EXPANDER
    * Propagate the cluster labels in the graph
  * Cluster Validation
    * Human!!!

## Suggestion DIversity
  * Omitting redundant responses
    * no two responses of same intent
    * intent defined based on clustering of response set
  * Enforcing Negatives and positives
    * not say how to tell wether positive or negative??

## Trggering
  * Requirements
    * good enough to figure where response is not expected
    * fast!!!
  * Data and Features
    * Positive class: messages with reply by human from mobile device...
    * Negative: subset of all messages
  * Network architecture
    * feedforward multilayer perceptron: better than svm in nlp
    * ReLu
    * dropout
    * AdaGrad
    * TensorFlow

## Evaluation
  * Perplexity: equal to k means, there are k candidates for next word
    * k = 1 is perfect
  * Response ranking
    * real response ranked between all possible response with P(r|o)
    * Calculate Mean Reciprocal Rank
