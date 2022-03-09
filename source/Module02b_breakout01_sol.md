## Cutadapt All Samples Exercise (Breakout)

<br>

Now that we've learned the basics of running Cutadapt, we need to trim all the rest of our samples. If you remember from the Computational Foundations course, we learned about using bash variables. Let's try an exercise where we use a bash variable to trim each one of our FASTQ files.

<br>

### Instructions:

<br>

- One group member should share their screen in the breakout room. If nobody volunteers, a helper may randomly select someone.
- The group members should discuss the exercise and work together to find a solution.
- After a solution is found, allow time for all members to complete the exercise.

<br>

- Review Cutadapt's help page and choose the proper arguments for our Cutadapt command(s).
- Use a bash variable along with Cutadapt to trim all remaining FASTQ files.
- Confirm that we have all of our expected output files.

<br>


> Hint: Using a bash variable allows us to quickly change some arguments in a repeated command, e.g. :
>
> ~~~
> noun="World"
> echo "Hello, $noun!"
> noun="Class"
> echo "Hello, $noun!"
> ~~~

<br>

### Solution - Cutadapt All Samples Exercise

<br>

One solution is to define a bash variable for the sample, use that variable in a Cutadapt command, and then redefine the variable before repeating the Cutadapt command for each change.

    # Define a variable $SAMPLE
    SAMPLE=sample_02
    # Create a command using the variable $SAMPLE
    cutadapt -a AGATCGGAAGAG -A AGATCGGAAGAG -o out_trimmed/${SAMPLE}_R1.trimmed.fastq.gz -p out_trimmed/${SAMPLE}_R2.trimmed.fastq.gz ../reads/${SAMPLE}_R1.fastq.gz ../reads/${SAMPLE}_R2.fastq.gz

    # Redefine the variable and run the command for each additional sample
    SAMPLE=sample_03
    cutadapt -a AGATCGGAAGAG -A AGATCGGAAGAG -o out_trimmed/${SAMPLE}_R1.trimmed.fastq.gz -p out_trimmed/${SAMPLE}_R2.trimmed.fastq.gz ../reads/${SAMPLE}_R1.fastq.gz ../reads/${SAMPLE}_R2.fastq.gz

    SAMPLE=sample_04
    cutadapt -a AGATCGGAAGAG -A AGATCGGAAGAG -o out_trimmed/${SAMPLE}_R1.trimmed.fastq.gz -p out_trimmed/${SAMPLE}_R2.trimmed.fastq.gz ../reads/${SAMPLE}_R1.fastq.gz ../reads/${SAMPLE}_R2.fastq.gz

<br>

Another solution is to create a for-loop with our bash variable and Cutadapt command. E.g.

    for SAMPLE in sample_02 sample_03 sample_04
        do
        cutadapt -a AGATCGGAAGAG -A AGATCGGAAGAG \
        -o out_trimmed/${SAMPLE}_R1.trimmed.fastq.gz -p out_trimmed/${SAMPLE}_R2.trimmed.fastq.gz \
        ../reads/${SAMPLE}_R1.fastq.gz ../reads/${SAMPLE}_R2.fastq.gz
    done

<br>