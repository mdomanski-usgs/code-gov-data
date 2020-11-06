# code-gov-data

Data used by Code.gov

## Setup instructions

To run this app locally you'll need a Code.gov API key. If you don't have one, go to the [https://developers.code.gov/key.html](https://developers.code.gov/key.html) to obtain one.

Once you have an API key, clone the repo and run the `npm install` command in the project's root directory to install all of the project’s dependencies.

Run `cp env.example .env` to create a template .env file in the root directory of the project

Replace “[your api key goes here]” in the .env file with your API key

## Filters

This repository is used to generate the repos.json and tasks.json files that populate the filters on the [browse projects page](https://code.gov/browse-projects?page=1&size=10&sort=data_quality) and the [open tasks page](https://code.gov/open-tasks?page=1&size=10) of ‘code-gov-front-end’.

### Generating new filters

Create a feature branch using Code.gov naming convention (e.g., jrc-update-filters). If there are no filter updates to commit and merge with master, the feature branch can be deleted.

Run the `npm run generate` terminal command which runs 2 commands:

- [ ] `npm run build-filters’ creates the filters/repos folder with the filters of the [browse projects page](https://code.gov/browse-projects?page=1&size=10&sort=data_quality)
- [ ] `npm run build-task-filter-data’ creates the filters/tasks folder with the filters of the [open tasks page](https://code.gov/open-tasks?page=1&size=10)

Once the script has finished, execute `git status` to see if any of the data changed. If so, commit the changes and submit a PR to master. These changes will not be reflected on Code.gov until a new release of code.gov is deployed following the instructions in the [Front End Release Management](https://github.com/GSA/code-gov-front-end/wiki/Front-end-release-management) wiki page of [`code-gov-front-end`](https://github.com/GSA/code-gov-front-end).

## name_with_owner.txt [DEPRECATED]

This text file includes all of the names of the Open Source repos on Code.gov. It is generated by extracting the name_with_owner column from code-gov-gh-repos-stats.csv

Generated by running `awk -F "\"*,\"*" 'NR>=2 { print $4 }' code-gov-gh-repos-stats.csv > name_with_owner.txt`
