---
layout: archive
title: Precision and Recall Evaluation Metrics in Machine Learning
date: 2020-04-29T20:23:30.161Z
updated_date: 2020-04-29T20:23:30.181Z
description: Recall is defined as the number of relevant documents retrieved by
  a search divided by the total number of existing relevant documents, while
  precision is defined as the number of relevant documents retrieved by a search
  divided by the total number of documents retrieved by that search.
published: true
show_ads: false
include_mathjax: true
---
Precision and Recall are two best known and most misunderstood evaluation metrics in machine learning. In this article we are going to discuss the simplest way in which we can understand them with an example.

Consider that we were playing a simple game online. The rules of the game are pretty simple, you will have to shoot the space ships of the opposition constantly, until you see a survivor space ship coming toward you.

{% include lazyload.html image_src="https://i.ibb.co/C68RwcW/Screenshot-2020-04-30-at-1-51-48-AM.png" image_alt="Space game example for understanding precision and recall" image_title="Space game example for understanding precision and recall" %}

Now let's consider that your model was playing the game from a long time and have collected a lot of related data.

Data points that we collected belonged to these 3 categories.

```
Total time you Stopped shooting: x
Total time you Stopped shooting with survivor ship ahead you: y
Total time you Stopped shooting with Opposition Space ship ahead you: z
```

Now, we created a Venn diagram to explain the occurrences.

{% include lazyload.html image_src="https://i.ibb.co/8DGyTrc/Screenshot-2020-04-30-at-2-27-56-AM.png" image_alt="Venn diagram for understanding precision and recall" image_title="Venn diagram for understanding precision and recall" %}

## Precision

Precision is the value which gives the value of number of times you took the correct action of all the times you took an action.

So, precision is given by the intersection divided by the blue part of the Venn diagram. i.e.

{% include math.html math_code="$precision = \frac{Correctly\ stopped\ shooting}{Total\ Number\ of\ Shooting\ stops}$" style="margin-top:0.2em;" %}

## Recall

Recall is the value which gives the value of all the times you were supposed to take an action of all the times you took an action.

So, Recall is given by the intersection divided by the orange part of the Venn diagram.

{% include math.html math_code="$recall = \frac{Correctly\ stopped\ shooting}{Total\ Number\ of\ times\ survivor\ ships\ in\ front}$" style="margin-top:0.2em;" %}

More detailed discussion of [precision](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/#precision) and [recall](https://ranvir.xyz/blog/how-to-evaluate-your-machine-learning-model-like-a-pro-metrics/#recall) are done in the evaluation metric post.

{% include linked_post.html url="how-to-evaluate-your-machine-learning-model-like-a-pro-metrics" %}