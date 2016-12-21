Experiment: Parsing Targets
===========================

### Requirements ###

* GNU Make 3.81 or higher

### Tested on ###

* Ubuntu 13.10

### Summary ###

This illustrates using implicit rules combined with standard GNU Make built-in
functions to parse any target and execute specific targets based on it.

For example, running `make run-named-daemon` attempts to set Make dependencies
as `_run`, `_named`, and `_daemon`. An implicit pattern is used to catch any
undefined target with an underscore preceding it.

Practical uses are to eliminate duplicate code for targets like `run`,
`run-named`, `run-daemon`, and `run-named-daemon`. Instead, variables can be
set in each individual target that indicate which options should be used for a
common command.

### Examples ###

The following evaluates targets `_dev` and `_run`:

```
make dev-run
```

The following evaluates targets `_prod` and `_run`:

```
make prod-run
```

The following evaluates targets `_%` and `_run`, where
`_%` is handling the case of `_bad`, which doesn't exist:

```
make bad-run
```

The following evaluates target `__no_args`, which is a
catch-all when no targets are provided as arguments:

```
make
```
