# Common Pitfalls

## Vague Task Descriptions

Avoid vague task descriptions. Clearly define tasks using natural language to ensure the AI understands the context and requirements. Example:

```bash
# Bad
prompt = "Fix the agent."

# Good
prompt = "Fix the skeptic agent by reviewing the latest PR and ensuring all tests pass."
```

## Lack of Monitoring

Continuously monitor the progress of your tasks. Use tools like tmux for parallelization and debugging. Example:

```bash
tmux attach-session -t my_session
```

## Insufficient Validation

Ensure the output meets the desired criteria. Use validation scripts and manual checks to verify the results. Example:

```bash
python validate_output.py --file output.txt
```

## Ignoring Staging Environments

Use staging environments to test new workflows before deploying them to production. Example:

```bash
open_claw --task "Test new workflow" --staging
```

## Overlooking Parallelization

Leverage parallelization tools like tmux to manage multiple agents efficiently. Example:

```bash
tmux new-session -d -s my_session 'command_to_run'
```