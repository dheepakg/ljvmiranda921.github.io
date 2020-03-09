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
right into it. Recall that in [Part
One](/notebook/2020/03/06/jupyter-notebooks-in-2020/), we identified (1) two
axes of growth&mdash; Cloud & Production, and (2) three forces of change that 
drives the growth of the Jupyter Notebook ecosystem:

![](/assets/png/jupyter2020/axis_with_jupyter_forces.png){:width="480px"}  
**Figure**: The growth of the Notebook ecosystem is driven by these forces
{: style="text-align: center;"}

Here in Part Two, we'll dive right in and examine what these key drivers mean,
how the Jupyter Ecosystem adapted to these forces (e.g. a new plugin,
a product offering, etc.), and putting them together to talk about my own
workflows.

#### Contents

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

A huge component of data science is experimentation. This can come in the form
of feature engineering, hyperparameter optimization, or testing-out models. As
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
| Runner-up | If you are using a Cloud Platform, I'd recommend checking-out managed notebook instances in [AWS Sagemaker](https://docs.aws.amazon.com/sagemaker/latest/dg/nbi.html) or Google Cloud's [AI Platform](https://cloud.google.com/ai-platform-notebooks). |
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
because they have Git integration out-of-the-box, it is easy to incorporate a
repository to the platform.

### Support for developer workflow 

<!-- extensions -->
<!-- non-notebook tools that can help: cookiecutter-datascience -->


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
