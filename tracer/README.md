# Tracer 
_- from 0 to hero, a "eu centrez, eu dau cu capul approach"_

## What we want
We want to trace three types of GPUs. We want to trace at a decent granularity, a good tradeoff between
not losing accuracy because of the too low granularity, but also not overloading the system because of the 
too high granularity.

Columns of the trace:
- timestamp
- prompt id
- input tokens
- output tokens (requested)
- gpu name
- llm name
- inference stage (either prefill or decode)
- gpu utilization
- instant power usage (how many watts)
- and maybe more, if they are relevant

## How to obtain prompts
Well, to send prompts to the LLM we need prompts, for both the prefill-oriented and the decode-orietented tracings.
We want to analyze for 10, 100, 1.000, and maybe 10.000 tokens, for prefill, and for decode.

#### Prefill-oriented
Let's gather prompts. We use Nebula API to generate these prompts. 
We'll generate input prompts of 10, 50, 100, 1.000, and 10.000 tokens. 100 prompts each.

We'll then ask:
```Summarize in 1 word.```

This will lead to a considerable prefill, and a decode length of 1 word.

#### Decode-oriented
Well... this gets simpler. We want to analyze for the same sizes, 10, 50, 100, 1.000, and 10.000 tokens

We'll prompt: ```Generate a <x> word story about <element>```.

We will have a pool of 100 elements, to ensure some randomness.


## How to trace
Now that we have the prompts, we'll next gather the traces. We'll monitor at a quite low granularity and save these
traces in files, one for prefill, one for decoding. 



## Structure of the tracer
```
tracer/
├── README.md              # This overview
├── requirements.txt       # e.g., pandas, requests, python-dotenv, tqdm
├── config.py              # API keys, GPU list, token sizes, sampling rate
├── nebula_client.py       # wraps Nebula API calls
├── prompt_generator.py    # builds prefill/decode prompts for each size
├── sampler.py             # starts `nvidia-smi --loop-ms=10`, parses CSV lines
├── logger.py              # assembles trace rows & writes to CSV
├── main.py                # orchestrates: gen prompts → send to LLM → trigger sampler → collect & save
└── traces/                # output CSVs: prefill_A10.csv, decode_A10.csv
```