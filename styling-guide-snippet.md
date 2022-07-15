# HashiCorp Engineering Writing Style

Whether it is a blog post or technical documentation, HashiCorp has a particular writing style we do our best to adhere to.

## Why?

A consistent writing style and voice strengthens the HashiCorp brand and 
produces clearer educational materials. Our style guide optimizes for:

- **Non-native speakers** - Common figures of speech may not translate easily in different countries or regions.

- **2am, half awake operators** - Flowery sentences are distracting when resolving production incidents.

- **Efficiency** - A clear style guide helps content developers to focus on the content itself. 

- **Product transitions** - Consistent style lets users seamlessly navigate between documentation for our different products.

## Guiding principles

User experience and feedback informs our principles. We aim to follow [Orwell's 6
rules](http://www.orwell.ru/library/essays/politics/english/e_polit):

- Never use a metaphor, simile, or other figure of speech which you are used to
  seeing in print.

- Never use a long word where a short one will do.

- If it is possible to cut a word out, always cut it out.

- Never use the passive where you can use the active.

- Never use a foreign phrase, a scientific word, or a jargon word if you can
  think of an everyday English equivalent.

- Break any of these rules sooner than say anything outright barbarous.

## Sentence structure

The following are our main rules for sentence structure.

### Active voice

To convey causality, always use active voice. For example:

- This file configures ...
- Terraform deploys ...
- The proxy sends ...

### Present tense

To convey the timing, always use present tense. For example:

- Now configure the server.
- Set the variable ...
- Add the parameter ...

### Directive language

To convey instructions, use directive language. For example:

- Open a browser. 
- Download the binary.
- Destroy the infrastructure. 


### Complete example

```text
Good:
To install Terraform, find the appropriate package for your system and download it as a zip archive.

Bad:
You can install Terraform by finding the binary and downloading it. You will need the appropriate package for your system.
```

## Word choice

Observe the following recommendations for word choice:

- Use "you" for the user
- Use "we" for HashiCorp recommendations
- Avoid ableist language
- Never use a metaphor, simile, jargon, or other figure of speech
- Use short words 
- Cut unnecessary words

Below are a few word-choice examples. 

### Grammatical person: "You" for the user

Write documentation in the second person, addressing the reader directly as "you".

```text
Good: Terraform Cloud's API lets you create workspaces without a VCS connection.

Bad: Terraform Cloud's API allows one to create workspaces without a VCS connection.
```

### Active voice: "We" for HashiCorp

Active voice _enforces attribution._ In
our documentation, the opinions and advice on offer belong to **us, here at
HashiCorp.** Our language should never try to hedge or evade responsibility for
the guidance we're providing. If HashiCorp is making a recommendation, say "we".

```text
Good:
We recommend configuring VCS access when first setting up an organization.

Bad:
It is recommended to configure VCS access when first setting up an organization.
```

In cases where the actor of a sentence is a tool or system, rather than a person
or company, you should still use active voice. It's easier to
understand and sometimes distinguishes between automated and operator actions.

```text
Good:
Next, Kubernetes will register the service.

Bad:
Next, the service will be registered.
```

### Inclusive Language

### Pronouns

If you are using the grammatical person "you" for the user you probably won't
use very many pronouns in your writing. If you do find yourself using pronouns,
make sure they are necessary, and if so, use the gender neutral "they/them".

|Good|Bad|
-|-
|Once you give the developer the token they can...|Once you give the developer the token she can...|

### Oversimplification

Our products can be complex. Words that indicate that processes are easy
can alienate users who are having a hard time or are encountering bugs.

Avoid saying:
- easy, easily, simply
- just (as in "just run this command")
- obviously
