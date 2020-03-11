---
layout: post
title: "How to use Jupyter Notebooks in 2020 (Part 2: How I use them today)"
date: 2020-03-20
category: notebook
comments: true
author: "LJ MIRANDA"
tags: [jupyter notebooks, 2020, technical review, git, data science, software engineering, machine learning]
description: |
    In the second part of this series, I'd like to share some of the tools in
    the Jupyter Notebook ecosystem and how I incorporate them in my workflow.
    I'll talk about what I like (and don't like) about them, and how I use them
    in my day-to-day.
header-img: /assets/png/jupyter2020/axis_with_jupyter_forces.png
excerpt: |
    In the second part of this series, I'd like to share some of the tools in
    the Jupyter Notebook ecosystem and how I incorporate them in my workflow.
    I'll talk about what I like (and don't like) about them, and how I use them
    in my day-to-day.
---


> This is the second of a three-part blog post on the Jupyter Notebook
> ecosystem.  Here, I'll talk about various tools that I use alongside
> Notebooks, and how I incorporate them in my day-to-day work. You'll find Part
> One [in this link](/notebook/2020/03/06/jupyter-notebooks-in-2020/).

Hello, thanks for joining me in the Second Part of this series! Let's jump
right into it. 

Recall that in [Part One](/notebook/2020/03/06/jupyter-notebooks-in-2020/), we
identified (1) two axes of growth&mdash; Cloud & Production, and (2) three
forces of change that drives the growth of the Jupyter Notebook ecosystem:

![](/assets/png/jupyter2020/axis_with_jupyter_forces.png){:width="480px"}  
**Figure**: The growth of the Notebook ecosystem is driven by these forces
{: style="text-align: center;"}

In Part Two, we'll examine what these key drivers mean and how the Jupyter
Ecosystem adapted to these forces (e.g. a new plugin, a product offering,
etc.). Lastly, we'll put them together as I talk about my own workflows.

#### Table of Contents

- [The three forces in focus](#the-three-forces-in-focus)
    * [Experiment on the Cloud](#experiment-on-the-cloud)
    * [Support for developer workflow](#support-for-developer-workflow)
    * [Quick turnaround from prototype to production](#quick-turnaround-from-prototype-to-prod)
- [Putting it together](#putting-it-together-my-notebook-workflows)
    * [Notebook basic gitflow](#notebook-basic-gitflow)
    * [Rapid experimentation](#rapid-experimentation)
    * [Publishing and production notebooks](#publishing-and-production-notebooks)
- [Conclusion](#conclusion)
    * [Response to Reddit FAQs](#response-to-reddit-faqs)

## The three forces in focus

### Experiment on the Cloud

A huge component of the data science workflow is experimentation. It includes
feature engineering, hyperparameter optimization, or testing-out models. As
data gets bigger and models get compute-intensive, it is not enough to do
everything in your laptop. Hence, experimentation workloads are often delegated
into the Cloud. 

#### Toolbox rundown

The figure below shows a collection of tools you can use to experiment on the
Cloud. I ordered them based on **how these services are managed**: *those further
below still requires setup and installation to deploy, while those further up
lets you get started immediately.* Remember: there's no perfect tool, just the
right one for your use-case. In the proceeding sections I'll talk about how I
incorporate them in my daily workflow.

![](/assets/png/jupyter2020/experiment_on_the_cloud.png){:width="480px"}  
{: style="text-align: center;"}

|  | Recommendation |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| Best Tool of Choice | [Google Colaboratory](https://colab.research.google.com/). With Colab, you have immediate access to powerful hardware for your experiments.|
| Runner-up | If you are on a Cloud Platform, I'd recommend checking-out managed notebook instances in [AWS Sagemaker](https://docs.aws.amazon.com/sagemaker/latest/dg/nbi.html) or Google Cloud's [AI Platform](https://cloud.google.com/ai-platform-notebooks). |
| Check out | [Binder](https://mybinder.org/) for "publishing" finished work, and [JupyterHub](https://jupyter.org/hub) if you wish to setup your own managed notebook instances. |


**Here, I'd highly-recommend [Google
Colaboratory](https://colab.research.google.com/) as your daily workhorse.** It
gives you a huge boost with the latest hardware (GPUs, TPUs, you name it!),
while making the user-interface as intuitive as possible. With Colab, you can
organize your notebooks inside a Google Drive folder, and share them as how
you'd share any Google Docs or Slides. I'd say that this *covers almost 80% of
your previous Notebook use-cases.*[^1]

For the other 20%, well it varies. If you're used to writing utility Python
modules for code reuse, then Colab may feel unwieldy. In addition, Git
integration is one-way and idle-time restarts your kernel. You cannot
push your own workflow into Colab&mdash; you have to do it their way.

Now, if you are using Cloud Platforms such as Amazon Web Services (AWS) or
Google Cloud (GCP), **I'd recommend taking a look at Notebook Instances.** They
are managed Jupyter Notebooks in a server, with the option of choosing your
preferred machine type. Between the two, I prefer SageMaker notebooks, it's
less buggy and more seamless than Google's AI Platform Notebooks. In addition,
because they have Git integration out-of-the-box, so it is easy to incorporate a
repository to the platform. 

Notebook instances can be thought of as managed versions of
[JupyterHub](https://jupyter.org/hub). If you're just working alone, I don't
recommend deploying your own Jupyter servers&mdash; the services above should
do the trick. In fact, I'd daresay that if you are in a machine learning
research/engineering team and you're actively using AWS, Azure, or GCP, just
use these managed instances and don't go through the hassle of maintaining your
own servers.

Lastly, Binder is a tool that I only used once but I see great promise in the
future. I used them in [Seagull](https://github.com/ljvmiranda921/seagull), my
Python library for Conway's Game of Life. There I had some Jupyter Notebook
examples that may be better read and interacted with, so I added a "binder
launcher" in the README. Try going to my repo's README, click the "Launch
Binder" badge and see how the magic happens!

### Support for developer workflow 

As data science teams grow, we see a confluence of researchers and engineers
working together. Unfortunately their toolsets vary a lot. I've met engineers
who disdain notebooks, and I've met accomplished researchers who just want to
solve problems and not be bothered by DRY, Inheritance, or what-not. 

In an [ideal world](https://naruto.fandom.com/wiki/Infinite_Tsukuyomi),
everyone uses the same thing and we're all happy. However in practice, we need
to learn how to compromise and support each other: engineers supporting the
tools comfortable for researchers, and researchers learning basic software
engineering principles.[^2] This section focuses more on the latter part,
whereas the next section (Quick turnaround from prototype to prod) will talk
about the former. Remember, the goal is to meet halfway.

#### Toolbox rundown

As shown in the figure below, most of the tools that support developer workflow
are already available as Jupyter Plugins. I'll also be talking about useful
things to check outside the Jupyter ecosystem such as cookiecutters and data
version-control.

![](/assets/png/jupyter2020/support_dev_workflow.png){:width="480px"}  
{: style="text-align: center;"}

|                     | In Jupyter-ecosystem           | External                   |
|---------------------|--------------------------------|----------------------------|
| Best Tool of Choice | magics, nbdime, nbstripout | cookiecutter-datascience   |
| Runner-up           | nbconvert                      | data-version control (DVC) |
| Check-out           | fast.AI's nbdev                |                            |

In my opinion, native-tooling that resembles the Git workflow **and** a
standardized project-structure will always hit the mark. First, I recommend
using the
[cookiecutter-datascience](https://github.com/drivendata/cookiecutter-data-science)
project structure when organizing your [data science projects. It definitely
works out-of-the-box, but you can configure it as you wish!

Now, Jupyter Notebooks by themselves aren't suited for a Git-like workflow.
Even if they're just a JSON text file, they become quite unruly when checking
for diffs or \*gulps\* resolving conflicts. 


<!-- extensions: nbstripout, nbdev, nbdiff -->
<!-- non-notebook tools that can help: cookiecutter-datascience, DVC -->


### Quick turnaround from prototype to prod 


## Putting-it together: My Notebook Workflows


### Notebook basic gitflow 

### Rapid experimentation

### Publishing and production notebooks


## Conclusion


### Response to Reddit FAQs

* **I don't like notebooks, it would be better if people just use text editors
    or IDEs**
* **Why tool X isn't there? Why is tool Y there?**


### Footnotes

[^1]: Generating plots and charts, quick-and-dirty exploratory data analysis (EDA), inspecting a dataset, training models, etc. 
[^2]: 
