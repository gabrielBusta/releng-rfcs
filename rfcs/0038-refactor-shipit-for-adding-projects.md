# RFC 38 - Refactor shipit to allow adding new projects without modifying the shipit source code

## Summary

Onboarding new products onto shipit releases requires making changes to the [shipit source code][0].

## Motivation

Refactoring shipit to allow adding new projects without changes to the shipit source code would reduce the time and effort necessary to get the latest Mozilla products shipping with shipit. Currently, adding custom code for each new project could take 2-3 months, quickly adding up to one year of people weeks to add 4-6 projects.

## Out of Scope
- Implementing a generic way to support product addons
- Implementing a generic way to expose phase artifacts in shipit

## Details
- Right now, there are two kinds of products using shipit releases
- Mozilla addons & Firefox products
- The Firefox products are Firefox Desktop, Firefox Developer Edition, Fenix, Android Components, and Focus (for Android)
- The product and addon releases have phases
- Each release phase represents a taskgraph
- i.e., shipit is a web service that offers a user interface for relman to schedule & run the taskgraphs for each product/addon
- The configuration for Firefox products is hardcoded in the shipit frontend & backend
- The configuration for Firefox addons is in a source code repository (xpi-manifest)
- Each addon lives in an independent Github repository
- Firefox is similar to the VPN in that it is a multi-platform, stand-alone application
- The Firefox addons are different because they are not stand-alone products (they are part of Firefox)
- Other products besides Firefox might want to implement "addons" (these would probably use a custom implementation per product, not necessarily web extensions)
- Releases are kept in a different table from xpi releases
- The reason xpi releases are in a different table is that addons need to store two revisions. The revision of the addon itself and the revision of the addon configuration in xpi-manifest
- The release table is a better starting point for a generic releases table that can support products besides Firefox
- We need to refactor shipit, so every bit of configuration related to products is in the database
- We need to refactor the frontend to increase the re-usability of the release/phase views
- We could add a way to configure "phase artifacts" for the products (maybe a pop-up of artifact links on the phases?)
- We need to re-design the shipit frontend a bit (we could add a product selection dropdown)
- We need to add pages and APIs to add, delete and update product configuration
- We could add the APIs and use them without a UI, sending them posts through an HTTP client like Postman

## Open Questions

1. Lorem ipsum?

[0]: https://github.com/mozilla-releng/shipit
