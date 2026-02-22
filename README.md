# runlocal-test

Test repository for [runlocal](https://github.com/RahatHameed/runlocal) - a lightweight workflow automation tool.

## Purpose

This repository provides test workflows for the runlocal project. Anyone can use it to test workflow triggering and status checking.

## Available Workflows

| Workflow | Description |
|----------|-------------|
| `test.yaml` | Simple test workflow with configurable message and sleep time |
| `choice-test.yaml` | Workflow with choice inputs to test parameter validation |

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

  choice-test:
    repo: RahatHameed/runlocal-test
    workflow: choice-test.yaml
    branch: main
    defaults:
      environment: Development
      database: MySQL8.0
```

Then run:

```bash
# Basic test workflow
make workflow-trigger project=test
make workflow-status project=test

# Choice test - demonstrates parameter validation
make workflow-trigger project=choice-test param=database="mysql8.0"
# Output: Warning: Correcting 'mysql8.0' to 'MySQL8.0'

# List available workflows and inputs
make workflow-list project=choice-test

# Check all projects at once
make workflow-status-all
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
