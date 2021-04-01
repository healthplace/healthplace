# Playbook

## Ways of Working

Below are some tenets to follow when working together:

* If there is any doubt... any at all... ask for clarification.
* Ensure tickets are always up to date and moved into the correct columns.
* If a ticket doesn't have everything you need to complete it, let it be known
before work is started.

## Branching Strategy

We use [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
as our branching strategy.

The `master` branch is the trunk branch where all work should eventually end up
in.

The `develop` branch is based off of `master` and is where a majority of feature
branches will be branched from.

Each ticket should have its own branch.

Feature branches should either be based off of `develop` or `master`.

Most tickets should have their branch based off of the `develop` branch.

Hotfixes that must be released immediately into production must have their
branch based off of `master`.

## Contribution Guidelines

Follow a [TDD](https://en.wikipedia.org/wiki/Test-driven_development) process to
ensure all work has sufficient automated testing.

When work is completed on your branch, first make sure all automated tests are
passing as well as manual tests; confirming the functionality in the
corresponding ticket has been satisfied.

Raise a PR back into the branch based off of (usually `develop`, but may be
`master` for hotfixes).

Update the corresponding ticket accordingly.

## Definition of Done

Before moving a ticket into review, first ensure:

* All acceptance criteria have been met.
* Relevant automated tests have been written.
* You have performed manual testing to ensure the functionality works as 
expected.
* All automated tests are passing.
* The CI/CD pipeline passes for the PR raised.

## Release Process

Releasing is managed entirely through version control and the CI/CD pipeline.

Releases to the staging environment are triggered via new commits pushed to the
`develop` branch, following a successful pipeline run.

Releases to the RC environment are triggered via new commits pushed to tabyhe
`release/*` branch, following a successful pipeline run.

Releases to the production environment are triggered via new tags (following the
`YYYY.MM.DD.X` format) pushed to the repository, following a successful pipeline
run.

### Tagging Convention

The tagging convention to use for releases is: `YYYY.MM.DD.X`

* `YYYY` - The current year.
* `MM` - The current month.
* `DD` - The current day of the month.
* `X` - The current release number of the day (starting from 1).

Examples of valid tags are:

```
# 1st release of the day for 22nd April 2021
2021.04.22.1

# 2nd release of the day for 22nd April 2021
2021.04.22.2

# 9th release of the day for 1st December 2021
2021.12.01.9
```
