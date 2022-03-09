## Conda Create Exercise (breakout)

<br>

We've covered the basics of Conda, including how to create environments, as well as activate and deactivate them. We'll use those same ideas in this exercise to create a conda environment with all of the software that we've used so far.

<br>

In this exercise, we'll use a special tool that enhances Conda, called Mamba. It is used for environment creation, so you will use it in place of `conda create` in this exercise.

<br>

### Instructions:

<br>

- One group member should share their screen in the breakout room. If nobody volunteers, a helper may randomly select someone.
- The group members should discuss the exercise and work together to find a solution.
- When a solution is found **DO NOT** have all users create the environment. Instead, choose only a few learners in each group to complete this exercise. We do not want to overwhelm the AWS instance.

<br>

- Use `mamba` to create an environment with all of the software that we used today:
    - cutadapt
    - fastqc
    - multiqc
    - star
    - rsem

<br>

> Hint: The tool `mamba` is a drop-in replacement for `conda create` and similar commands.
> It is powerful and fast, which allows us to easily replicate our whole environment from today.
> `conda create` can be very slow or uncooperative when creating environments with certain
> software combinations, and `mamba` helps us get around that in this case.
> The command is exactly the same as a `conda create` command, e.g.:
>
> ~~~
> mamba create -n <env-name> -c <channel> <package1> ...
> ~~~

<br>

### Solution - Conda Create Exercise

<br>

```
# Create a conda environment with Cutadapt, FastQC, MultiQC, STAR, and RSEM.
mamba create -n RSD_environment -c bioconda cutadapt fastqc multiqc star rsem
# Activate the environment and use which to check for software presence
conda activate RSD_environment
which cutadapt
which fastqc
which multiqc
which STAR
which rsem-calculate-expression
# Deactivate the environment
deactivate
```

<br>