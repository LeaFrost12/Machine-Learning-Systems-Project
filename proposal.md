# Project Title

## Team and Responsibilities
Lea Frost  
Strengths:
- Experience in both software engineering and machine learning research
- Knowledge of machine learning algorithms and the math behind them

I will write weekly progress updates throughout the project in which I will describe my progress and decisions.

## Problem and Motivation

System context: 
- Real-time acoustic identification systems continuously process incoming audio and perform ML inference to identify sounds as they occur.

Affected users:
- Researchers, birders, and conservationists who use continuous real-time acoustic monitoring in noisy and resource-constrained environments. 

Limitations:
- Real-time identification systems must balance detection speed, accuracy, and computational cost.
- Background noise and overlapping bird sounds can reduce accuracy.

Significance:
- Real-time machine learning inference is used in various fields like healthcare, industrial monitoring, and autonomous driving.
- Latency is often a priority in these systems, but there is a tradeoff between accuracy and latency. Decreasing latency usually results in lower accuracy and vice versa. One must find a balance between them when designing a system.

## Research Questions and Hypotheses
RQ1: How does audio window size affect classification performance and time-to-detection?

RQ2: How does prediction frequency affect time-to-detection and computational resource usage?

RQ3: What model configuration provides optimal values for accuracy, latency, and computation cost. 

H1: Smaller window size will decrease time-to-detection but reduce classification accuracy.

H2: Higher prediction frequency will reduce time-to-detection but increase computational cost.

H3: More complex models will improve accuracy but increase inference latency and computational cost.

## Related Work

1. BirdNET: A deep learning solution for avian diversity monitoring, Kahl et al. (2021)  
https://doi.org/10.1016/j.ecoinf.2021.101236  
- **Overview**: This paper details BirdNET, a state-of-the-art Deep Neural Network used for bird sound identification trained on both single-species audio and more complex overlapping soundscapes.
It also found that shorter FFT windows resulted in higher accuracy, supporting that temporal audio configuration can affect accuracy.  
- **Artifact**: I will rely on BirdNET's approach to bird-sound classification, specifically how it acquired the data it used to train the model, the evaluation methods, and the way they pre-processed their data.   
- **Difference**: This paper mainly focused on achieving highest classificiation performance. Unlike what was done in this paper, I will vary the audio processing and model configuration to compare latency, accuracy, and resource usage.   

2. Nighthawk: Acoustic Monitoring of Nocturnal Bird Migration in the Americas, Van Doren et al. (2023)  
https://doi.org/10.1101/2023.05.22.541336  
- **Overview**: Nighthawk adapts the Merlin Sound ID system to nighttime migratory birds by reducing the input window from 3s to 1s, changing the model from MobileNet to ResNet-34 (a more complex model), and setting the prediction interval to 0.2s.  
- **Artifact**: I will reference the paper's audio streaming design (continuous audio with overlapping windows) as well as its approach to adjusting audio and model configuration.  
- **Difference**: This paper only used one static configuration for its results. I will use many different window sizes, prediction intervals, and model choices for my results

3. A real-time bird sound recognition app via deep learning techniques
https://doi.org/10.1007/s11042-026-21211-y  
- **Overview**: Develops a real-time identification system for mobile deployment and compares several different model choices and their effects on prediction performance, inference time, and memory usage.
- **Artifact**: I will consult this paper's comparison of different models' effects on accuracy and efficiency, which demonstrates the importance of model choice in streaming inference systems.
- **Difference**: This paper only studied model configuration whereas I will also be studying audio configuration, specifically window size and prediction frequency.

## Proposed System or Approach


## Evaluation Plan

Research question / experiment
- RQ1: Vary audio window size (1s, 2s, 3s, 5s) while other variables remain constant and evaluate on the same data splits and compare accuracy and time-to-detection.
- RQ2: Vary prediction interval (0.2s, 0.5s, 1.0s) while other variables remain constant and evaluate on the same data splits, comparing time-to-detection and computational utilization.
- RQ3: Train a simple custom CNN, fine-tune a few pre-trained bird identification models, and compare prediction performance, latency, and resource usage. 

Datasets / workloads
- Dataset: BirdSet (Rauch et al., 2025) - Bird-sound recordings on multiple species with background noise. Will select a subset of 20 species for simplification.
- Workload: Labeled recordings will be played as real-time continuous audio stream to simulate microphone recording.

Baseline / Ablations
- Baseline: 3s window, 1.0s prediction interval, medium-sized model
- Ablations: Ablate one variable at a time to find the most optimal choices. Will then select the best combinations of all 3 variables for an overall system comparison.

Controlled / varied factors
- Controlled: Audio window size, prediction frequency/interval, model configuration
- Varied: dataset, data split, preprocessing, hardware, software environment

System/quality metrics
- Quality: Accuracy, precision, recall, F1 (%)
- System: time-to-detection (s), inference latency (ms), CPU utilization (%), memory usage (MB)

Hardware/software
- All experiments will be run on my laptop in a virtual environment.
- Python 3.x, Pytorch, torchaudio, and scikit-learn.

Trails and variability
- Train each configuration with 5 random seeds
- Evaluate each trained model on the same test workload
- 
- Report 95% confidence intervals of metrics where appropriate

Planned plots & tables
- F1 vs window size
- time-to-detection vs window size
- time-to-detection vs prediction interval
- F1 vs prediction interval
- Inference latency vs model configuration
- Memory usage vs model configuration
- Pareto chart of F1 vs time-to-detection, resource usage showed as bar chart
- Summary table of all tested configurations


## Expected Deliverables


## Timeline and Milestones


## Risks and Mitigations


## Reproducibility Plan


## References
