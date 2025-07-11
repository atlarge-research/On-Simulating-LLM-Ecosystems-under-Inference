# On-Simulating-LLM-Ecosystems-under-Inference

### Abstract

Large Language Models (LLMs) are widely used by our increasingly digitalized society, but raise sustainability, performance, and financial concerns, especially as inference workloads grow. 
To improve LLM Ecosystems, we envision simulators and simulation-based digital twins becoming primary decision-making tools. LLM Ecosystems leverage many heterogeneous components, making simulation a non-trivial, yet critical operation. 
The simulation challenge is exacerbated by the absence of a comprehensive reference architecture of LLM Ecosystems; the lack of such a conceptual model can be costly. Without a reference architecture, even the most experienced stakeholders could tinker in researching, engineering, or maintaining LLM Ecosystems.
In this work, we bring a three-fold contribution to the scientific community. 
Firstly, we synthesize, propose, and validate a reference architecture (RA) of LLM Ecosystems under inference. 
Then, adhering to the reference architecture, we design Kavier, the first simulation instrument able to predict the performance, sustainability, and efficiency of LLM Ecosystems under inference, through discrete-event and (KV)-cache-aware simulation. 
Lastly, through experiments with a prototype and real-world traces, (i) we measure the accuracy of Kavier and the performance in massive-scale simulations, (ii) we multi-tier analyze LLM Ecosystems under various caching policies, and (iii) we compare the performance, sustainability, and efficiency of different KV-Caching policies.

### This repository
This repository is the home of Kavier, the first scientific instrument for predicting performance, sustainability, and efficiency of LLM ecosystems under inference, through discrete-event, cache-aware simulation.

- [Kavier](https://github.com/Radu-Nicolae/Kavier)  
- [LLM Trace Archive](https://zenodo.org/record/15858418)  
- [Tracer](https://github.com/Radu-Nicolae/Tracer)  
- [Thesis (PDF)](thesis.pdf)