<h1>Version Release</h1>

We may automate this in the future, but these are the tasks currently done when generating a new release of Vlad.

- Bump version number in vlad/VERSION.txt
- Merge dev into master branch on vlad repo.
- Tag master branch with new version number.
- Go to github and update the version release with the change logs, these will be taken from the vlad docs changelog.
- Merge dev into master branch on vlad-docs repo.
- Tag version number on vlad-docs repo.
- (optional) Update the Vlad breaking changes site with new breaking changes.
- Spread the news!
