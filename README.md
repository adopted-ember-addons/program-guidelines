# Program Guidelines

Sometimes an Ember addon needs a new maintainer. This org was created so that community members can find a new home for their ember addon if they are no longer able to maintain it.

## Getting an addon adopted

- To get your addon adopted, please ping the adopted-ember-addons org owner (`@Melanie#1618`) in the [Ember Discord](https://discord.gg/emberjs) chat in the `#adopted-ember-addons` channel and let them know what repository you'd like to transfer.
- Once they are aware, complete the Addon Transfer checklist (below).
- After the checklist is complete, coordinate a time where you can transfer the repository here on GitHub (the invites time out).
- The org owner is then responsible to transfer the addon to this org (Adopted Ember Addons).

**Warning**: You cannot fork the repository to the same account it was transferred from. Trying to do so will break GitHub's redirect of the old URL to the new.

## Addon Transfer Checklist

These are the things that need to done to transfer your addon:

- [ ] Update the `repository` field of the `package.json` to point to the new location.
- [ ] If any demo URL or homepage is referenced, it should be updated. At the very least, file an issue on the repository so an adopter can fix.
- [ ] Remove inactive maintainers, if reasonable.
- [ ] Ensure release practices are documented.
- [ ] Add the adopted-ember-addons org owner (`melsumner`) to the the package on `npm`. _Make sure they have admin permissions_.

## Adopting an addon

No bots or AI accounts may maintain any addon.

If you want to help maintain an addons:

- Please open an issue that requests to be added as a contributor or ping `@Melanie#1618` on Ember Discord.
- You must have two-factor authentication (2FA) set up and enabled for both GitHub and NPM. This is not optional.

## Standardizing Addon Maintenance

Adopted Ember Addons is a community effort. Maintaining the addons requires people with different backgrounds, experiences and opinions to work together successfully.
As such, we request that addons have similar release processes and at least be on the latest LTS.

### Terminology

This document uses the keywords *must*, *must not*, *should*, *should not* and *may*.

*Must* and *must not* express absolute requirements. Any addon within the org that do not follow these requirements should be updated as soon as possible. A pull request that changes an addon within the org accordingly to these requirements must be merged.

*Should* and *should not* express a recommendation. There may be valid reasons to not follow the recommendation in some edge cases. If so the reasons should be documented.

*May* means that an item is truly optional. It's an individual decision for each addon within the org to implement this item or not. A given decision should not be questioned to avoid changing it back and forth.

> This terminology is based on [RFC 2119](https://tools.ietf.org/html/rfc2119), which is used by many specification documents.

### Prettier

All addon within the org should format the JavaScript code with [Prettier](https://prettier.io/). Prettier should be integrated as an [ESLint](https://eslint.org/) plugin. The setup and configuration should follow the [RFC 628](https://github.com/emberjs/rfcs/pull/628).

> Prettier is an opinionated code formatter. Using it prevents stylistic debates while maintaining addons within the org and helps both developers, reviewers and maintainers to focus on the problems the addon try to solve.

> Prettier has experimental support for Glimmer templates. But it is not stable enough yet to be adopted by addons within the org. It's very likely that we will recommend using it for Glimmer templates as well as soon as it's stable enough. The progress is tracked in [this quest issue](https://github.com/jgwhite/prettier/issues/1).

### Continuous Integration

All addons within the org should run tests and linting automatically for all pull requests _before_ merging them and for the main branch (e.g. `master`) after merging them. They must use GitHub Actions to do so. The GitHub Actions CI workflow may be generated with [create-github-actions-setup-for-ember-addon](https://github.com/jelhan/create-github-actions-setup-for-ember-addon).

### Release process

All addons within the org should document their release process in the `RELEASE.md` file in the root folder of the repository.

For consistency of maintenance, [release-plan](https://github.com/release-plan/release-plan) should be used to automate versioning and package publishing related tasks. 
This allows folks to manage releases fully within GitHub without needing to have access or keys distributed locally on individual's machines. 

Addons may use the setup script [create-release-plan-setup](https://github.com/mansona/create-release-plan-setup) provided by Chris Manson (`@mansona`) to setup `release-plan` and create the release documentation. 

### Versioning

All addons with the org must use [semantic versioning](https://semver.org/) (SemVer).

Dropping support for

- specific versions of Ember packages (`ember-source`, `ember-cli` and `ember-data`) or other peer dependencies,
- node releases or
- browser targets

must be considered as breaking changes. Such changes must not be released in minor or patch versions.
Deprecations may be included in a minor or patch release before removing public APIs in the next major release.

### Changelog

All addons within the org should have a changelog. The changelog may not cover versions that were released before it was introduced.

This is one reason that we request that addons use [release-plan](https://github.com/release-plan/release-plan); it automatically generates a changelog.

### GitHub labels

Issues and pull requests should be labeled. 

For issues, follow the [rules for ember-source repository](https://github.com/emberjs/ember.js/blob/master/CONTRIBUTING.md#issue-labeling).

For pull requests, each PR must to be labeled with at least one of the following labels:

- breaking
- enhancement
- bug
- documentation
- internal

### Code of conduct

The [Ember Community Guidelines](https://emberjs.com/guidelines/) apply to all repositories within the org.
It may be referenced in the repository's README or in a `CODE_OF_CONDUCT.md`.
Even if not included explicitly in a repo within this org, the entire org must follow the Ember Community's code of conduct.
If any participants find themselves unwilling or unable to do so, they will be removed from the project.

### Hosting and Deployments

If the addon provides additional documentation (e.g., not in the README) or demo application, it should be deployed for easier accessibility.
Either [Netlify](https://www.netlify.com) or [GitHub Pages](https://pages.github.com/) should be used for hosting.

## Sponsors

We'd like to thank the companies that support us:

[![GitHub](https://github.githubassets.com/images/modules/logos_page/GitHub-Logo.png)](https://github.com/)

<!-- Netlify badge must be present on README of the repository per requirement of their Open Source plan -->
[![Netlify](https://www.netlify.com/img/global/badges/netlify-color-accent.svg)](https://www.netlify.com)
