# Program Guidelines
Sometimes an Ember addon needs a new maintainer. In order to make this a consolidated community effort, we started Adopted Ember Addons, an org where community members can find a new home for their ember addon. 

## Getting your addon adopted
- To get your addon adopted, please ping one of the adopted-ember-addons org owners (`@Melanie#1618`, `@Alon#3707`, or `@knownasilya#9990`) in [Ember Discord](https://discord.gg/emberjs) chat and let them know what repo you'd like to transfer. 
- Once they are aware, complete the Addon Transfer checklist (below).
- after the checklist is complete, transfer the repo to them here on Github. 
- The org owner is then responsible to transfer the addon to this org (Adopted Ember Addons). 

** Warning: You cannot ever fork the repo to the same account it was transferred from -- it will break GitHub's redirect of the old URL to the new **

## Addon Transfer Checklist
These are the things that need to done to transfer your addon: 
- [ ] Update the package.json repository field to point to the new location
- [ ] If any demo URL or homepage is referenced, it should be updated. At the very least, file an issue on the repo so the adopter can fix
- [ ] Ensure Release practices are documented
- [ ] Add at least one of the adopted-ember-addons org owners (`melsumner`, `alonbukai`, or `knownasilya`) to the maintainers of the package on `npm`. Remove other maintainers. 

## Adopting an addon
Anyone can submit a pull request to help maintain an addon in this repo! 

It's also possible that you'd like to wear more of an official maintainer hat, and that's cool too! If you want to help maintain one of these addons:
- please open an issue that requests to be added as a contributor or ping melsumner on Ember Discord 
- make sure you have 2FA set up for GitHub

Once we've had a chat, we can add you as a contributor. Easy-peasy!
