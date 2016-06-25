# changelog plugin

[![fastlane Plugin Badge](https://rawcdn.githack.com/fastlane/fastlane/master/fastlane/assets/plugin-badge.svg)](https://rubygems.org/gems/fastlane-plugin-changelog)

## Getting Started

This project is a [fastlane](https://github.com/fastlane/fastlane) plugin. To get started with `fastlane-plugin-changelog`, add it to your project by running:

```bash
fastlane add_plugin changelog
```

## About changelog

This plugin is inspired and based on [Keep a CHANGELOG](http://keepachangelog.com/) project. [Keep a CHANGELOG](http://keepachangelog.com/) proposes a standardised format for keeping change log of your project repository in CHANGELOG.md file. This file contains a curated, chronologically ordered list of notable changes for each version of a project in human readable format.

Since [Keep a CHANGELOG](http://keepachangelog.com/) project proposes a well-defined structure with _sections_ (e.g.: `[Unreleased]`, `0.3.0]`) and _subsections_ (`Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`) it opens up an opportunity to automate reading from/writing to CHANGELOG.md with [`fastlane`](https://fastlane.tools). 

## Getting started
1. `cd` to your project folder
2. `touch CHANGELOG.md`
3. open CHANGELOG.md in your favourite text editor
4. paste the following: `## [Unreleased]`

## Actions

### read_changelog

Reads the content of a section from your project's `CHANGELOG.md` file. `CHANGELOG.md` must follow structure proposed by [Keep a CHANGELOG](http://keepachangelog.com/) project. 

``` ruby
read_changelog	# Reads the "Unreleased" section from CHANGELOG.md in your project's folder
```

``` ruby
read_changelog(
  changelog_path: './custom_folder/CHANGELOG.md',	# Specify path to CHANGELOG.md
  section_identifier: '[Unreleased]',	# Specify what section to read
  excluded_markdown_elements: '["###"]'	# Specify which markdown elements should be excluded
)
```
 
 Use the output of this action in conjunction with for example [`pilot`](https://github.com/fastlane/fastlane/tree/master/pilot#uploading-builds) to upload your change log to TestFlight or with [`github_release`](https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Actions.md#github-releases) to create a new release on Github.
 
### write_changelog
**Coming soon**


## Example
As a developer you have to **remember to keep your CHANGELOG.md up-to-date** with whatever features, bug fixes etc. your repo contains and let [`fastlane`](https://fastlane.tools) to do the rest. 

``` ruby
lane :beta do
  gym
  changelog = read_changelog
  pilot(changelog: changelog)
  # write_changelog
end
```

<Check out the [example `Fastfile`](fastlane/Fastfile) to see how to use this plugin. Try it by cloning the repo, running `fastlane install_plugins` and `bundle exec fastlane test`. 

**Note to author:** Please set up a sample project to make it easy for users to explore what your plugin does. Provide everything that is necessary to try out the plugin in this project (including a sample Xcode/Android project if necessary)>

//## Run tests for this plugin

To run both the tests, and code style validation, run

````
rake
```

To automatically fix many of the styling issues, use 

rubocop -a

//


## Issues and Feedback

For any other issues and feedback about this plugin, please submit it to this repository.

## Troubleshooting

If you have trouble using plugins, check out the [Plugins Troubleshooting](https://github.com/fastlane/fastlane/blob/master/fastlane/docs/PluginsTroubleshooting.md) doc in the main `fastlane` repo.

## Using `fastlane` Plugins

For more information about how the `fastlane` plugin system works, check out the [Plugins documentation](https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Plugins.md).

## About `fastlane`

`fastlane` is the easiest way to automate building and releasing your iOS and Android apps. To learn more, check out [fastlane.tools](https://fastlane.tools).
