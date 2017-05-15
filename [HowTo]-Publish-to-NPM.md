> (for maintainers only)

## Publishing a 1.x release to NPM

First, make sure the version you want to publish is checked out in the current folder. Then run

```bash
cake release
```

one last time to make sure that all the built files (browser compiler, annotated source, etc.) are fully up-to-date. The version in `package.json` should also be the version you intended to publish at (we’ll use `1.99.9` in this example). This is a 1.x release, so you should be on the `master` branch and the `package.json` `name` field should be `coffee-script`.

No going back after you type this:

```bash
npm publish
```

This publishes the current folder to NPM as the version in `package.json`, and updates the `latest` tag to point to it. Then do:

```bash
npm dist-tag add coffee-script@1.99.9 stable
```

replacing `1.99.9` with the current version number, to update the `stable` tag too. If you then type `npm dist-tag ls coffee-script` you should see both `latest` and `stable` pointing to this version.

Let’s tag this commit so that we know exactly which commit was published:

```bash
git tag 1.99.9
```

And push it to the repo (assuming you have the `jashkenas` repo saved as `upstream`):

```bash
git push upstream 1.99.9
```

Since we just published to `coffee-script`, you now need to also publish to the `coffeescript` repo. **Edit `package.json`** and change `name` to just `coffeescript` (no hyphen). Then:

```bash
npm publish
```

We’re not tracking the `stable` tag in this module, so we’re done publishing to `coffeescript`. Finally, reset `package.json`:

```bash
git checkout package.json
```

## Publishing a 2.0.0-beta release to NPM

First, make sure the version you want to publish is checked out in the current folder. Then run

```bash
cake release
```

one last time to make sure that all the built files (browser compiler, annotated source, etc.) are fully up-to-date. The version in `package.json` should also be the version you intended to publish at (we’ll use `2.0.0-beta0` in this example). Since this is a 2.x release, the `package.json` `name` field should be `coffeescript` (no hyphen).

No going back after you type this:

```bash
npm publish --tag next
```

This publishes the current folder to NPM as the version in `package.json`, and updates the `next` tag to point to it. (The `latest` tag should still point to the latest 1.x version). You can type `npm dist-tag ls coffee-script` to confirm.

Let’s tag this commit so that we know exactly which commit was published:

```bash
git tag 2.0.0-beta0
```

And push it to the repo (assuming you have the `jashkenas` repo saved as `upstream`):

```bash
git push upstream 2.0.0-beta0
```

At some point in the future, we may publish 2.x releases to `coffee-script`, in which case the instructions will be more similar to the previous section.