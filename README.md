# GitHub Contributors Action

Automatically generate and update a 'Contributors' section in your repository's `README.md` file.

## Features

- Lists all unique contributors with their avatars and links to GitHub profiles.
- Runs automatically on pushes, keeping your contributors list always up-to-date.
- Easy to integrate into any GitHub Actions workflow.

## Usage

Add this action to your workflow file `.github/workflows/contributors.yml`:

yaml
name: Update Contributors

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Generate Contributors
        id: contributors
        uses: YOUR_GITHUB_USERNAME/gh-contributors-action@v1 # Replace with actual marketplace action id
        with:
          repo-token: ${{ secrets.GITHUB_TOKEN }}
          # Optional: path to README, defaults to README.md
          # readme-path: 'README.md'
          # Optional: header to look for, defaults to '## Contributors'
          # header: '## Our Awesome Contributors'



## Example Output

markdown
## Contributors

<a href="https://github.com/octocat"><img src="https://github.com/octocat.png" width="50px;" alt="octocat"/></a>
<a href="https://github.com/another-user"><img src="https://github.com/another-user.png" width="50px;" alt="another-user"/></a>
<!-- And so on... -->


This action will look for a header (defaulting to `## Contributors`) and replace the content beneath it until the next header or end of file. If the header is not found, it will append the section to the end of the `README.md`.

## Local Development

More details on setting up for local development will be provided soon.

## License

[MIT](LICENSE)
