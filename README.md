## Building a Data Analysis pipeline using a shell script tutorial
adapted from [Software Carpentry](http://software-carpentry.org/)

This example data analysis project analyzes the word count for all words in 4
novels. It reports the top 10 most occurring words in each book in a [report](doc/count_report.qmd).

### Current usage:

#### Set-up (first time only)

1. Clone this repo, and using the command line, navigate to the root of this project.

2. Run the following commands to create the conda environment:

```
conda-lock install --name da-pipeline-sh conda-lock.yml
```

#### Run the analysis 

Activate the conda environment:

```
conda activate da-pipeline-sh
```

Count the words:

```
python scripts/wordcount.py \
    --input_file=data/isles.txt \
    --output_file=results/isles.dat
python scripts/wordcount.py \
    --input_file=data/abyss.txt \
    --output_file=results/abyss.dat
python scripts/wordcount.py \
    --input_file=data/last.txt \
    --output_file=results/last.dat
python scripts/wordcount.py \
    --input_file=data/sierra.txt \
    --output_file=results/sierra.dat
``````

Create the plots:

```
python scripts/plotcount.py \
    --input_file=results/isles.dat \
    --output_file=results/figure/isles.png
python scripts/plotcount.py \
    --input_file=results/abyss.dat \
    --output_file=results/figure/abyss.png
python scripts/plotcount.py \
    --input_file=results/last.dat \
    --output_file=results/figure/last.png
python scripts/plotcount.py \
    --input_file=results/sierra.dat \
    --output_file=results/figure/sierra.png
```

Render the report:

```
quarto render report/count_report.qmd
```

### Exercise:

Your task is to add a data analysis pipeline using a shell/bash script!
It should accomplish the same task as outlined in the README.md file when you type:

```
bash runall.sh
```

### Depenedencies
- Quarto
- Python & Python libraries:
    - `click`
    - `matplotlib`
    - `pandas`
