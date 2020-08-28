# Common(?) argument fallacies


The other week I read the first book from Plato's *The Republic* and realized that I can derive far more value from the book if I was aware of common fallacies in arguments and try to spot them. This list is an effort towards the same. Reminder to self : the point of an argument is not *just* spotting errors.

# Formal Fallacies

A logical argument is said to have a *formal fallacy* if, and only if, formalizing in the argument in a logical system (for instance, propositional logic) leads to an illogical step in the argument. Note that all the premises may indeed be sound. It is only required that the derivation have at least one illogical step. An example includes a mathematical proof that contains an incorrect step.

## Appeal to probability

Concluding that something will happen because it is likely. For example, Murphy's law - if something can go wrong, something *will* go wrong (although usually used ironically)

## Argument from fallacy

a.k.a. argumentum ad logicam, fallacy fallacy, argument to logic, fallacist's fallacy, bad reasons fallacy

Concluding that since an argument is invalid, the conclusion is also invalid. Special case of converse error.

$$(P\implies Q)\implies (\neg P\implies\neg Q)$$

## Base rate fallacy

Ignoring generic information in favor of specific information. For example, consider the false positive paradox - "when the prevalence, the proportion of those who have a given condition, is lower than the test's false positive rate, even tests that have a very low chance of giving a false positive in an individual case will give more false than true positives overall." Most people find this counterintuitive.

## Conjunction fallacy

a.k.a. Linda problem, Vadacchino Principle

Choosing more specific conclusion, which is always less probable than the more general conclusion (hence "conjunction"), because of internal bias rising from given information. Example:

> Linda is 31 years old, single, outspoken, and very bright. She majored in [philosophy](https://www.psychologytoday.com/us/basics/philosophy). As a student, she was deeply concerned with issues of [discrimination](https://www.psychologytoday.com/us/basics/bias) and social justice, and also participated in anti-nuclear demonstrations. Which is more probable? 
1. Linda is a bank teller.
2. Linda is a bank teller and is active in the feminist movement

## Masked Man fallacy

a.k.a intensional fallacy, epistemic fallacy

### Leibniz's law

It states that if A and B are the same object, then A and B are indiscernible.

Incorrect applications of Leibniz's law lead to Masked Man fallacy, i.e. applying modus tollens (concluding that A and B are not the same object since they are discernible) without recognizing the gap between *knowing* that A and B are not the same and they *actually* not being the same. Example:

1. I know X
2. I do not know Y
3. Therefore Y is not X

## Propositional Fallacies

Fallacies involving compound propositions (and, or, not etc)

### Denying the antecedent

Inverse error

$$A\implies B\\
\neg A\\
\therefore\neg B$$

### Affirming the consequent

Converse error

$$A\implies B\\
B\\
\therefore A$$

### Affirming a disjunct

$$A\lor B\\
A\\
\therefore\neg B$$

## Quantification Fallacies

Quantifier of premises don't logically agree with quantifiers of conclusion.

## Formal Syllogistic Fallacies

### Illicit negative

Making conclusion with at least one false premise. Example: No boys are girls, and no girls are invisible, therefore all boys are invisible.

$$(A\cap B = \phi)\cap(B\cap C = \phi)\implies A\subset C$$

### Fallacy of exclusive premises

todo