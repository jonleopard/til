# Updating and Upgrading with Homebrew

##### Understanding the difference between 'update' and 'upgrade'

`brew update`: This command fetches the newest version of Homebrew and all
formulae ('aka packages') from Github using git.

`brew upgrade`: This command upgrades all of your installed packages.

##### Upgrading individual or all packages

To upgrade a specicific package: `brew upgrade <package_name>`

To upgrade all packages: `brew upgrade`

##### Updating Homebrew and Fetching Package Changes

To update homebrew to the latest version and fetch all package changes upstream:
`brew update`

# Useful tips

##### Installing a package with custom flags

Sometimes you might want to change the default installation procedure for a
package. I'll use [yarn](https://yarnpkg.com/en/docs/install#mac-stable) as an example here.

The `yarn` [installation formulae](https://github.com/Homebrew/homebrew-core/blob/master/Formula/yarn.rb) marks `node` as a dependency, but our system already has node installed via [n](https://github.com/tj/n). If we don't tell homebrew to ignore `node` as a dependency, it will install node for us. This will likely cause issues[^1] as now we would have two node binaries installed in different locations in our `PATH`.

To avoid issues, add some custom flags to your installation command:

`brew install yarn --ignore-dependencies`

This will install the yarn binary without `node`. The only _minor_ issue is that `brew doctor` will report `node` as a missing dependency.

##### Merge Conflicts when Upgrading a package

A few times I've seen some merge conflicts rise up when upgrading a package.

Example:

```
$ brew upgrade spotify-tui
Error: spotify-tui: /usr/local/Homebrew/Library/Taps/rigellute/homebrew-tap/Formula/spotify-tui.rb:2: syntax error, unexpected <<
<<<<<<< HEAD
^~
```

`Homebrew` won't be able to upgrade the package until you try resolving the
merge conflict.

A quick way to try and fix this is by running:
`brew update --force`

And if that is unsuccessful, try:
`brew update-reset`

[^1]: There are no issues with having multiple node binaries installed on your system aslong as they are installed with a version manager such as nvm or n so you have full control on which one is currently being used on your system/project.
