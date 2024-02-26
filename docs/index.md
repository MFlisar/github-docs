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
{% set lib = 'ComposeThemer' %}{% set type = 'compose' %}{% include 'index_table_row.md' %}
{% set lib = 'ComposeDebugDrawer' %}{% set type = 'compose' %}{% include 'index_table_row.md' %}

## :material-code-tags: Source Code

[https://github.com/MFlisar/github-docs](https://github.com/MFlisar/github-docs){target=_blank}

## :material-information-box: Usages and State

|Library|Version|Readme|Documentation|Used In|
|:-|:-:|:-:|:-:|:-|
| **Utilities** {: colspan=5 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| CacheFileProvider     | {% set lib = 'CacheFileProvider' %}{% include 'github_release_info.md' %} | ✓ | ✓ | • FeedbackManager |
| FeedbackManager       | {% set lib = 'FeedbackManager' %}{% include 'github_release_info.md' %} | ✓ | ✓ | • Lumberjack |
| **Libraries** {: colspan=5 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| Lumberjack            | {% set lib = 'Lumberjack' %}{% include 'github_release_info.md' %} | ✓ | ✓ | • ComposeDebugDrawer |
| KotPreferences        | {% set lib = 'KotPreferences' %}{% include 'github_release_info.md' %}   | ✓ | ✓ | • ComposePreferences<br>• ComposeChangelog<br>• ComposeDebugDrawer |
| KotBilling            | {% set lib = 'KotBilling' %}{% include 'github_release_info.md' %}   | ✓ | ✓ | • ComposeDialogs |
| **Compose** {: colspan=5 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ComposeDialogs        | {% set lib = 'ComposeDialogs' %}{% include 'github_release_info.md' %} | ✓ | ✓ | • ComposePreferences |
| ComposePreferences    | {% set lib = 'ComposePreferences' %}{% include 'github_release_info.md' %}   | ✓ | ✓ | - |
| ComposeChangelog      | {% set lib = 'ComposeChangelog' %}{% include 'github_release_info.md' %} | ✓ | ✓ | - |
| ComposeThemer         | {% set lib = 'ComposeThemer' %}{% include 'github_release_info.md' %} | ✓ | ✓ | - |
| ComposeDebugDrawer    | {% set lib = 'ComposeDebugDrawer' %}{% include 'github_release_info.md' %} | ✓ | ✓ | - |

[Dependencies as graph](https://viewer.diagrams.net/?tags=%7B%7D&highlight=0000ff&layers=1&nav=1&title=Diagramm.drawio#R7VrbkuI2EP0aHnfKlnzjcQaWTbLZ2qmapLL7qLEbW1ljUbK45esjYxlbMhczwAxV8ITUull9%2BnSrJXp4MFl%2B4WSafGMRpD1kRcseHvYQsh3syJ9CsiolPvJKQcxppDrVghf6HyihpaQzGkGudRSMpYJOdWHIsgxCockI52yhdxuzVF91SmJoCV5Ckral%2F9BIJKU0QH4t%2Fw1onFQr216%2FbHkl4a%2BYs1mm1stYBmXLhFTTqD3mCYnYoiHCn3t4wBkTZWmyHEBaqLXSWDlutKN188kcMtFlwFPwfQTi92D18vj9x%2FTr9I%2FF3%2FAJ4XKaOUlnShfqa8WqUs56e1DMYvfw0yKhAl6mJCxaF9IcpCwRk1Q1j2maDljK%2BHosjggE41DKc8HZL2i0eGEAr2PZ0t6H2tocuIBlQ6T29QXYBARfyS6qFblKx8r8bOSW9UUNpm1ZqlPSQNJTMqIMKN7MXWtSFpQyj1Cs3dLrgIQJjGgKz5zNpbnzlqLlboWuTV1rEYzJLBWGltcmh59ISuNMVkOpRjk3firUR6WJP6qGCY2iYqWtCNYYW5tlKybY5wHJC3SQ3Er3TZCcLRjhS2GEWhiNAKKC0t9IJil%2F8whZH41QB%2B8EWfRYRIBCsSnJcxrqAOl6gyUVP4ryg6tqP1W%2FojxcNroNV1Ulk1tpDCqqP5tt9bB1rRq3E5GczXgIhw1TEB6DOOxkINKiWxvfBn7uFvgqGYeUCDrXY%2BI2TNUKz4zKnW3Mp%2B%2Fp5uP0DbMo961GNSOVMZFtW8ZMjjFTqZnWTGsb2%2Bz77WbntMzuz9nkFfi%2F0jXcuE9w8Ef7BPc2fYLT0Segq%2FIJvuETXJPJXX1CgA07DN7XJQQtq%2FvKxDOHMUgoQ5m73JZbCHwdDow%2B2i30t7gFb63fiM5lMS6KErMnqW2axVWjXKvRfmMoYuvaUKwuBPbDOGCTKcthSEnK4vwO5RYoN7B9HJTtFHg3lJonvcNZn52vB852trwbzkFCshgkOe9g9tpn6CsAc1tivQvMvxKYFHchdyRbx54rQLKdq%2B4JmPA6i4ecLO5wlq2Wd3V4HpfeKk13yG0dVGW0HbJbWXkGTuWWCtz2Zrz2gYw3l4mZaGfja%2FGIpulmikjVTkuTqwPk4buz67o8M2PE5jx3bKLsG4ny5gMPJMoSIrJqdJsWHfLdH4wN6iDL2vtdzpH93f39ZaH84rNm%2BbZ%2FFPu6XC7VtFEMrIjzyXqwMD7AnnWtRcX6wqqPm6R%2BsDz%2FaGKfwLXqqfYQ14I71U6hmutjfZ3%2Bfur0UX9f%2FwtRp31Ddj7qHHXH2oh5rn9SzDuBGuhOjfeghu84%2BjrBAWo41r7%2BF6LGtrvJc1HDM2NKGQJOiCmdKXMCPbq%2BZtzpcRI9bNtc6BA%2F3L18ugw%2FqlvnizzpGSekExIf7fTWiElnf%2BrrzA7nqthhI9vTjeetj3028vSZbPOvBGfjh6MfrRzHfQd733Yzfq54gN54VkLv4ve7Zuf9q7JsbJwabPPxuathm9f6jhlA3vyKLav1X0nL7vVfdfHn%2FwE%3D)
