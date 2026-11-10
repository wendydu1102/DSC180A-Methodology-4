# DSC 180A Methodology Assignment 4

**Name:** Shunyi
**Email:** s7du@ucsd.edu  
**Section:** D27  
**Mentor:** Misha Belkin, Tianhao Wang

---

**What is the most interesting topic covered in your domain this quarter?**

The most interesting topic for me was how E-STEER treats emotion as three continuous numbers (valence, arousal, and dominance) instead of a label like "angry" or "sad," and then actually reaches into the model to move along those numbers. Most earlier work I read just tells the model in the prompt to feel a certain way, and one paper we cited found that models mostly ignore numeric emotion values written into a prompt. Sparse autoencoders get around that by breaking the hidden states into features you can find and turn up or down. I also liked that the paper's main claim is that the effect isn't monotonic, so more emotion isn't simply better or worse for reasoning.

**Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

For Q2 I'd like to push the steering experiment past the single dimension we did in Q1. The plan would be to steer valence, arousal, and dominance one at a time on LogiQA across a range of strengths, and see whether the curves are actually non-monotonic like the paper says. I'd also check whether the three directions are really independent, for example by seeing if pushing valence also changes how arousal-like the output reads. If there's time, I'd add a second reasoning benchmark so the result isn't just a LogiQA quirk.

**What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

The biggest change I'd make is collecting more evidence. In Q1 we steered one dimension on a sample of LogiQA questions, and with a small sample it's hard to tell a real trend from noise. I'd run more questions and use several random-feature controls instead of one, so the comparison is fairer. I'd also build the feature prompts from a few different templates instead of only "Right now you are feeling {word}," to make sure the features we find are about the emotion and not the wording of that one sentence.

**What other techniques would you be interested in using in your project?**

A good one is a simpler baseline, like a difference-of-means steering vector built straight from the hidden states (the approach in Turner et al. and the persona vectors paper), to see whether the SAE features actually buy us anything. I'd also compare against just naming the emotion in the prompt, since that's what most prior work does. Beyond that, ablating the VAD features instead of adding them could show whether they matter for reasoning at all. And if a matching SAE exists, trying a larger Qwen model would tell us whether any of this changes with scale.
