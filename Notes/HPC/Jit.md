## Compute Graph

depict  directed acyclic graph 

Node represents Data. Edge represents Compute

## Dynamic Graph

Define by Run

Construct and run for each step

Easy to debug

Update and graph for each compute.

## Static Graph

Define and Run

Define all the compute flow and Run.

May save memory usage.

# Jit

fix torch dynamic into static

## Concept

Just in Time Compilation

```python3
prog = re.compile(pattern)
result = prog.match(string)
```

```
result = re.match(pattern, string)
```

trace

use an input to do forward in model for getting graph structure.