# ICFP'20

## ICFP'20

I enrolled as a Student Volunteer for this year's ICFP which was held online due to the pandemic. This series of posts contains my thoughts and notes I've taken while attending it.

## PLMW

From SIGPLAN's [page](http://sigplan.org/Conferences/PLMW/)

> The purpose of this mentoring workshop is to encourage graduate students \(PhD and MSc\) and senior undergraduate students to pursue careers in programming language research. This workshop will provide technical sessions on cutting-edge research in programming languages, and mentoring sessions on how to prepare for a research career. We will bring together leaders in programming language research from academia and industry to give talks on their research areas. The workshop will engage students in a process of imagining how they might contribute to our research community.

Being relatively new to research I thought this

### Session 1

#### Introduction

* PLMW is also a scholarship program when conducted in person - students get sponsored to attend PLMW

#### How to write papers so people can read them

* Do research → write papers → give talks : repeat
* Paper readers' POV : What does it **do** and why do I **care**?
* Curse of knowledge : writer's don't know what it is like to be a reader who don't know what they're reading about
* Books
  * Style : Toward clarity and grace, Joseph M. Williams
  * Learn technical writing in tow hours per week,
  * _How to write a great research paper,_ Simon Peyton Jones
* Principles for writing clearer : constructive litmus tests 1. Flow: adjacent sentences/paragraphs relation should be clear

  ```text
    Use "old to new" - begin sentences with old information and end sentences with new information
  ```

  1. Coherence: each paragraph should make its place clear in the big picture

     Use "one paragraph, one point" - put main point at/near the beginning of the paragraph

  2. Name your baby : Unique names to things and consistent usage
  3. Just in time : give information precisely when needed, not before
  4. Short subjects : subject of sentence at most 8 words long

* Structure of a research paper 1. 3-5 people from the program committee read your paper, everything in their hands 2. Each PC member has &lt; 1 day to review each paper

  * Principle \#1: Top down approach
  * Principle \#2: Tell them what they want to know \(don't leave it to their inference!\)

    Things PC reviewers look for

    1. Importance of work?
    2. Novelty of work?
    3. How is your work interesting?

  * Useful structure:
  * Abstract 1-2 paragraphs, 1k readers
  * Intro 2-4 pages, 100 readers

    CGI model for abstract + intro : context \(motivate general topic\), gap \(specific problem & why existing work does not adequately solve it\) and innovation \(how your work fills the gap\)

  * Key ideas 4-6 pages, 50 readers

    Forces you to have a takeaway \(something interesting\), may readers only care for takeaway \(including PCs!\), for interested readers it acts as a scaffolding for the technical meat.

    How would you explain it to someone at a whiteboard? Concrete illustrative examples

  * Technical meat 8-12 pages, 5 readers
  * Related work 1-3 pages, 100 readers

    Goes at end of paper : con only properly compare to related work once you've explained your own

    Give real comparison : not laundry list - explain in detail how your work compares to others

  **Managing Your Research, Advisor, PhD**

  Pre-PhD

  * Finding what to work on : ask PL faculty member for advice, attend talks, read paper intros, email faculty after reading papers - makes authors happy!
  * Where to go
    1. Most important factor is advisor \(research interests + personality\)
    2. Next is lab culture & peer group.
    3. Not important - financial incentives, institution, location
  * Advisor fit 1. Talk to current & former students 2. Work expectations - freedom to pick topic, large project team vs individual project 3. Do they train students for academia/research labs? 4. How well did current & former students do \(papers, research reputation, jobs post-PhD\)

    PhD Year 1

  * Starter project : something helps you learn technical skills, become familiar with literature & leads to first research paper
  * Advisor relationship, meetings, communication - it is **your** project, keep notes TODOs, questions
  * Discuss ideas, give talks about work in progress, ask questions
  * **Dont's**
    1. Focus on classes and ignore research
    2. Working the day before advisor meeting
    3. Avoiding advisor - busy advisor may not push you
    4. Not investing time in making lab friends
  * Understand advisor's role
    1. Help pick starter project
    2. Help make you part of research community
    3. Help develop research taste & high research standards
    4. PhD is not for your advisor, for you
    5. Develop strategies to engage your advisor effectively
  * Pressure to publish : few high quality &gt; many so-so ones

    PhD Year 2-3

  * Discussing the big picture with your advisor - where your project is headed and what you want to do

  **Basic Mechanics of Operational Semantics**

  * Natural semantics : relation over syntactic terms and semantic domain

    $$\downarrow\subseteq\mathcal{A}\times D$$

    Example

    $$e\downarrow 1\implies Pred(e)\downarrow(i-1)$$

  * Small Step Semantics : Two expressions are related if one can reach the other in one step

    $$\rightarrow\subseteq \mathcal{A}\times\mathcal{A}$$

    Example

    $$Pred(e)\rightarrow e-1$$

    Relation between natural and SSS

    $$e\downarrow e'\iff e\rightarrow^* e'$$

  * Reduction semantics : They tell you how to reduce expressions to normal forms \(think term rewriting\)
  * Abstract machine : states and transitions on states

## Main track

The talks I listened to were

### POPLMark reloaded: Mechanizing proofs by logical relations

### The Simple Essence of Algebraic Subtyping: Principal Type Inference with Subtyping Made Easy \(Functional Pearl\)

### Regular Language Type Inference with Term Rewriting

### A dependently typed calculus with pattern matching and erasure inference

