# HashiCorp Engineering Writing Style

Whether it is a blog post, technical documentation, or communication with users,
HashiCorp has a particular writing style we do our best to adhere to.

It is important to note that these are _guidelines_. There are situations where
violating these rules is sensible, acceptable, or required. However, try to
adhere to these guides.

## Why?

Having a consistent writing style and voice is what makes the HashiCorp brand
strong and vibrant. There are a few reasons for the choices of our writing
style. In particular:

- **Optimizing for non-native speakers** - HashiCorp is a global company. We
  have users on at least 6 continents, many of whom do not speak English (the
  primary language of the company and our writings). Translation tools are not
  very smart, but even literal translations do not mean the same thing in
  different colloquialisms.

- **Optimizing for 2am, half awake operators** - Many HashiCorp tools are in the
  path of downtime. While we strive to make the best tools in the world,
  sometimes they fail. Having flowery sentences is not helpful when trying to
  get a system back online.

- **Optimizing for our own time** - When we write in the same style, we can
  spend more time focusing on the content and body of a pull request or
  documentation change, instead of pointing out small style inconsistencies.

- **Optimizing for product transitions** - A user who is familiar with the
  Consul documentation that chooses to adopt Vault should not feel as though
  they need to learn an entire new language just to read the docs. This helps
  our overall adoption strategy.

## Guiding Principles

The majority of our principles are guided by experience and user feedback. As a
high-level set of rules, we follow [Orwell's 6
rules](http://www.orwell.ru/library/essays/politics/english/e_polit):

- Never use a metaphor, simile, or other figure of speech which you are used to
  seeing in print.

- Never use a long word where a short one will do.

- If it is possible to cut a word out, always cut it out.

- Never use the passive where you can use the active.

- Never use a foreign phrase, a scientific word, or a jargon word if you can
  think of an everyday English equivalent.

- Break any of these rules sooner than say anything outright barbarous.

### Grammatical Person: "You" for the User

Write docs in the second person, addressing the reader directly as "you".

```text
Good: Terraform Cloud's API lets you create workspaces without a VCS connection.

Bad: Terraform Cloud's API allows one to create workspaces without a VCS connection.
```

### Active Voice: "We" for HashiCorp

Avoid [passive voice](https://en.wikipedia.org/wiki/English_passive_voice);
write with the active voice as much as possible.

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

In cases where the actor of a sentence is a tool or system (rather than a person
or company), you should still use active voice, because it's easier to
understand and sometimes distinguishes between automated and operator actions.

```text
Good:
Terraform has a provider framework to leverage this behavior.

Bad:
To hook into this behavior, a provider framework has been built into Terraform.

Good:
Next, register the service

Also good:
Next, Kubernetes will register the service.

Bad:
Next, the service will be registered.
```

## Inclusive Language

### Pronouns

If you are using the grammatical person "you" for the user you probably won't
use very many pronouns in your writing. If you do find yourself using pronouns,
make sure they are necessary, and if so, use the gender neutral "they/them".

|Good|Bad|
-|-
|Once you give the developer the token they can...|Once you give the developer the token she can...|

### Over Simplification

Our products can be complicated. Words that indicate that processes are easy
don't add meaning to your writing and can alienate users who are having a hard
time or encountering bugs.

Avoid saying:
- easy, easily, simply
- just (as in "just run this command")
- obviously
