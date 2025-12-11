# Environment Modules

eX3 uses [environment modules](https://envmodules.io/) to manage reusable version of different software packages.
The [documentation](https://modules.readthedocs.io/en/latest/) is extensive, so advanced users are asked to consult the official documentation
for details. In particular the [cookbook](https://modules.readthedocs.io/en/latest/cookbook.html) will be interesting for advanced users, e.g., to create their own module files.

Here, we only highlight basic usage and eX3 specific elements and recommended practices.

## Basic commands
To know what is already loaded:
```
$> module list
Currently Loaded Modulefiles:
 1) slurm/slurm/21.08.8   2) rustc/1.85.1(default)   3) cuda12.9/toolkit/12.9.1   4) hwloc/gcc/2.12.2+cu129   5) hwloc/gcc/2.12.2-base
```

To search for available modules (by pattern, here 'cuda'):
```
$> module avail cuda
module avail cuda
--------------------------------------------------------------------------------------------------------- /cm/shared/modulefiles ----------------------------------------------------------------------------------------------------------
cuda9.2.OLD/toolkit/9.2.148  cuda10.1/profiler/10.1.243 ...
...
cuda10.1/nsight/10.1.243 ...
```

To load a module
```
$> module load julia/1.11.4
```

or likewise to unload:
```
$> module unload julia/1.11.4
```
