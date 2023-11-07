---
hide:
- toc
---

This homepages main purpuse is to document all my **open source libraries** in one place with the same styling.

I do very often offer implementations for my libraries as optional extensions inside my other libraries and all my libraries do play together very nicely so this page is a good starting point to check out what I do offer.

## :material-library-outline: Projects

Check out the [open source projects](pages/index.md) section to see all the projects that are available and documented here or get an overview below.

## :material-table: Overview

|Image|Library|Description|
|-|-|-|
| **Utilities** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
{% set lib = 'CacheFileProvider' %}{% set type = 'utilities' %}{% include 'index_table_row.md' %}
{% set lib = 'FeedbackManager' %}{% set type = 'utilities' %}{% include 'index_table_row.md' %}
| **Libraries** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
{% set lib = 'Lumberjack' %}{% set type = 'libraries' %}{% include 'index_table_row.md' %}
{% set lib = 'KotBilling' %}{% set type = 'libraries' %}{% include 'index_table_row.md' %}
| **Compose Libraries** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
{% set lib = 'ComposeDialogs' %}{% set type = 'compose' %}{% include 'index_table_row.md' %}
{% set lib = 'ComposePreferences' %}{% set type = 'compose' %}{% include 'index_table_row.md' %}
{% set lib = 'ComposeChangelog' %}{% set type = 'compose' %}{% include 'index_table_row.md' %}
{% set lib = 'ComposeCustomTheme' %}{% set type = 'compose' %}{% include 'index_table_row.md' %}
{% set lib = 'ComposeDebugDrawer' %}{% set type = 'compose' %}{% include 'index_table_row.md' %}

## :material-code-tags: Source Code

[https://github.com/MFlisar/github-docs](https://github.com/MFlisar/github-docs){target=_blank}

## :material-information-box: Usages and State

|Library|Version|Readme|Documentation|Used In|
|:-|:-:|:-:|:-:|:-|
| **Utilities** {: colspan=5 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| CacheFileProvider     | 0.3.0 | ✓ | ✓ | • FeedbackManager |
| FeedbackManager       | 2.0.4 | ✓ | ✓ | • Lumberjack |
| **Libraries** {: colspan=5 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| Lumberjack            | 6.0.2 | ✓ | ✓ | • ComposeDebugDrawer |
| KotPreferences        | 0.3   | ✓ | ✓ | • ComposePreferences<br>• ComposeChangelog<br>• ComposeDebugDrawer |
| KotBilling            | 0.6   | ✓ | ✓ | • ComposeDialogs |
| **Compose** {: colspan=5 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ComposeDialogs        | 1.0.4 | ✓ | ✓ | • ComposePreferences |
| ComposePreferences    | 0.3   |   |   | - |
| ComposeChangelog      | 0.3.2 | ✓ | ✓ | - |
| ComposeCustomTheme    | 0.1.2 | ✓ | ✓ | - |
| ComposeDebugDrawer    | 0.5.1 | ✓ | ✓ | - |