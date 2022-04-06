# GitHub CLI Extension - gh-dash

*Source: [dlvhdr/gh-dash: gh cli extension to display a dashboard of PRs and issues - configurable with a beautiful UI. (github.com)](https://github.com/dlvhdr/gh-dash)*

## Contents

* [gh-dash](GitHub%20CLI%20Extension%20-%20gh-dash.md#gh-dash)
* [Installation](GitHub%20CLI%20Extension%20-%20gh-dash.md#installation)
* [Configuring](GitHub%20CLI%20Extension%20-%20gh-dash.md#configuring)
* [Usage](GitHub%20CLI%20Extension%20-%20gh-dash.md#usage)
* [Author](GitHub%20CLI%20Extension%20-%20gh-dash.md#author)
* [Appendix: Links](GitHub%20CLI%20Extension%20-%20gh-dash.md#appendix-links)

## gh-dash

✨ A GitHub (`gh`) CLI extension to display a dashboard with **pull requests** and **issues** by filters you care about.

<img width="800px" src="https://raw.githubusercontent.com/dlvhdr/gh-prs/main/demo.gif" />

## Installation

Installation requires a minimum version (2.0.0) of the the Github CLI to support extensions.

1. Install the `gh` CLI - see the [installation](https://github.com/cli/cli#installation)

1. Install this extension:
   
   ````sh
   gh extension install dlvhdr/gh-dash
   ````

1. To get the icons to render properly you should download and install a Nerd font from https://www.nerdfonts.com/.
   Then, select that font as your font for the terminal.

<details>
    <summary><strong>Installing Manually</strong></summary>


 > 
 > if you want to install this extension **manually**, do these steps:

1. clone repo
   
   ````bash
   # git
   git clone https://github.com/dlvhdr/gh-dash
   
   # github cli
   gh repo clone dlvhdr/gh-dash
   ````

1. cd to it
   
   ````bash
   cd gh-dash
   ````

1. install it locally
   `bash gh extension install . `

</details>

## Configuring

Configuration is provided within a `config.yml` file under the extension's directory (usually `~/.config/gh-dash/`)

The default `config.yml` file contains:

````yml
prSections:
  - title: My Pull Requests
    filters: is:open author:@me
  - title: Needs My Review
    filters: is:open review-requested:@me
  - title: Subscribed
    filters: is:open -author:@me repo:cli/cli repo:dlvhdr/gh-dash
    limit: 50 # optional limit per section
issuesSections:
  - title: Created
    filters: is:open author:@me
  - title: Assigned
    filters: is:open assignee:@me
  - title: Subscribed
    filters: is:open -author:@me repo:microsoft/vscode repo:dlvhdr/gh-dash
defaults:
  prsLimit: 20 # global limit
  issuesLimit: 20 # global limit
  preview:
    open: true
    width: 60
````

Adding a PR or issue section is as easy as adding to the list of `prSections` or `issueSections` respectively:

* title - shown in the TUI
* filters - how the repo's PRs should be filtered - these are plain [github filters](https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests)

## Usage

Run:

````sh
gh dash
````

Then press <kbd>?</kbd> for help.

## Author

Dolev Hadar dolevc2@gmail.com

---

## Appendix: Links

* *Tools*

*Backlinks:*

````dataview
list from [[GitHub CLI Extension - gh-dash]] AND -"Changelog"
````
