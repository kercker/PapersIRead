# Machine learning and Feature Based Approaches to Gender Classification of Facebook Statuses
Authorship classification and gender classification based on Facebook statuses.

##Introduction
  Compared with based on email: short text, lack stylisticly rich information.
  
  Human survey as baseline, accuracy:65.5%.

##Related work
  Email: females often use emotion words, questions, compliments, apologies. male: opinions, adjectives,
    insults.
    
  Another email authorship: character attributes, word based attributes, structural attributes, human function words.
  Corney.
  
  Second Life: emoticons, slang, typos, specific high frequency words.

##Dataset
  Over 170,000 statuses from males and females crawled from Facebook through Facebook Open Graph
    API.
    
  Female preponderance. 12:7. Maybe: female write more statuses; error in data collecting.
  
  Trained on equal amounts of male and female data.

##Human classification
  Not very good.
  
  Some easy, some extremely ambiguous, others skewed strongly in for the wrong gender.

##Maximum Entropy Classifier
  120,000 statuses. 60 iter.
  
  Features
  
    Word Based
      *HAS_WORD_ + word: stem
      *HAS_MULTIPLE_REPEATED_LETTERS: happyyyyyy
      *specific features: common word or text strings. omg, lol, love, haha, xo
      *links: bit.ly, youtube.com
      *these features guess Female for everything.
      
    Structure Based
      *punctuation
      *capital letters
      *emoticons
      *HAS_SMILEY
      *Excessive punctuation, capital letters
      
    Count Based
      *percentage of letters, digits, punctuation, whitespace, upper case, lower case
      *bucket on percentage: 0-9% in one, 10-19% next
      *punctuation and case features helpful.
      
  Performance
    Use both as positive instance to calculate two f1's
    
    59-62.2% depending on which features activated.
    
    accuracy versus amount of data.
    
  Errors
    Male different posting patterns when directed towards males vs females.
    
    short statuses.
    
    Posible improvements: smarter lexical stemming system.
##Perceptron
  Male positive: positive word weights related to male, negative to female, closer
    to 0 less useful
    
  increased performance by artificially boosting weights of important words.
##Bigram Status Generator
  interesting.
