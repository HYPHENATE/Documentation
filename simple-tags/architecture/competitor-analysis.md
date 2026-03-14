
# Tagging Competitor Analysis

_Last reviewed: March 14, 2026_

## Overview

Organisations often need a flexible way to classify records across multiple objects for reporting, segmentation, or operational workflows.

Before implementing a custom tagging framework like **SimpleTags**, many organisations explore several alternatives.

This page compares common approaches used in Salesforce environments and explains the advantages and limitations of each.

---

# Overview of Approaches

| Approach | Typical Usage | Reporting Capability | Cross-Object Support | Administration |
|------|------|------|------|------|
| Multi-Select Picklists | Simple categorisation | Limited | No | Easy |
| Salesforce Topics | Knowledge & Chatter classification | Limited | Partial | Moderate |
| Salesforce Interest Tags | Experience Cloud personalisation | Limited | No | Moderate |
| Vera Solutions Many2Many | Relationship modelling for NPSP/PMM | Strong | Yes | Moderate |
| **SimpleTags** | Flexible tagging across objects | Strong | Yes | Moderate |

---

# Multi-Select Picklists

Multi-select picklists are one of the most common approaches used when organisations first need tagging behaviour.

## Example

A field called **Funding Themes** might contain values such as:

- Health
- Education
- Climate Action
- Community Development

## Advantages

| Benefit | Description |
|------|------|
| Simple to implement | No additional objects required |
| Native Salesforce feature | Works out of the box |
| Easy to add to page layouts | Minimal configuration required |

## Limitations

| Limitation | Description |
|------|------|
| Poor reporting | Reporting on individual values can be difficult |
| Limited scalability | Managing large lists becomes complex |
| Hard to maintain | Adding or retiring values requires metadata changes |
| No metadata structure | Cannot group values into categories |
| Object-specific | Each object requires its own field |

---

# Salesforce Topics

Salesforce **Topics** allow users to tag content within collaboration features such as Chatter or Knowledge.

## Advantages

| Benefit | Description |
|------|------|
| Native Salesforce feature | No development required |
| User-driven tagging | Users can create topics dynamically |
| Works well with collaboration tools | Integrates with Chatter and Knowledge |

## Limitations

| Limitation | Description |
|------|------|
| Not designed for record classification | Topics focus on content tagging |
| Limited reporting support | Difficult to build structured reports |
| No category structure | Topics are flat |
| Limited configuration | Hard to control usage |

---

# Salesforce Interest Tags

Interest Tags are typically used within **Experience Cloud** to personalise content for users.

## Advantages

| Benefit | Description |
|------|------|
| Supports personalisation | Useful for Experience Cloud experiences |
| Native platform capability | No custom development required |

## Limitations

| Limitation | Description |
|------|------|
| Limited reporting | Not designed for operational reporting |
| Community-focused | Intended mainly for Experience Cloud use |
| Limited object flexibility | Cannot easily apply to multiple record types |

---

# Vera Solutions Many2Many

The Vera Solutions Many2Many model uses a junction object to represent relationships between two records.

## Advantages

| Benefit | Description |
|------|------|
| Strong reporting support | Junction objects allow powerful reporting |
| Flexible relationships | Supports multiple records in both directions |
| Well-established model | Widely used in nonprofit Salesforce implementations |

## Limitations

| Limitation | Description |
|------|------|
| Typically designed for two objects | Not always suited for broad tagging across many object types |
| Requires configuration | Additional objects and relationships must be created |
| Less lightweight | Designed more for structured relationships than lightweight tagging |

---

# SimpleTags

**SimpleTags** provides a flexible tagging framework designed specifically for structured reporting across multiple Salesforce objects.

## Architecture

Tag Category → Tag → Tag Link → Record

## Advantages

| Benefit | Description |
|------|------|
| Strong reporting support | Tags are stored as records and can be used in report types |
| Cross-object tagging | Tags can apply to many objects |
| Category structure | Tags can be grouped for better organisation |
| Flexible configuration | Metadata determines which objects are supported |
| Scalable | Tags can grow with organisational needs |

## Limitations

| Limitation | Description |
|------|------|
| Requires custom components | LWC components provide the UI |
| Requires configuration | Metadata must be defined for supported objects |

---

# Summary

| Solution | Best For |
|------|------|
| Multi-Select Picklists | Simple categorisation |
| Salesforce Topics | Collaboration and content tagging |
| Interest Tags | Experience Cloud personalisation |
| Vera Many2Many | Structured relationships between records |
| **SimpleTags** | Flexible cross-object tagging and reporting |
