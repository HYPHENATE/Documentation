# Tag Governance

Tag governance helps ensure that the tagging framework remains **consistent, scalable, and useful for reporting** over time.

Without clear governance, tagging systems can quickly become difficult to manage due to:

- duplicate tags
- inconsistent naming
- tags applied in the wrong context
- uncontrolled growth in tag lists

This guide outlines recommended practices for managing tags effectively within the **SimpleTags** framework.

---

## Why Governance Matters

Tags are often used to support:

- reporting and dashboards
- programme and campaign classification
- supporter segmentation
- operational workflows

If tags are poorly managed, reporting becomes unreliable and users may struggle to find the correct tags.

Good governance ensures that:

- tags remain meaningful
- categories stay organised
- reporting remains accurate
- users can easily find the correct tags

---

## Use Categories to Structure Tags

Every tag should belong to a **Tag Category**. Categories provide structure and make it easier for users to find relevant tags.

Example categories might include:

| Category | Example Tags |
|------|------|
| Programme Area | Education, Health, Community Development |
| Campaign Type | Fundraising, Awareness, Event |
| Supporter Interest | Volunteering, Advocacy, Donations |

Try to keep category names **clear and broad enough** to support future growth.

---

## Avoid Duplicate Tags

Before creating a new tag, always check whether a similar tag already exists.

For example:

| Poor Practice | Better Practice |
|------|------|
| Education Programme | Education |
| Fundraising Campaign | Fundraising |
| Community Dev | Community Development |

Consistency in naming improves search results and reporting accuracy.

---

## Use Clear and Consistent Naming

Tags should be **short, descriptive, and consistent**.

Recommended naming practices:

| Guideline | Example |
|------|------|
| Use clear names | `Volunteer` |
| Avoid abbreviations | Use `Community Development` instead of `Comm Dev` |
| Avoid unnecessary prefixes | Use `Education` instead of `Programme - Education` |
| Use singular terms where possible | `Campaign` instead of `Campaigns` |

---

## Restrict Tags to Relevant Objects

Tags can be configured to only appear on specific objects.

For example:

| Tag | Available Objects |
|------|------|
| Programme Area | Account, Opportunity |
| Campaign Theme | Campaign |
| Supporter Interest | Contact |

Restricting tags ensures that users are only presented with **relevant tagging options**.

This reduces confusion and improves data quality.

---

## Review Requested Tags

If the **tag request feature** is enabled, users may submit new tags.

Administrators should review requested tags to determine whether they should be:

- approved and activated
- merged with an existing tag
- rejected

When reviewing a request:

1. Confirm that the tag does not already exist.
2. Ensure the name follows governance guidelines.
3. Assign it to the correct category.

---

## Manage Inactive Tags Carefully

Sometimes tags become outdated or no longer needed.

Instead of deleting tags immediately, consider marking them as **Inactive**.

Benefits include:

- preserving historical reporting
- preventing new usage
- allowing safe retirement of tags

---

## Monitor Tag Growth

Over time the number of tags may increase.

Administrators should periodically review:

- unused tags
- duplicate tags
- categories that have grown too large

A good rule of thumb is that **categories should remain manageable for users to browse**.

---

## Encourage Consistent Usage

Users should be encouraged to:

- apply tags consistently
- avoid unnecessary tagging
- use existing tags whenever possible

Providing simple documentation or training on tagging practices can significantly improve data quality.

---

## Governance Checklist

Use this checklist when managing tags:

| Question | Consideration |
|------|------|
| Does the tag already exist? | Avoid duplicates |
| Is the name clear and consistent? | Ensure readability |
| Is it in the correct category? | Maintain structure |
| Should it be restricted to certain objects? | Improve relevance |
| Does it support reporting or classification? | Ensure value |

---

## Related Documentation

- [Tag Category](/custom-objects/tag-category)
- [Tag](/custom-objects/tag)
- [Tag Link](/custom-objects/tag-link)
- [Tag Meta](/custom-objects/tag-meta)