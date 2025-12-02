stormdb-python
==============

* Python classes for interacting with the STORM database at CFIN.
* A command-line utility (`submit_to_cluster`) for submitting commands for processing on the Hyades-cluster.

__NB! Help with documentation and examples needed!__

Command line utility: `submit_to_cluster`
-----------------------------------------
Install with [uv](https://docs.astral.sh/uv/) by calling

``` bash
uv tool install "stormdb @ https://github.com/meeg-cfin/stormdb-python.git"
```

which creates symlinks in your `~/.local/bin` that lets you use `submit_to_cluster` 

```
usage: submit_to_cluster [-h] [-n N_THREADS] [-q QUEUE] [-m TOTAL_MEMORY] [-p PROJECT] [-w WORKING_DIR] [--noclean] exec_cmd

positional arguments:
  exec_cmd              Full command to execute, in quotes (")

options:
  -h, --help            show this help message and exit
  -n N_THREADS, --n_threads N_THREADS
                        Number of threads to run per process.
  -q QUEUE, --queue QUEUE
                        Name of queue to submit to
  -m TOTAL_MEMORY, --total_memory TOTAL_MEMORY
                        Total amount of memory to request (max 1 thread). Format: M=megabytes, G=gigabytes (e.g. 30G). See docstring of
                        `ClusterJob` for details!
  -p PROJECT, --project PROJECT
                        Name of project (or set MINDLABPROJ)
  -w WORKING_DIR, --working_dir WORKING_DIR
                        Working directory for the job (default: cwd)
  --noclean             Do not clean up the qsub submission script.
```


Submodule: access
-----------------

Home of the `Query`-object, used to send queries to the database (_e.g._, for the purpose of getting a list of included subjects).

```
from stormdb.access import Query
q = Query('MINDLAB20XX_MEG-YourProject')
subjects = q.get_subjects()
for sub in subjects:
  # do some work
```

Submodule: process
-----------------

NEEDS UPDATING, see also `doc`-folder
