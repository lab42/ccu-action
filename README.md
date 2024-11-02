# Conventional Commit PR Title Validator

This GitHub Action validates Pull Request titles to ensure they follow the [Conventional Commits](https://www.conventionalcommits.org/) specification. It uses the [CCU (Conventional Commit Util)](https://github.com/lab42/ccu) tool to enforce structured and compliant commit messages.

## Configuration

The action can be customized using the following inputs:

| Input    | Description                               | Required | Default                                                           |
|----------|-------------------------------------------|----------|-----------------------------------------------------------------|
| `type`   | Regular expression for commit type        | No       | `build\|chore\|ci\|docs\|feat\|fix\|perf\|refactor\|revert\|style\|test` |
| `topic`  | Regular expression for commit topic       | No       | `(\([a-zA-Z0-9\-\.]+\))?(!)?`                                   |
| `message`| Regular expression for commit message     | No       | ` .*`                                                           |

### Example

```yaml
name: Validate PR Title
on:
  pull_request:
    types: [opened, edited, synchronize, reopened]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - name: Validate PR Title
        uses: lab42/ccu-action@main
        with:
          type: 'feat|fix|chore'
          pr_title: ${{ github.event.pull_request.title }}
```

## Valid PR Title Examples

- `feat: add new feature`
- `fix(auth): resolve login issue`
- `docs: update README`
- `chore(deps): update dependencies`
- `feat!: breaking change in API`

## Contributing

I welcome contributions to this project! If you have ideas for new features or improvements, please submit a feature request or contribute directly to the project.

## License

This project is licensed under the [MIT License](LICENSE).
