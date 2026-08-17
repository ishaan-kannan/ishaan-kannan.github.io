---
layout: post
title: "Bringing quantum advantage to today's classical world"
description: "A single qubit can help us learn exponentially more from the world around us."
---

<!-- MathJax is loaded here so the inline mathematical notation in this post renders without requiring any site-wide changes. -->
<script>
window.MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']]
  }
};
</script>
<script defer src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

We are classical agents constantly learning from the classical world around us. Every stimulus is a signal containing data which we process through various _receivers_, like our eyes and ears, our phones, and our computer screens; our ability to learn is determined by how well they can relay the content within. Can a quantum machine improve the quality of our interface with the classical world, thereby enhancing the data through which we learn?

### A quantum challenge

At first, extracting information from classical signals seems to be a classical engineering challenge. All parties involved are macroscopic, classical agents; where lies the structure that a quantum machine could exploit? But nearly three decades ago, a simple observation revealed that quantum mechanics may enable improvements to our interfaces with the classical world that are otherwise impossible. Namely, when $N$ quantum components are [entangled](https://en.wikipedia.org/wiki/Quantum_entanglement) and exposed to a classical signal, their response is more than the sum of their parts: they accumulate information about the signal $\sqrt{N}$ times faster than any system of $N$ classical sensors could. This square-root speedup kicked off the study of *quantum metrology*, which seeks to learn features of signals whose structure is already well-known.

Since then, the field of quantum computing has burgeoned, and as quantum scientists have sought to discover applications of quantum machines with genuine societal impact, many proposals have suggested pairing large quantum processors with sensors to realize quantum metrological speedups at scale. Unfortunately, we have identified more obstructions than use-cases in which these proposals enable significant practical impact. Most kinds of realistic noise are now known to destroy the quantum entanglement leveraged by quantum metrology, and in [recent work](https://arxiv.org/pdf/2607.27342) we give rigorous proofs that when realistic noise is non-negligible, the square-root speedup vanishes.

So is this the end of the road? Are the applications of quantum machines (beyond their canonical advantage for cryptanalysis) limited to special and exotic tasks native to quantum physics and relevant only to academic study?

In [new work](https://arxiv.org/pdf/2608.13521), we overturn the common worry that quantum advantage and practical utility may be incompatible. We prove that quantum machines enhance the expressivity of our interfaces with the classical world not only quadratically, but exponentially. Moreover, machines with these capabilities require *far fewer* resources than previously believed: Sridhar Prabhu and the McMahon lab at Cornell built a quantum machine for processing classical signals utilizing only a single qubit, and together we watched as our proofs of exponential quantum advantage happened in real life. Our work gives the first experimentally-validated demonstration that technologically pragmatic objectives, realistic engineering constraints, and rigorous exponential quantum advantages can coincide while interfacing classical learners with classical signals.

### A broader perspective

How did we obtain a massive exponential speedup, despite proving that a smaller square-root improvement was already impossible? We tackled a messier problem than quantum metrology usually addresses. 

Conventional quantum metrology usually assumes that we know everything about a classical signal (its exact waveform, timing, power, etc.) except for a few well-defined parameters, and in that setting a square-root speedup really is the best we can ever hope for. But real-world signals are not this clean: we often know very little about them, and we rarely control their source. The practical goal, then, is to extract as much as we can when an unstructured signal passes by and persists for unknown time.  Counterintuitively, this messier, more realistic regime, full of randomness, noise, time-varying drift, and overlapping signals, is exactly where exponential quantum advantages emerge.

In these practical applications, we're usually interested in specific _features_ of a signal rather than a complete reconstruction. One ubiquitous example is the Fourier coefficient: complicated signals are often composed of many overlapping signals of different frequencies, and the Fourier coefficients tell us how dominant each constituent is. Because of this, estimating Fourier coefficients is a central goal of [signal processing](https://en.wikipedia.org/wiki/Signal_processing). So we asked: if we know nothing about a signal (which could be very faint, random, or time-varying), how can we learn important features such as Fourier coefficients and beyond?

<figure style="margin: 2.6rem 0;">
  <a href="/assets/blog/bringing-quantum-advantage/img-1.png" target="_blank" rel="noopener" style="display:block;">
    <img
      src="/assets/blog/bringing-quantum-advantage/img-1.png"
      alt="Schematic of classical signals carrying information from the physical world to a receiver."
      style="display:block; width:auto; max-width:88%; max-height:500px; height:auto; margin:0 auto;"
    >
  </a>
</figure>

### Extracting information in a quantum domain

The usual way to measure these features is to take lots of snapshots of the signal, then apply a classical algorithm to estimate the feature from the resulting data. As with machine learning, the amount of data you need depends on how well it describes the feature of interest. But for many interesting features and realistic signals, data collected in this way correlates to the information of interest very poorly, so we need to make lots of measurements as quickly as possible. That is, the signal is an unobserved physical object containing lots of data; our conventional interface with it severely attenuates the amount of data we can actually extract.

To understand the origin of this attenuation, let's consider a simple example. Suppose I gave you slightly noisy samples of data $x$, whose true value (unknown to you) is $5$, and asked you to estimate the value of $10^{x}$ to within $1\%$ error. If each shot of $x$ is $1\%$ noisy, note that your estimated error amplifies massively: $10^5$ and $10^{5.05}$ are about $12\%$ apart! In this sense, the data you observe is poorly correlated to your feature of interest, and you need lots of shots of $x$ to make your estimate of $10^x$ accurate.

We proposed _quantum feature sensing_ (QFS), a family of quantum-enhanced algorithms that estimate features using exponentially fewer measurements than conventional interfaces require. The key observation of QFS is that the classical processing normally applied _after_ making measurements can in fact be performed _before_ measurement — in the quantum domain. In the language of the example above: QFS takes the signal $x$ and maps it to $10^x$ before you ever make a noisy measurement. Whereas conventional measurements previously produced $1\%$-noisy estimates of $x$, QFS directly produces $1\%$-noisy samples of $10^x$.

To perform this quantum preprocessing, we take a conventional receiver and add to it a single qubit. Applying a sequence of controlled operations between the qubit and the receiver places the receiver in a carefully-designed state of quantum superposition. Unlike a classical receiver, which reacts to the signal itself (the $x$ above), this superposition loses its responsiveness to the raw value of $x$ while becoming extremely sensitive to the feature of interest (e.g. $10^x$). We build out a complete framework, called Quantum Phase-Space Inference (Q$\Psi$) to systematically design these strategies and prove their optimality.

<figure style="margin: 2.6rem 0;">
  <a href="/assets/blog/bringing-quantum-advantage/img-2.png" target="_blank" rel="noopener" style="display:block;">
    <img
      src="/assets/blog/bringing-quantum-advantage/img-2.png"
      alt="Comparison of quantum feature sensing, which filters a signal before measurement, with conventional sensing."
      style="display:block; width:auto; max-width:88%; max-height:500px; height:auto; margin:0 auto;"
    >
  </a>
</figure>

### Exponential quantum advantage in learning from the physical world

Using Q$\Psi$ and quantum feature sensing, we discover that quantum machines available today can exponentially enhance our ability to process the data contained in classical signals. We start by rigorously proving that a quantum feature sensor can estimate Fourier coefficients exponentially more efficiently than any conventional sensor.  This suggests a number of applications in radar, astronomy, and cosmology, fields which often use electromagnetic receivers to analyze a source via subtle irregularities in the electromagnetic signals it emits. 

The exponential advantages don't end there. Rapid advances in quantum error correction now make it likely that only a few years from now, quantum devices like the one used in our experiments may be equipped with so-called *logical* qubits, which are protected by quantum error correction so that the quantum data they store can persist for long times in the presence of noise.  We showed that short-lived, noisy receivers can be massively enhanced by coupling them to a single long-lived logical qubit. If you hand me a receiver only capable of instantaneous measurements before it becomes too lossy, I can couple it to a logical qubit which retains a quantum memory of its interactions with the receiver. By doing so, I provably gain the ability to learn features of time-varying signals exponentially faster than is possible in the absence of quantum memory resources.

Continuing in this manner, our work establishes a *hierarchy of quantum resources*. The message is that by taking an sensing device that lives at one level of the hierarchy, and adding a single quantum resource (such as a single qubit, a memory, or more controlled operations), a new regime of classical signal data becomes exponentially easier to access. Through this hierarchy, the incremental development of quantum technology will continue to yield provable exponential improvements in our ability to extract data from the natural world. Even in our preliminary proof-of-concept experiments, the quantum advantage could be as large as a factor of ten million times fewer measurements used.

<figure style="margin: 2.6rem 0;">
  <a href="/assets/blog/bringing-quantum-advantage/img-3.png" target="_blank" rel="noopener" style="display:block;">
    <img
      src="/assets/blog/bringing-quantum-advantage/img-3.png"
      alt="Hierarchy of quantum resources and the exponential sensing advantages enabled by additional quantum capabilities."
      style="display:block; width:auto; max-width:88%; max-height:500px; height:auto; margin:0 auto;"
    >
  </a>
</figure>

### The future of quantum technology

The prevailing folklore in the field of quantum computing has been that massive quantum algorithmic speedups for practical tasks will not be realized until we build a full-fledged quantum computer with hundreds of error-corrected logical qubits. And even then, it has been unclear precisely where the gains would come. We have now given proof-of-principle demonstrations that a quantum processor of the minimum possible capability, a single qubit, and a single quantum gate, is already enough.

We aren't at the point where these advances can be immediately deployed in modern technology. The initial applications are likely to display subexponential, but meaningful gains in scientific tasks: for instance, we saw in simulations that a quantum receiver may characterize dark matter signals from primordial sources in our own galaxy while achieving dozens-to-hundreds of times better accuracy than existing proposals for dark matter [haloscopes](https://en.wikipedia.org/wiki/Haloscope). Meanwhile, biomedical research often requires tracking time-dependent patterns in electromagnetic waves emitted by biological sources, such as the [brain](https://en.wikipedia.org/wiki/Magnetoencephalography); our work now opens up avenues for investigation as to whether these problems may admit a near-term quantum speedup by developing medical sensors equipped with qubit controls.

<figure style="margin: 2.6rem 0;">
  <a href="/assets/blog/bringing-quantum-advantage/img-4.png" target="_blank" rel="noopener" style="display:block;">
    <img
      src="/assets/blog/bringing-quantum-advantage/img-4.png"
      alt="Dark-matter particle-stream sensing example comparing quantum feature sensing with conventional approaches."
      style="display:block; width:auto; max-width:88%; max-height:500px; height:auto; margin:0 auto;"
    >
  </a>
</figure>

Looking to the future, I envision quantum-powered instruments capable of facilitating everyday technology. For instance, we designed and simulated a quantum receiver for wireless telecommunications, and saw that when signals were very weak, QFS allowed us to decode transmitted messages using $10,000\times$ fewer resources than classical radiofrequency communication technology. Our cell phones use comparatively much stronger signals, where the quantum advantage is much smaller, but future long-range communication or radar could plausibly become more energy-efficient and secure by leveraging these ideas. Even these more speculative proposals require far less sophisticated quantum technology than applying quantum computers to cryptanalysis or simulation, which require thousands of logical qubits, opening new domains to quantum advantages that can be engineered and tested in the near term.

<figure style="margin: 2.6rem 0;">
  <a href="/assets/blog/bringing-quantum-advantage/img-5.png" target="_blank" rel="noopener" style="display:block;">
    <img
      src="/assets/blog/bringing-quantum-advantage/img-5.png"
      alt="Wireless communication example comparing a quantum receiver with a classical receiver."
      style="display:block; width:auto; max-width:88%; max-height:500px; height:auto; margin:0 auto;"
    >
  </a>
</figure>
### Automating the design of quantum instruments

The field of quantum computing has struggled to find reproducible strategies for designing useful applications of quantum computers. The few examples we know of have been developed case-by-case, and it is unclear what special underlying structure connects these problems (such as factoring numbers, database search, etc.) and makes them amenable to quantum advantage. Such a guiding principle would be especially valuable in today's AI-powered research climate: AI can't tackle an open-ended question like "Discover new quantum advantages," but with clever physics-motivated scaffolding, AI models could plausibly discover new quantum speedups.  Q$\Psi$ gives us a footing to enable AI to assist in these open-ended discoveries.

The core innovation of Q$\Psi$ is that quantum speedups that appear in *learning* tasks (i.e. any task involving learning from an uncharacterized system, be it a signal, material, molecule, biological cell, etc.) can be mapped onto a classical statistics problem. In particular, every learning protocol you can run (including all of its resource constraints, the measurements you make, and the classical computations you run) can be written down as a single, known mathematical function $f(x)$. Likewise, the feature of interest can be written as its own function, $g(x)$, on the same domain. In Q$\Psi$, how well your chosen protocol learns the feature is directly quantified by how strongly these two functions overlap with one another. A beautiful concept then emerges: design of quantum technology can be formalized as a classical optimization problem. Given features of interest, we want to tweak the function representation $f(x)$ of our protocol until we maximize its overlap with our features, represented by $g(x)$.

In this way, Q$\Psi$ could provide exactly the kind of scaffolding needed for AI to interface with quantum computing. A scientist with access to a newly-built quantum machine could feed its specs, and their problems of interest, into a physics-guided AI that would convert this data into a tractable optimization problem and output the optimal way to run an experiment with the device. Conversely, an experimentalist speculating on how to build the best device tailored to a task of interest could input the task and the full family of quantum technologies they are considering building, and a classical AI would respond with the best choice. By using the rigorous guarantees provided by Q$\Psi$, the outputs of such an AI would be mathematically certifiable: we could guarantee that the given design achieves a quantum speedup over conventional technology, removing the uncertainty we usually struggle with when using AI for scientific purposes.

We're still a ways from this future. The theoretical basis for Q$\Psi$ needs to be expanded beyond the settings we studied, and quantum technology needs to develop further. But to me, these ideas are the start of a new phase of quantum science: one in which quantum technologies within our current reach reshape the manner in which we interface with the world around us.

Even as classical creatures evolving in a classical world, we now know that a quantum lens can let us see more clearly than ever before.

<figure style="margin: 2.6rem 0;">
  <a href="/assets/blog/bringing-quantum-advantage/img-6.png" target="_blank" rel="noopener" style="display:block;">
    <img
      src="/assets/blog/bringing-quantum-advantage/img-6.png"
      alt="Illustration of AI-assisted design of one-qubit quantum instruments for extracting useful features from physical signals."
      style="display:block; width:auto; max-width:88%; max-height:500px; height:auto; margin:0 auto;"
    >
  </a>
</figure>
#### References

Ishaan Kannan, Sridhar Prabhu, Saeed A. Khan, Mandar M. Sohoni, Xingrui Song, Saswata Roy, Alen Senanian, Valla Fatemi, Peter L. McMahon, and Jordan Cotler. [Exponential quantum advantage for learning signals with a single qubit](https://arxiv.org/abs/2608.13521), arXiv:2608.13521, 2026.

Constantin Cedillo Vayson de Pradenne, Ishaan Kannan, Harald Putterman, and Jordan Cotler. [Restrictions on non-Clifford fault tolerance and ruling out beyond-SQL quantum metrology](https://arxiv.org/abs/2607.27342), arXiv:2607.27342, 2026.
<!-- force blog rebuild -->
