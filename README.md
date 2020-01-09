<p align="center">
    <img width="250" height="250" src="./sb-mig-logo.png" alt="Logo" />
</p>

## Contents

- [How to install](#how-to-install)
- [Usage](#how-to-install)
- [Schema documentation](#schema-documentation)
  - [Basics](#basics)
- [Roadmap](#roadmap)

---

# How to install and configure

```
npm install --global sb-mig
```

You have to create `.env` file with your variables:

```
STORYBLOK_OAUTH_TOKEN=1234567890qwertyuiop
STORYBLOK_SPACE_ID=12345
STORYBLOK_ACCESS_TOKEN=zxcvbnmasdfghjkl
```

if u want to use experimental feature of downloading `.js` files from seed project (storyblok schema based files, and react-match-storyblok files), you have to add and set github access token

```
GITHUB_TOKEN=1234567890-qwertyuiop
SEED_REPO=https://raw.githubusercontent.com/your-org/your-seed-project/master
```

You can also provide your custom config. To do that u have to create `storyblok.config.js` file in your root catalog with following structure:

```
// storyblok.config.js
module.exports = {
  componentDirectory: 'sbmig/storyblok',
  storyblokApiUrl: 'https://api.storyblok.com/v1',
  oauthToken: process.env.STORYBLOK_OAUTH_TOKEN,
  spaceId: process.env.STORYBLOK_SPACE_ID,
  accessToken: process.env.STORYBLOK_ACCESS_TOKEN,
  githubToken: process.env.GITHUB_TOKEN,
  seedRepo: process.env.SEED_REPO
};
```

You don't need to pass everything to the config file. If u want to have only `componentDirectory` as custom below code will be also valid. 

```
// storyblok.config.js
module.exports = {
  componentDirectory: 'storyblok',
};
```

## Usage

```
        _                           _
  ___  | |__            _ __ ___   (_)   __ _
 / __| | '_ \   _____  | '_ ` _ \  | |  / _` |
 \__ \ | |_) | |_____| | | | | | | | | | (_| |
 |___/ |_.__/          |_| |_| |_| |_|  \__, |
                                        |___/
Usage: sb-mig [options]

Options:
  -V, --version                                               output the version number
  -h, --help                                                  output usage information
    * -M, --migrate <component-name>                              Migrate single component using schema
    * -S, --sync                                                  Sync all component from schema
  -a, --all-components                                        Get all components
  -c, --component <component-name>                            Get single component by name
  -q, --all-presets                                           Get all presets
  -p, --preset <preset-id>                                    Get preset by id
  -d, --component-presets <component-name>                    Get all presets for single component by name
  -z, --get-sb-test-component <storyblok-component>           Get test storyblok schema based component
  -x, --get-react-test-component <storyblok-react-component>  Get test react matching to schema based component
  -d, --debug                                                 Output extra debugging
  



  * - experimental feature, use with caution
```

# Schema documentation:

## Basics
This is basic look of the schame based `.js` file which will map to `Storyblok` component
```
module.exports = {
  name: "text-block",
  display_name: "Text block",
  is_root: false,
  is_nestable: true,
  component_group_name: "Some group",
  schema: {
    title: {
      type: "text",
    },
  }
};
```

## Roadmap:

- [ ] Upload presets
- [x] Sync single component
- [x] Sync all components
- [x] Sync components using schema based .js file (based on idea from [storyblok-migrate](https://github.com/maoberlehner/storyblok-migrate))
- [x] Component groups

General, purpose of this package is to manage creation and maintainance of components and other stuff, from code/command line.
To be able to create whole space and basic structure of the project without using GUI.
