# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

## [1.0.0](https://github.com/csshugs/FluidMS/compare/0.2.3...1.0.0) (2023-02-14)


### ⚠ BREAKING CHANGES

* FluidMS now uses Dart Sass, which requires the app
using FluidMS to also use Dart Sass.
* run `npm install` to update dependencies

### Features

* use native `clamp()` function ([28a2e60](https://github.com/csshugs/FluidMS/commit/28a2e60f888cc1e72216a35e8bbbbce698a27b36))



### [0.2.3](https://github.com/csshugs/FluidMS/compare/0.2.2...0.2.3) (2022-11-10)


### Bug Fixes

* enable in shadow DOM ([39d07df](https://github.com/csshugs/FluidMS/commit/39d07dfb3baa98df4efa133d79a4db04850feb62))

### [0.2.2](https://github.com/csshugs/FluidMS/compare/0.1.1...0.2.2) (2020-05-18)


### Features

* make config adjustable ([#27](https://github.com/csshugs/FluidMS/issues/27)) ([7f6681a](https://github.com/csshugs/FluidMS/commit/7f6681a752a1a4f4f80d8b808d32ca942b322767))

### [0.2.1](https://github.com/csshugs/FluidMS/compare/0.1.1...0.2.1) (2020-05-04)


### Refactor

* comply with official else-if notation ([41de11a](https://github.com/csshugs/FluidMS/commit/41de11a1e39433e71e175759d9eb0727777883a9))

## [0.2.0](https://github.com/csshugs/FluidMS/compare/0.1.1...0.2.0) (2020-02-03)


### ⚠ BREAKING CHANGES

* the name of the `$ms` argument for the
`fluidms-font-size()` mixin has changed to `$font-size` to make
it more natural to use if a custom font-size is used.
* rename `$FLUIDMS-GLOBAL-CONFIG` to `$FLUIDMS-CONFIG`
as the uppercase notation already indicates its global scope.


### Bug Fixes

* use correct punctuation ([f98a4fa](https://github.com/csshugs/FluidMS/commit/f98a4fa))
* webserver not serving `index.html` on baseUrl ([#13](https://github.com/csshugs/FluidMS/issues/13)) ([d374247](https://github.com/csshugs/FluidMS/commit/d374247))


### Documentation

* enhance contributing guidelines ([50273b4](https://github.com/csshugs/FluidMS/commit/50273b4))
* provide automatic changelog generation ([#7](https://github.com/csshugs/FluidMS/issues/7)) ([e6a3be6](https://github.com/csshugs/FluidMS/commit/e6a3be6))
* add sassdoc integration ([7152506](https://github.com/csshugs/FluidMS/commit/7152506))


### Features

* add feature flag for baseline grid ([#2](https://github.com/csshugs/FluidMS/issues/2)) ([45f2b2b](https://github.com/csshugs/FluidMS/commit/45f2b2b))
* add line-height ratio ([#18](https://github.com/csshugs/FluidMS/issues/18)) ([ba469b3](https://github.com/csshugs/FluidMS/commit/ba469b3))
* allow custom font-sizes ([b438492](https://github.com/csshugs/FluidMS/commit/b438492))
* stop shrinking of small type on larger viewports ([#21](https://github.com/csshugs/FluidMS/issues/21)) ([4ae74f1](https://github.com/csshugs/FluidMS/commit/4ae74f1))
