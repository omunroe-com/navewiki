> (for maintainers only)

First, make sure the version you want to publish is checked out in the current folder. Then run

```bash
cake release
```

one last time to make sure that all the built files (browser compiler, annotated source, etc.) are fully up-to-date. The version in `package.json` should also be the version you intended to publish at (we’ll use `2.99.9` in this example). This is a current release, so you should be on the `master` branch and the `package.json` `name` field should be `coffeescript`.

No going back after you type this:

```bash
npm publish
```

This publishes the current folder to NPM as the version in `package.json`, and updates the `latest` tag to point to it. Then do:

```bash
npm dist-tag add coffeescript@2.99.9 stable
npm dist-tag add coffeescript@2.99.9 next     # Unless there are also beta versions ahead of this version
```

replacing `2.99.9` with the current version number, to update the `stable` and `next` tags too. If you then type `npm dist-tag ls coffeescript` you should see both `latest`, `stable` and `next` pointing to this version.

Let’s tag this commit so that we know exactly which commit was published:

```bash
git tag 2.99.9
```

And push it to the repo (assuming you have the `jashkenas` repo saved as `upstream`):

```bash
git push upstream 2.99.9
```