# OpenSauced Dev Card Fetcher

This project fetches the [OpenSauced](https://opensauced.pizza) dev card for an OpenSauced user with the GitHub username specified in the GitHub action.

## Usage

To use this action, you need to add the following to a GitHub Actions workflow file.

```yaml
name: Update OpenSauced Dev Card

on:
  schedule:
    - cron: "0 0 * * *" # Run daily at midnight UTC
  workflow_dispatch: # Allow manual triggering

jobs:
  update-dev-card:
    runs-on: ubuntu-latest
    steps:
      - name: Update Dev Card
        uses: nickytonline/open-sauced-dev-card-action@v1.0.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          username: "your_username"
```

We suggest you add this to a workflow file in the `.github/workflows` directory of your repository and call it something like `update-open-sauced-dev-card.yml`.

When the action runs it will generate an image in the root of your repository called `dev-card.png`.

To use the image, you need to add the following markdown to your `README.md` of your [special GitHub repository](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme) for your README. For example, if your GitHub username is `nickytonline`, the repository would be `nickytonline/nickytonline` and the markdown you would add would be:

```markdown
[![My OpenSauced Dev Card](./dev-card.png)](https://oss.fyi/nickytonline)
```
