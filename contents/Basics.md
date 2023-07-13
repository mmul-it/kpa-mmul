# **KPA**: a definition

The Knowledge **Pods** Approach (**KPA**) is a method for creating training materials,
presentations and documentation that separates the _content_ creation
(**the knowledge**) from their _presentation_ (**the files**, i.e. pdf, ppt and html).

**KPA** relies on the standard markdown file format, which means that there will be
no need to rely on proprietary tools and formats to create contents.

**KPA** helps to concentrate on what matters most: **the knowledge**.

---

## What is a **KPA project**

A **KPA project** is a set of markdown files and variables in a yaml format that
are used by the Ansible role named [kpa_generator](https://github.com/mmul-it/kpa_generator) to automate the creation
of a single markdown file that can be processed using [Marp (Markdown Presentation Ecosystem)](https://marp.app/#get-started) to obtain a set of slides in the usual presentation
formats like **html**, **pdf** and **ppt**.

**KPA** makes it possible to control all the knowledge in a standard and "edit from
everywhere" way, making it easy to compose and mix the set of topics you want to
include into the training, by creating sequences of **Knowledge Pods** (**KP**).

---

## What is a **Knowledge Pod**

Just as a _Kubernetes_ Pod is the _smallest execution unit_ in Kubernetes, a
**KP** is the _smallest knowledge unit_ in which you can cover a topic.

A **KP** can be a unit, a chapter, a section that covers entirely a topic and
cannot be split into sub topic. If you need to deliver a training named
"_How to use my technology_" you will likely to have these **KP**s:

- Introduction.md
- Prerequisites.md
- Installation.md
- Day-0-operations.md

**KPA** then takes care to combine everything in a standard and replicable doc.

---

## What is **KPA** in the end

**KPA** is at the same time:

- The definition of an approach, described in the [KPA GitHub page](https://github.com/mmul-it/kpa).
- A container available at the [quay.io registry](https://quay.io/repository/mmul/kpa).
- An Ansible role named **kpa_generator** available in [Ansible Galaxy](https://galaxy.ansible.com/mmul/kpa_generator).
