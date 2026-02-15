# runlocal-test

Test repository for [runlocal](https://github.com/RahatHameed/runlocal) - a lightweight workflow automation tool.

## Purpose

This repository provides test workflows for the runlocal project. Anyone can use it to test workflow triggering and status checking.

## Available Workflows

| Workflow | Description |
|----------|-------------|
| `test.yaml` | Simple test workflow with configurable message and sleep time |

## Usage with runlocal

Add to your `projects.yaml`:

```yaml
projects:
  test:
    repo: RahatHameed/runlocal-test
    workflow: test.yaml
    branch: main
    defaults:
      message: "Hello from runlocal!"
      sleep_seconds: "15"
```

Then run:

```bash
make workflow-trigger project=test
make workflow-status project=test
```

## Contributing

Contributions are welcome! Feel free to:

- Add new test workflows
- Improve existing workflows
- Report issues

### Adding New Workflows

1. Fork the repository
2. Create a new workflow in `.github/workflows/`
3. Use `workflow_dispatch` trigger with inputs
4. Submit a pull request

## License

MIT License - see [LICENSE](LICENSE) for details.
