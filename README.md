# Bengali BPE  Tokenizer

In this repository I have built Bengali Tokenizer for inputting text into LLM.

The spaces app for inputting bengali sentence is as below:

![space-app](https://github.com/monimoyd/bengali_bpe_tokenizer/blob/main/screenshot_bengali_tokenizer_spaces_app.png)

Output Compression Ratio: 3.8125

Vocabulary size: 5000

## Base Vocabulary For Bengali
-  List all the unicode characters for Bengali Language
-  Include all the separators
-  Make this whole list as base vocabulary

## Preprocessing Bengali Corpus
- Collect the Bengali corpus data from kaggle
https://www.kaggle.com/code/sayankr007/bengali-text-generation-and-language-modelling/input

- Based on https://www.unicode.org/charts/PDF/U0980.pdf the bengali characters can have unicode values between 0980 to 09FF. Hence, Made a regex pattern to separate bengali words including spaces
    ```
    r""" ?[\u0980-\u09FF]+| ?[^\s]+|\s+(?!\S)|\s+"""
    ```
- Then input this word to train method using Byte-Pair-Encoding algorithm

## Training Methodology
- This method will take the separated words from preprocess step.
- It will pair the characters using BPE
- It will use the get_stats method to pair and find the maximum occuring pairs.
- After finding the most common pair, it will call the merge method to merge the pair with a new token.
- Finally vocabulary gets updated.

## Inference
- It has got encode method which can take the input text and provide the BPE codes
- It has also got decode method which will show the inputted text from BPE codes

## Results
- It has achieved compression ratio of more than 3 in many input text.
- It has resullted 5000 as output tokens consisting the new vocabulary.

## Deployment
- This is deployed in Huggingface Spaces. The link is provided below.

https://huggingface.co/spaces/Monimoy/bengali_bpe_tokenizer 

