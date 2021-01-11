# GrowFlow React Scripts

<img alt="Logo" align="right" src="https://create-react-app.dev/img/logo.svg" width="20%" />

This is GrowFlow's fork of Create React App (more specifically the `react-scripts` package) that allows us to make customizations while avoiding ejecting. This process of creating a `react-scripts` fork is described in [this article](https://create-react-app.dev/docs/alternatives-to-ejecting/).

## Usage

```
npx create-react-app myapp --scripts-version @growflow/react-scripts
```

## Customizations

This `react-scripts` package has the following customizations:

- The package has been renamed to [@growflow/react-scripts](https://www.npmjs.com/package/@growflow/react-scripts).

- It uses [GrowFlow's browser support list](https://github.com/GrowflowTeam/javascript/tree/main/browserslist) for babel compilation by default.

- [.less files](http://lesscss.org/) are supported out-of-the-box.

- Instead of hard-coding the babel config, the Babel Webpack loader is configured to search the consuming app for a babel configuration file. By default, it will use [GrowFlow's babel web configuration](https://github.com/GrowflowTeam/javascript/tree/main/babel-preset). But, it is very easy to override on a per-app basis since the config file is exposed in the app.

- Jest integration has been removed in favor of using [GrowFlow's shared jest configuration](https://github.com/GrowflowTeam/javascript/tree/main/jest) (which can be used for server apps as well).

- The Webpack ESLint integration has been removed. The default template instead will lint via a `package.json` command. There is no reason to slow down the Webpack build to lint with a different set of rules than what the app uses to lint.

- The webpack configuration will make any env variables defined in a `.env` file (or its variations) available to app scripts. This is in contrast to the default behavior which only makes available env variables that are prefixed with `REACT_APP`. This makes things Just Work™ with when using `@growflow/config` with `.growflowrc.js`.

## Maintaining the Fork

We should periodically update our fork of `react-scripts` with changes from the [upstream repository](https://github.com/facebook/create-react-app). This can be done by [configuring your local repository with an upstream remote](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork) and then [syncing the fork](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/syncing-a-fork) with your local repository.

The `master` branch in this repository is configured to follow the upstream's `master` branch. We should merge changes as-is to `master`. Once the remote's changes are in this repository's `master` branch, we can merge `master` to the `growflow` branch. The `growflow` branch is the default branch for this repository and has all of our customizations on that branch.
