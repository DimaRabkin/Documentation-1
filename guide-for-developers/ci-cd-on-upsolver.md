---
description: >-
  This article provides an overview of the typical continuous integration and
  continuous delivery (CI/CD) pipeline on Upsolver.
---

# CI/CD on Upsolver

## Continuous Integration and Development \(CI/CD\) in Upsolver

CI/CD is a set of methodologies used to frequently deliver new features to customers. 

The main CI/CD frameworks are continuous integration, continuous delivery, and continuous deployment. CI/CD is used to solve problems that development and operations teams often encounter when integrating new code. 

Implementing CI/CD in databases can be challenging, but Upsolver’s event sourcing architecture makes it easy to apply CI/CD principles throughout your development lifecycle.

## About CI/CD

* Only need CI/CD for ETL code \(raw data is stored as an immutable log\)
* Isolation between dev and prod
* GIT integration for ETL code source control
* REST API for infra-as-code

{% hint style="info" %}
**See:** [FAQ on Upsolver CI/CD](../getting-started/tutorials-and-faq/faq.md#upsolver-ci-cd)
{% endhint %}

