
+++

title = "Large language models as oracles for instantiating ontologies with domain-specific knowledge"
description = "Presentation for the paper 'Large language models as oracles for instantiating ontologies with domain-specific knowledge'"
outputs = ["Reveal"]
aliases = [
    "/llmg4kg/"
]

+++


# Large language models as oracles for instantiating ontologies with domain-specific knowledge

[Giovanni Ciatto](https://www.unibo.it/sitoweb/Giovanni.Ciatto/en), 
[Andrea Agiollo](https://www.unibo.it/sitoweb/Andrea.Agiollo/en), 
[Matteo Magnini](https://www.unibo.it/sitoweb/Matteo.Magnini/en), 
and
[Andrea Omicini](https://www.unibo.it/sitoweb/Andrea.Omicini/en)

<br/>

ArXiv preprint: [arXiv:2404.04108](https://arxiv.org/abs/2404.04108) 

<br/>

(Currently under revision for the [Knowledge-Based Systems](https://www.sciencedirect.com/journal/knowledge-based-systems) journal.)

---

## Context (pt. 1)

### The problem

- Many knowledge-based applications require __structured data__ for their operation

- These systems commonly __adapt__ their behaviour to the available data...
    + ... and acquire new data __while__ operating

- Notable example: __recommendation systems__
    + providing __hints__ to users based on their __preferences__...
    + ... and on the __profiles__ of similar users

- Chicken-and-egg problem, namely the __cold-start__:  
    1. the system need data to operate effectively
    2. the system acquires data while operating, from users
    3. at the beginning there's no data, and no users
    4. how to escape this situation?
---

## Context (pt. 2)

### Example

As part of the CHIST-ERA IV project ["Expectation"](https://expectation.ehealth.hevs.ch/posts/home/), we needed to:

1. design a virtual coach for __nutrition__
    + giving personalised advices on __what to eat when__ to users

2. the system would need __data__ about:
    + food, e.g. recipes, their ingredients, their nutritional values, etc.
    + users, e.g. their preferences and their habits, goals, medical issues, etc.

3. __model__ the data schema and __find__ some data matching it

---

## Context (pt. 3)

### The insight

> Obvious solution: __generating__ (i.e., synthesizing) data

<br>

Yet, the generated data should:
- be __syntactically__ valid, i.e. match the __structure__ expected by the system
- be __likely__, and therefore __meaningful__ for the system
    + in a nutshell: match the __domain__ the system is going to be deployed into

### Example 

1. Generate a schema for recipes and user profiles
2. Design the business logic on top of that
3. Generate data matching the schema

---

## Background (pt. 1)

### Ontologies

- Easy yet powerful means to represent __knowledge__ in a structured way
    + theoretically sound
    + widely used in __AI__ and __knowledge engineering__
    + technologically supported by the __Semantic Web__ stack

- In a nutshell:
    
    ![Overview on ontologies](http://www.plantuml.com/plantuml/svg/TP2nJiCm48PtFyMDPN0Ve8gYLXLC81P6bcjoJTmwTdHs41MmLomy1y_1c_0acDWkNf2YvFwxx_wB_hNpo7uQj1YnEM97S4iTcHPU142ZqJdOMjFGwF_q_AugN1wNkAnh8I0pKBrALbtlPQ9MuARTNDxlOV7z_d4LuF3OtO4Q3ygqwacr4-govpm6jtykMDdAOcy5ocs2y_aSdEFHZ4IR4X1GR8AKB6LTW2FRaTYV7iqYNWOcZLvPuterpd_-9YuvNJ_ZC6eAGSLO7dfbEf74ngW1TH9RzAcwivCZ8MRqDokPmVY9hO2NEY-bUBmTSdaWvfCGMuofpACPZZAEGnCaophA5JGzEd8NkmvvhqYtMVFNvr1wvdbf79ayWKhgr0lkrXxTZUKGr9fCEmtw1m00)