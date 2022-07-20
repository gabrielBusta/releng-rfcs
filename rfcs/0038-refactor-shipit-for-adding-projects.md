# RFC 38 - Refactor shipit to allow adding new projects without modifying the shipit source code

## Summary

Onboarding new products onto shipit releases requires making changes to the [shipit source code][0].

## Motivation

Refactoring shipit to allow new projects without changes to the shipit source code would reduce the time and effort necessary to get new shipping on with shipit. Currently, adding custom code for each new project could take 2-3 months, quickly adding up to one year of people weeks to add 4-6 projects.

## Out of Scope
- Implementing a generic way to support product addons?

## Details
- Right now, there are two kinds of products using shipit releases
- Mozilla addons & Firefox products
- The Firefox products are Firefox Desktop, Firefox Developer Edition, codename pinebuild, Fenix, Android Components, and Focus (for Android)
- The product and addon releases have phases
- For some reason, xpi and regular (Firefox) product releases are two different models/tables in the database. I need to investigate why
- Each release phase represents a taskgraph
- i.e., shipit is a web service that offers a user interface for relman to schedule & run the taskgraphs for each product/addon
- The configuration for Firefox products is hardcoded in the shipit frontend & backend
- The configuration for Firefox addons is in a source code repository (xpi-manifest)
- Each addon lives in an independent Github repository
- Firefox is similar to the VPN in that it is a multi-platform, stand-alone application
- The Firefox addons are different because they are not stand-alone products (they are part of Firefox)
- Other products besides Firefox might want to implement "addons" (these would probably use a custom implementation per product, not necessarily web extensions)

## Open Questions

1. Lorem ipsum?

[0]: https://github.com/mozilla-releng/shipit
