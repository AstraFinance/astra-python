Via https://github.com/plaid/plaid-python/blob/master/PUBLISH.md

# Publish guide

`astra-python` is published via [Pypi][1]

1. **Prepare for release**

Follow these steps sequentially to prepare a new release to Pypi:

- Increment the library version in `astra/version.py` by following [semantic versioning guidelines](https://semver.org/)
- Update the `CHANGELOG.md` with the release version and relevant comments and changes
- Build the updated docs with `make docs`
- Commit the change, create a Pull Request, and obtain approval from a Astra team member
- Merge the commit into `master`, and pull down the latest changes locally from `master`

2. **Publish to Pypi**

Publishing to [Pypi][1] requires `twine` to upload the dist package:

```bash
pip install twine
```

Clean and remove old packages before building a new package with the latest
version and changes. This command removes any existing packages in the `/dist`
directory:

```bash
make package-clean
```

Build a new package into the `/dist` directory:

```bash
make package-build
```

Test and check the new package will render properly on Pypi:

```bash
make package-check
```

Finally, once everything has been tested and you are confident in publishing
the new package to Pypi, run the publish command.

_*Warning: this command is final and will create a new astra release*_

Use `__token__` for the username, and the Astra PyPI token as the password.

```bash
make package-publish
```

3. **Verify publish to Pypi**

Verify that the latest package version you just released matches the version
history at:

```
https://pypi.org/project/astra/#history.
```

[1]: https://pypi.org/project/astra/
