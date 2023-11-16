---
layout: post
title: Tagging Document - LangChain 
date: 2023-08-10 09:01:00
description: Labelling/Classifying corpus using LangChain
tags: 
categories: 
---

### Tagging Document - LangChain 🦜
`Labelling/Classifying corpus using LangChain`


Recently LangChain introduced Document Tagging Chain. Tagging refers to simply assigning label(s) to a corpus.
I will cover a basic demo of how document tagging works using LangChain. From analyzing sentiment in customer feedback to identifying the intensity oflanguage use, the potential applications of this technology are vast. 

I will take the text-book task for classification in Machine Learning i.e Email Classification to demonstrate tagging via langchain. 
We already have a plethora of tools in the market for classifying and filtering out emails. So how will using a Tagging chain from LangChain will be any different/better?

Unfortunately, these tools are based on rule-based filtering and classification techniques, which may not capture the context and nuances of emails effectively. This is where we can power up the classification using tagging chain.

- Install the dependencies

{% raw %}
```zsh
!pip install -qU langchain pydantic
```
{% endraw %}

- Importing dependencies

{% raw %}
```python
from langchain.chains import LLMChain, create_tagging_chain_pydantic
from langchain.chat_models import ChatOpenAI
from enum import Enum
from pydantic import BaseModel, Fieldimport 
import os
```
{% endraw %}

- Prepare the source text

{% raw %}
```python
text_source = """
Subject: Urgent Concerns about the Reliability of WonderTech AI Product

Dear Arshad,

I am Bruce, the CTO at Microsoft. I am writing to express my deep disappointment regarding the recent issues with our AI product.

We value our longstanding partnership, and it is crucial that we address these concerns promptly. Please provide a comprehensive plan outlining the steps you will take to improve the reliability of our AI system.

I appreciate your partnership and trust that, by working together, we can overcome these challenges.

Sincerely,
Bruce
CTO
Microsoft

"""
```
{% endraw %}

- Create Tag description by Pydantic class

I outlined four specific tags that provide a detailed description of the topic. These tags also include information about the sender's significance, the urgency of their message, and their feelings. These details assist the recipient in better organizing their emails for efficient management.

{% raw %}
```python
class EmailFeatures(BaseModel):
    topic: str = Field(
        ...
        enum=[
            "Customer Complaint",
            "Follow-up",
            "Proposal",
            "Demo/Product Presentation",
            "Deal Negotiation",
            "Order Processing",
            "Customer Testimonials/Reviews",
            "Product Information Request",
            "Account Support",
            "Shipping and Delivery",
            "Payment and Billing",
            "Return and Refund",
            "Product Support",
            "Technical Support",
            "Partnership/Cooperation",
            "Event/Conference Invitation",
            "Webinar/Training Registration",
            "Other"
        ],
    )

    sender_weighs: int = Field(
        ...,
        description="The importance of sender based on their title and company, and their content of the message",
    )
    urgent: int = Field(
        ...,
        description="Score 1-10, 10 is the highest level of urgency",
    )
    sentiment: int = Field(
        ...,
        description="wether the email has a negative, positive or neutral sentiment",
    )
```

{% endraw %}

- setting up model and chain

{% raw %}
```python
os.environ["OPENAI_API_KEY"] = <your_api_key>
llm = ChatOpenAI(temperature=0, model="gpt-3.5-turbo-16k")
tagging_chain = create_tagging_chain_pydantic(EmailFeatures, llm)
res = tagging_chain.run(text_input)
print(res)
```
{% endraw %}


The output would be:
{% raw %}
```html
topic='Customer Complaint', sender_weighs=10, urgent=10, sentiment='negative'
```
{% endraw %}

These tags would give a clearer picture of the email to you without you having to read through the entire mail.

Lastly, there are many other potential use cases such as:
- Resume Screening
- Medical Record Analaysis
- Legal Document Analysis


