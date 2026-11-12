# squeue and sacct displayed with rich

Install with uv
```
uv tool install rs --from https://github.com/bdvllrs/rich-slurm
```

or directly use with uvx:
```
uvx rs --from https://github.com/bdvllrs/rich-slurm
```

Without uv:

```
pip install --user https://github.com/bdvllrs/rich-slurm
```

## Commands

Display my jobs (equivalent to `sacct -u $USER`)
```
rs me
```

Display job info (equivalent to `sacct -j <job_id>`):
```
rs job <job_id>
```

Display queue (equivalent to `squeue`):
```
rs queue
```

Display my jobs in queue (equivalent to `squeue --me`):
```
rs queue --me
```

All these command can take additional sacct arguments.

Change the displayed columns:

```
rs --columns "Job Id:job_id,Mem:tres.mem" ...
```

The format is `Displayed Name 1:column_id_1,Displayed Name 2:column_id_2`.

Display available columns with: `rs columns`. The column ids mostly correspond to the
keys given by `sacct --json`.

> [!note]
> You can also define the displayed columns with the environment variable `RS_COLUMNS`
(see below).

# Environment variables

Here are available environment variables to configure the tool, with the default values.

Displayed columns (use `rs columns` for available columns):

```
RS_COLUMNS="Job Id:job_id,Mem:tres.mem"
```

Change colors (based on the job status):

```
RS_COLOR_ERROR="bright_red"
RS_COLOR_RUNNING="deep_sky_blue1"
RS_COLOR_COMPLETED="green3"
RS_COLOR_PENDING="medium_purple1"
RS_COLOR_CANCELLED="orange3"
```
[Available colors](https://rich.readthedocs.io/en/stable/appendix/colors.html#standard-colors).

Values used to derive the job's energy consumption:

```
RS_GPU_TDP=700
RS_CPU_TDP=5.5
```
