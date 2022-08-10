# mytasks
PyInvoke tasks setup

1. Add following line to ~/.bashrc: `alias ik="invoke --search-root ~/.invoke"`
2. Create the file `~/.invoke/tasks.py` with the following content:
```python
from pathlib import Path
import sys
from invoke import task


@task(name="list_tasks", default=True)
def _tasks(c):
    """Show the current list of tasks"""
    filepath = Path(__file__)
    with c.cd(filepath.parent):
        c.run(f"{sys.executable} -m invoke -c {filepath.stem} -l")
``` 