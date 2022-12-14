# Evaluate OpenAI's Whisper on (almost) any Hugging Face Hub dataset

[Whisper](https://openai.com/blog/whisper/) is an automatic speech recognition (ASR) system trained on 680,000 hours of multilingual and multitask supervised data collected from the web.

It enables transcription in multiple languages, as well as translation from those languages into English.

This notebook provides an easy to use interface to evaluate Whisper on audio recordings of text passages that have been sampled from Hugging Face Datasets.

The notebook sets up a Gradio UI that allows the user to:

1. Sample text passages from any Dataset hosted on the Hugging Face Hub
2. Record an audio snippet narrating the text,
3. Transcribe the audio with Whisper
4. Save the audio, transcribed and reference text, and word error rate to [Comet](https://www.comet.com/site/?utm_source=colab&utm_medium=referral&utm_campaign=AMS_US_EN_SNUP_Online_WhisperAI_Notebook) for further evaluation and analysis.

## The Evaluation UI

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DN6/whisper-eval/blob/main/WhisperEval.ipynb)

<img width="1038" alt="whisper-eval" src="https://user-images.githubusercontent.com/7529846/195259707-bc19d0e2-1d0a-4b9e-918f-f686e8bef533.png">

To use the Evaluation UI, you will need a [Comet](https://www.comet.com/site/?utm_source=github&utm_medium=referral&utm_campaign=AMS_US_EN_SNUP_Online_WhisperAI_Notebook) account.

The UI has the following input components

1. The Dataset Name. This is the root name of the text dataset on the Hugging Face hub.
2. Subset. Certain datasets on the Hub are divided into subsets. Use this field to identify the subset, if there is no subset, you can leave it blank.
3. Split. Which split of the dataset to sample from. e.g. `train`, `test` etc.
4. Seed. Set the random seed for sampling. If the seed isn't set, a random one is automatically generated.
5. Audio. One you have sampled a text passage, hit the record button to record yourself narrating the passage.

Finally hit the Transcribe button. That's it! All the relevant data will be logged to Comet for further analysis.

## Logging Evaluations to Comet

The Evaluation UI will log the following data to a Comet Experiment.

You can check out an example project [here](https://www.comet.com/team-comet-ml/evalwhisper/view/RZVIJKQQnFHDe9R9MVnDmt2Hu/panels?utm_source=github&utm_medium=referral&utm_campaign=AMS_US_EN_SNUP_Online_WhisperAI_Notebook)


### Model Parameters
1. Model Type (tiny, base, small, medium etc)
2. Beam Search Width
3. Model Language

### Dataset Parameters

1. Dataset Name
2. Dataset Subset
3. Column in the Dataset that contained the text
4. Split (`train`, `test`,  etc.) of the dataset
5. Seed used to sample the text passage from the dataset
6. Sample Text Length

### Model Metrics

1. Word Error Rate Score

### Evaluation Assets
1. Audio Snippet of the narrated text
2. Reference/Sampled Text
3. Transcribed Text

https://user-images.githubusercontent.com/7529846/195363714-b613755c-b77c-49f4-a1f8-e3c0f5d90be1.mp4
