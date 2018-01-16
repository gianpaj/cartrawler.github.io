---
title: Introduction
position: 1
type: Android
right_code: |
---

In general we are producing following libraries:

**cartrawler-api.jar** – pure Java library, which contains models and business logic. It talks to the CarTrawler API and provides data through high level classes.

**cartrawler-pay.aar** - separate Android library, which provides logic and interface for native card payments to CarTrawler API. It’s hosted and included separately for PCI compliance reasons.

**cartrawler-app.aar** – Android library, which contains all presentation and resources (configs, strings, theme, drawables, layout files, etc). It also contains cartrawler-api.jar and cartrawler-pay.aar and uses them.