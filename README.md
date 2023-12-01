# Prefix Tuning for Text Generation
## Reference
This is my homework two for advanced nlp class. Below is the description link to it

    https://anoopsarkar.github.io/advanced-nlp-class/hw2.html

## Approach
Utilize prefix tuning library to optimize continuous prompts which guide (distilled) gpt2 to generate certain types of content.

## dataset 
The dataset used for this project was table to text dataset (https://huggingface.co/datasets/e2e_nlg). Hugging Face library was used to load the dataset.

## Default solution model file

The default model file is the `distilgpt2` model file that will be
downloaded when you run `default.py` for the first time.

## Installation

Make sure you setup your virtual environment:

    python3.10 -m venv venv
    source venv/bin/activate
    pip install -U -r requirements.txt

You can optionally copy and modify the requirements for when we
test your code:

    cp requirements.txt answer/requirements.txt

## train
The final model is too big to be uploaded. To train a model

    python3 answer/prefixtune.py -f

About 5 epoches reach the optimum. Best hyper parameters can be found on the function generate() in the file answer/prefixtune.py  


## Inference on the training, validation and testing dataset

To inference on the training, validation and testing dataset

    python3 zipout.py

For more options:

    python3 zipout.py -h


## Check your accuracy on the dataset

To check your accuracy on the dataset:

    python3 check.py

For more options:

    python3 check.py -h

In particular use the log file to check your output evaluation:

    python3 check.py -l log

## Inference and validate on custom dataset

To inference on the custome dataset:

    python3 answer/prefixtune.py -i data/input/custom.txt > output.txt


To check your accuracy on the custom dataset (I assume you provide custom.out for comparsion):

    python3 bleu.py -t data/reference/custom.out -o output.txt


## Data files

The data files provided are:

* `data/train.txt.gz` -- the training data used to train the `answer/default.py` model (`default.py` uses the [huggingface dataset for E2E](https://huggingface.co/datasets/e2e_nlg) to load the data but a copy of the training data is provided just in case).
* `data/input` -- input files `dev.txt` and `test.txt` infected with noise. a subset of `dev.txt` is provided as `small.txt` for development of your solution.
* `data/reference/dev.out` -- the reference output for the `dev.txt` input file
* `data/reference/small.out` -- the reference output for the `dev.txt` input file
