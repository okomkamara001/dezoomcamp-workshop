# Workflow Orchestration
Welcome to Module 2 of the Data Engineering Zoomcamp! This week, we’ll dive into workflow orchestration using **[kestra](https://go.kestra.io/de-zoomcamp/github)**.

Kestra is an open-source, event-driven orchestration platform that simplifies building both scheduled and event-driven workflows. By adopting Infrastructure as Code practices for data and process orchestration, Kestra enables you to build reliable workflows with just a few lines of YAML.

# 2.1 Introduction to Workflow Orchestration

In this section, you’ll learn the foundations of workflow orchestration, its importance, and how Kestra fits into the orchestration landscape.

## 2.1.1 - What is Workflow Orchestration?

Think of a music orchestra. There's a variety of different instruments. Some more than others, all with different roles when it comes to playing music. To make sure they all come together at the right time, they follow a conductor who helps the orchestra to play together.

Now replace the instruments with tools and the conductor with an orchestrator. We often have multiple tools and platforms that we need to work together. Sometimes on a routine schedule, other times based on events that happen. That's where the orchestrator comes in to help all of these tools work together.

