# Program Guidelines

Sometimes an Ember addon needs a new maintainer. In order to make this a consolidated community effort, we started Adopted Ember Addons, an org where community members can find a new home for their ember addon.

## Getting your addon adopted

- To get your addon adopted, please ping one of the adopted-ember-addons org owners (`@Melanie#1618`, `@Alon#3707`, or `@knownasilya#9990`) in the [Ember Discord](https://discord.gg/emberjs) chat in the `#adopted-ember-addons` channel and let them know what repository you'd like to transfer.
- Once they are aware, complete the Addon Transfer checklist (below).
- After the checklist is complete, transfer the repository to one of them here on GitHub.
- The org owner is then responsible to transfer the addon to this org (Adopted Ember Addons).

**Warning**: You cannot ever fork the repository to the same account it was transferred from. Trying to do so will break GitHub's redirect of the old URL to the new.

## Addon Transfer Checklist

These are the things that need to done to transfer your addon:

- [ ] Update the `repository` field of the `package.json` to point to the new location.
- [ ] If any demo URL or homepage is referenced, it should be updated. At the very least, file an issue on the repository so the adopter can fix.
- [ ] Ensure Release practices are documented.
- [ ] Add the adopted-ember-addons org owners (`melsumner`, `alonbukai`, or `knownasilya`) to the maintainers of the package on `npm`. Make sure they have all admin permissions. Remove inactive maintainers, if reasonable.

## Adopting an addon

Anyone can submit a pull request to help maintain an addon in this repository!

It's also possible that you'd like to wear more of an official maintainer hat, and that's cool too! If you want to help maintain one of these addons:

- Please open an issue that requests to be added as a contributor or ping `@Melanie#1618` on Ember Discord.
- Make sure you have two-factor authentication (2FA) set up and enabled for GitHub.

Once we've had a chat, we can add you as a contributor.

## Standardizing Addon Maintenance

Adopted Ember Addons is a community effort. Maintaining the addons requires people with different backgrounds, experiences and opinions to work together successfully. Setting shared conventions for some aspects of addons maintenance provides a reference point how common problems should be solved within the org. This ensures a consistent experience for contributors and maintainers across the different addons within the org. It also reduces the entry barrier for new contributors and helps them getting started by providing clear guidance. Additionally it reduces the risk of [bike-shedding](https://en.wikipedia.org/wiki/Law_of_triviality) by providing a dedicated place to discuss and change patterns and practices.

### Terminology

This document uses the keywords *must*, *must not*, *should*, *should not* and *may*.

*Must* and *must not* express absolute requirements. Any addon within the org that do not follow these requirements should be updated as soon as possible. A pull request that changes an addon within the org accordingly to these requirements must be merged.

*Should* and *should not* express a recommendation. There may be valid reasons to not follow the recommendation in some edge cases. If so the reasons should be documented.

*May* means that an item is truly optional. It's an individual decision for each addon within the org to implement this item or not. A given decision should not be questioned to avoid changing it back and forth.

> This terminology is based on [RFC 2119](https://tools.ietf.org/html/rfc2119), which is used by many specification documents.

### Prettier

All addon within the org should format the JavaScript code with [Prettier](https://prettier.io/). Prettier should be integrated as an [ESLint](https://eslint.org/) plugin. The setup and configuration should follow the [RFC 628](https://github.com/emberjs/rfcs/pull/628).

> Prettier is an opinionated code formatter. Using it prevents stylistic debates while maintaining addons within the org and helps both developers, reviewers and maintainers to focus on the problems the addon try to solve.

Prettier should not be used to format templates (`*.hbs`) yet, due to issues with whitespace.

> Prettier has experimental support for Glimmer templates. But it is not stable enough yet to be adopted by addons within the org. It's very likely that we will recommend using it for Glimmer templates as well as soon as it's stable enough. The progress is tracked in [this quest issue](https://github.com/jgwhite/prettier/issues/1).

### Continuous Integration

All addons within the org should run tests and linting automatically for all pull requests _before_ merging them and for the main branch (e.g. `master`) after merging them. They must use GitHub Actions to do so. The GitHub Actions CI workflow may be generated with [create-github-actions-setup-for-ember-addon](https://github.com/jelhan/create-github-actions-setup-for-ember-addon).

### Release process

All addons within the org should document their release process. The documentation should be located in `RELEASE.md` file in the root folder of the repository.

[release-plan](https://github.com/embroider-build/release-plan) should be used to automate versioning and package publishing related tasks. This allows folks to manage releases fully within GitHub without needing to have access or keys distributed locally on individual's machines. For example, `release-plan` will create a preview-PR [like this one](https://github.com/adopted-ember-addons/ember-sortable/pull/536) and once merged, release will happen automatically.

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

> Changelogs are important to communicate end users what is going on with the project. See [keepachangelog.com](https://keepachangelog.com/en/1.0.0/) for additional reasoning.

The changelog should be generated and updated automatically as part of the release process. [`lerna-changelog`](https://github.com/lerna/lerna-changelog) should be used to do so.

> Lerna-changelog generates changelogs based on GitHub pull requests and their labels. Please refer to [it's documentation](https://github.com/lerna/lerna-changelog#lerna-changelog) for more details.

lerna-changelog can be integrated with `release-it` to automatically generate the changelog as part of the release process. Robert Jackson (`@rwjblue`) provides a script to automate the setup for these tools: [create-rwjblue-release-it-setup](https://github.com/rwjblue/create-rwjblue-release-it-setup). It should be used for the setup and as a reference for recommended configuration.

> Please refer to the [documentation of create-rwjblue-release-it-setup](https://github.com/rwjblue/create-rwjblue-release-it-setup#create-rwjblue-release-it-setup) for usage instructions. The script could be rerun on a repository already using lerna-changelog and release-it to update the configuration to the latest recommendations.

### GitHub labels

GitHub issues and pull request should be labeled. It should follow the [rules for ember-source repository](https://github.com/emberjs/ember.js/blob/master/CONTRIBUTING.md#issue-labeling) for issues and [lerna-changelog](https://github.com/lerna/lerna-changelog)'s defaults for pull requests.

### Code of conduct

The [Ember Community Guidelines](https://emberjs.com/guidelines/) apply to all repositories within the org. It may be referenced in the repository's README or in a `CODE_OF_CONDUCT.md`.

### Hosting and Deployments

If the addon provides a documentation or demo application, it should be deployed for easier accessibility. Either [Netlify](https://www.netlify.com) or [GitHub Pages](https://pages.github.com/) should be used for hosting.

## Sponsors

We like to thanks the companies, which infrastructure we could use for free:

[
  ![GitHub](https://github.githubassets.com/images/modules/logos_page/GitHub-Logo.png)
](https://github.com/)

<!-- Netlify badge must be present on README of the repository per requirement of their Open Source plan -->
[
  ![Netlify](https://www.netlify.com/img/global/badges/netlify-color-accent.svg)
](https://www.netlify.com)
