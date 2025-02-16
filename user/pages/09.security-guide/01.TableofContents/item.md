---
title: 'Security Table of Contents'
metadata:
    description: 'Security Guide Table of Contents'
    author: 'Joe Bordes'
content:
    items:
        - '@self.children'
    limit: 5
    order:
        by: date
        dir: desc
    pagination: true
    url_taxonomy_filters: true
taxonomy:
    category:
        - security
        - manual
        - securityguide
    tag:
        - guide
---

- [This Guide](..)
- [Chapter 1: Introduction to Role-Based Security.](../introduction_too_roleBased_security)
- [Chapter 2: Examples](../examples)
- [Chapter 3: Summarized Rules](../summarized_rules)
- [License](../LicenseUsageAcknowledgements)

This book describes the concept of role-based security and other security features as it has been implemented by coreBOS

This book is based on the official Open Source release. Your individual configuration might be slightly different if your CRM service provider has made changes to the system.

## This Guide's Audience

This guide has been written mainly for coreBOS administrators. We expect that readers will have some familiarity with security management. This guide assumes a basic knowledge of security-related concepts and terms, including authentication, authorization, and roles. Although we provide a description of all features as they are implemented at the release date, this guide may not suffice as your only reference about coreBOS. This depends, on your needs and experience but also on the progress coreBOS makes.

## This Guide's Organization

The first chapter of this book deals with security concept only, i.e. there are no prerequisites in terms of setting up coreBOS. It is helpful to have a basic knowledge of security-related concepts and terms. With regard to the real world example, however, having access to a CRM installation would obviously be an advantage as you could duplicate the setup and investigate your own tweaks to the security configuration. This manual is divided into two parts:

[Chapter 1: Introduction to Role-Based Security.](../02.Introduction%20to%20Role-Based%20Security/)

Describes how role-based security works. Explains in simple terms how to prepare yourself to start working with the CRM's security features. Provides all the information required to understand role-based security supported by the CRM System. Lists all the possibilities of different security settings.

[Chapter 2: Examples](../03.Examples/)

Explains, with examples, how to use the CRM system to assign privileges. Shows real-world examples for setting up complex user hierarchies

## Why Read This Guide?

- This guide is designed to be a clear and supportive reference to the coreBOS security concept

- We hope to answer most of the questions you might have about the user access management at the CRM system. In particular, we cover the following subjects:

- The general approach to the security settings. With all the different settings and their relationship to each other, access right management can be a bit overwhelming at first. We quickly get you up to speed on how the pieces fit together.

- What are the used terms mean?

- How to start using security settings. What should you do first?

- Customizing coreBOS. Each company is different. We explain how you can tailor the security settings to fit your company needs on real-life examples.

- Understanding all of the relationships. Most security settings are somehow related to other settings. These relationships are extensively documented, including the intended purpose. If suitable examples of proper usage are given.

## This Guides' Acknowledgements

This book has been in the works for a long time. It could not have been completed without the help and encouragement of a lot of people.

The vtiger team, its user community, and a number of people contributed technical feedback as this book was being written.

We thank the countless people who contributed to this manual with informal reviews, suggestions, and fixes. While this is undoubtedly not a complete list, this manual would be incomplete and incorrect without the help of Emilio Paolini, Walter Schönenbröcher, Dirk Gorny, Alexander Rothenberg.

------------------------------------------------------------------------

[Next](../02.Introduction%20to%20Role-Based%20Security/) | Chapter 1: Introduction to Role-Based Security.

------------------------------------------------------------------------

© 2006 crm-now
