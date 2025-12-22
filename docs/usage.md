# Usage

This description intends to offer starting points for eX3 and how to use it.
We will continuously improve this documentation.


## Prerequisites

In order to access eX3, a user will have to file an application and register first. For that purpose
please follow the registration process as documented [here](https://www.ex3.simula.no/access).

Once access has been granted, use the credentials and received login instructions to access the system.


## Logging in
User can login from within Simula or from extern using dnat, where
dnat will drop you on srl-login1:
```
    ssh username@dnat.simula.no -p 60441
```

Within Simula network users can use one of the available login nodes:

- srl-login1.ex3.simula.no (priority)
- srl-login3.ex3.simula.no

So in case srl-login1 should not be available (for whatever reason), srl-login3 serves as fallback.


```{admonition} Hint
:class: tip
Login nodes should be used to launch jobs on other nodes - they are not fit for running heavy workloads on them.
```


## Filesystem

A user has access to the usual home directory on the current login node. In addition, a user
has access to shared storage on /global/D1/.
In addition project specific paths can be created upon request.

| Description | Path |
| ----------- | ---- |
| Home on global share | /global/D1/homes/\<username\> |
| Projects on global share | /global/D1/projects/\<projectname\> |

Since reading from shared filesystem can be a bottleneck for data heavy jobs, a local (faster) NVME disk can be used.
For that purpose, when running a job, prepare data (copy it over from the global share) into /work/*\<username\>*/ on the node that requires the data.

## Getting an overview

In order to gain an overview over available resource on eX3 you can navigate to https://naic-monitor.simula.no - as long as you can access the internal network.
Depending on how you access eX3 you might have to set up port forwarding ssh ... -L 443:443 .

## Running an interactive job

Start an interactive job, e.g., requesting one gpu and minimum 2 cpus
```
    srun -p dgx2q --gres=gpu:1 --mincpus=2 --pty /bin/bash
```

Once you have gained access to the system, check that the GPU is visible, here for an NVidia GPU
```
    $> nvidia-smi -L
    GPU 0: Tesla V100-SXM3-32GB (UUID: GPU-ad466f2f-575d-d949-35e0-9a7d912d974e)

    $> echo $CUDA_VISIBLE_DEVICES
    0
```

