# Toward an Organic-Based ALU — Phase 1
## Engineered Biological Logic Cells, Directional Electrical Interconnects, and Fan-Out
**Version:** 0.1 — November 18, 2026  
**Status:** Design hypothesis; not an experimentally validated ALU.

## Abstract
This report defines the first research phase toward an arithmetic logic unit (ALU) with an **external dimension below 20 mm**, composed of genetically engineered living cells inspired by neurons. Rather than long axons, chemical synapses, or learning-based neural networks, the proposed architecture employs short, selective electrical cell-to-cell connections; pA-scale current encoding; two independent outputs; threshold-based logic; and standardized cell production. The immediate goal is not a complete ALU but measurable research hypotheses for a prototype demonstrating a single gate, a two-cell connection, and **fan-out = 2**. The size constraint anticipates integration with a biological RISC processor and organic artificial intelligence platform; it is not yet supported by a validated layout calculation.

## 1. Research question and scope
Can a living cell be engineered to implement one of the NOT, AND, OR, NAND, or NOR logic functions with stable thresholds? Can it transmit the same logical result through **two distinct electrical outputs**, despite variations in input loading? Can selective electrical cell junctions reduce undesirable reverse coupling? Can reproducible logic elements be obtained from a manufacturable cell line?

Out of scope for Phase 1 are claims of a fabricated full 8-bit ALU, memory, instruction decoder, clock distribution, RISC execution unit, learning algorithms, and autonomous photovoltaic power. These remain system-level requirements for later phases.

## 2. Primary architecture — N-CURRENT / N-GATE / N-LINK
- A metabolically viable engineered logic cell derived from neurons or exhibiting neuron-like electrophysiology.
- Information is represented by ionic currents on the pA scale; membrane potentials and electrochemical gradients remain physically necessary.
- Low-impedance input current sensing and a high-dynamic-impedance active output are **design targets**, not intrinsic properties of natural neurons.
- Short, geometrically guided membrane contacts and selective heterotypic gap-junction proteins are **candidate interconnects**. Selective pairing does not itself guarantee rectification or signal gain.
- At least two outputs per cell, with a separate local driver and membrane extension for each; electrical cross-coupling between outputs must be measured.
- A per-output current-gain target of unity is acceptable initially. However, if two outputs each equal the input current, their **aggregate current gain is two** and requires metabolic energy. This must not be presented as gain-free fan-out.

## 3. Two alternative dual-output designs
**A — Shared logic core with two separated drivers.** One logical state controls local ion-channel activity in two different membrane regions. The design seeks to reduce the effect of load-dependent voltage/current changes at one output on the other. Complete isolation cannot be assumed because the cytoplasm and membrane remain shared.

**B — Shared inputs with two logic-processing regions inside one cell.** If design A does not achieve acceptable fan-out and isolation, two local logic subunits within the **same cell** can each sense the same inputs and generate their own output. This is not a proposal to use two separate cells. Shared-input loading, spatial protein targeting, intracellular signaling, and energy demand are distinct risks. Design B has not been demonstrated as a biological logic implementation.

**C — Comparison control.** Passive branching of a single driver to two contacts, with measured current splitting, provides a quantitative baseline for A and B.

## 4. Minimal electrical model
For each cell:

`C_m dV/dt = I_in - g_L(V - E_L) - I_ion(V,t)`

For two junctions, as a first approximation:

`I_j = g_j(V_out - V_load,j)`

Actual gap-junction conductance may depend on voltage, connexin composition, and direction. Current-source-like output behavior must be established experimentally.

Define cross-load sensitivity:

`K_12 = |(Delta I_2 / I_2) / (Delta Z_1 / Z_1)|`

A change below 5% in output 2 across a predefined loading range is a **proposed engineering criterion, not a literature-established biological limit**. Forward/reverse transmission asymmetry, bit error rate, logic-level separation, response latency, energy use, and cell-to-cell variability should also be reported.

For charge and capacitance, `Q = I*t`. For example, 10 pA for 1 ms transfers `10^-14 C`, approximately `6.24 x 10^4` monovalent ions. With an ideal 10 pF capacitance, this produces only 1 mV. Leakage and channel kinetics complicate the response further. Small currents alone therefore do not imply fast or reliable switching.

## 5. Logic functions
An abstract threshold model is `Y = H(w_A A + w_B B + b)`, where `H(x) = 1` for `x > 0`, otherwise zero. Example parameter tuples `(w_A,w_B,b)` are: NOT `(-1,0,+0.5)`; AND `(+1,+1,-1.5)`; OR `(+1,+1,-0.5)`; NAND `(-1,-1,+1.5)`; NOR `(-1,-1,+0.5)`. These coefficients do **not** directly specify realizable biological ion-channel designs. XOR is not linearly separable and needs multiple regions or cells. A NOT-like gate with two outputs suffices for the first demonstration; other gates belong to subsequent steps.

## 6. Cell production and power
Rather than attempting to make mature neurons divide reliably, the proposed manufacturing route is to engineer a proliferative stem/progenitor cell line, expand it, and then differentiate the cells into logic elements. Genetic identity does not guarantee identical electrical characteristics: single-cell characterization, selection, and calibration are required.

A photovoltaic source, rechargeable battery/capacitor, and controlled electrochemical interface are a long-term power concept. Stored electrical energy does not directly maintain cellular ion gradients; ion pumps and metabolism require an appropriate energy-conversion mechanism. Conventional cell-culture metabolism with external stimulation and measurement is more realistic in Phase 1.

## 7. Phase 1 experimental validation logic (conceptual)
1. Demonstrate a stable NOT-like response and quantify its threshold noise margin in one cell.
2. Establish a selective contact between two cells and compare intended with unintended pairing.
3. Measure forward and reverse electrical transmission; do not confuse molecular selectivity with electrical rectification.
4. Measure passive branching of one output into two loads and its sensitivity to changing loads.
5. Test two outputs and cross-coupling under architecture A.
6. If A fails, evaluate common inputs, two local logic regions, and output independence under architecture B.
7. Measure repeatability, viability, channel variability, energy consumption, and speed.

**Decision gate:** Do not claim readiness for ALU scaling until reproducible logic levels, interconnect behavior that limits undesirable feedback, and reliable operation with two loads have been demonstrated. Failure invalidates a particular implementation, not every possible biological logic architecture.

## 8. Interpretation of the sub-20-mm goal
The mechanical envelope is **less than 20 mm**. Biological logic elements, life-support volume, electrodes, microfluidic channels, and interconnect topology must each receive an explicit space budget. Phase 1 does not establish a validated gate density or timing model at this scale. Documentation should preserve a path toward a common cell platform for a later RISC processor, registers, control, memory, and organic AI systems.

## 9. Principal risks and falsifiability
- Natural gap junctions can electrically couple cells in ways that undermine isolation.
- Selective heterotypic pairing does not necessarily produce unidirectional transmission.
- Two output drivers may couple strongly through a shared membrane and cytoplasm.
- A low-impedance input could shunt the local voltage signal needed for channel activation.
- At pA currents, stochastic channel behavior, leakage, and narrow signal margins matter.
- Two logic regions within one cell may fail because of protein localization limits and common-input loading.
- Cell size and connection density may prove incompatible with a sub-20-mm ALU.

## 10. Candidate laboratories (not contacted)
1. **Kafui Dzirasa Lab, Duke University, USA:** engineered selective electrical synapses; molecular pairing and junction design. https://www.neuro.duke.edu/research/faculty-labs/dzirasa-lab
2. **Nenad Bursac Lab, Duke University, USA:** engineering electrical excitability in cells, ion channels, and patterned tissues. https://bursaclab.pratt.duke.edu/research/electrophysiology-excitable-cells-and-tissues
3. **Adam E. Cohen Lab, Harvard University, USA:** engineered excitable cells, voltage imaging, and biophysical characterization. https://cohenweb.rc.fas.harvard.edu/Research/research.html
4. **Michael Levin Lab, Tufts University, USA:** bioelectric signaling, synthetic biology, and multicellular information processing. https://as.tufts.edu/biology/levin-lab/research/direction-lab
5. **Edmond Walsh / Richard Wade-Martins collaboration, University of Oxford, UK:** microfluidic organization of human neuronal circuits. https://eng.ox.ac.uk/news/creating-brain-circuits-with-human-neurons-and-fluid-walls

These candidates were selected for topical relevance. Their willingness or capacity to collaborate has not been confirmed.

## 11. References
[1] Ransey E. et al. (2026). *Long-term editing of brain circuits using an engineered electrical synapse*. Nature. DOI: 10.1038/s41586-026-10501-y. https://pmc.ncbi.nlm.nih.gov/articles/PMC13372691/

[2] Kirkton R.D. & Bursac N. (2011). *Engineering biosynthetic excitable tissues from unexcitable cells for electrophysiological and cell therapy studies*. Nature Communications 2, 300. https://www.nature.com/articles/ncomms1302

[3] Nebuloni F. et al. (2024). *A fluid-walled microfluidic platform for human neuron microcircuits and directed axotomy*. Lab on a Chip 24, 3252–3264. DOI: 10.1039/D4LC00107A. https://pubs.rsc.org/en/content/articlehtml/2024/lc/d4lc00107a

[4] Rabinowitch I., Colón-Ramos D.A., Krieg M. (2024). *Understanding neural circuit function through synaptic engineering*. Nature Reviews Neuroscience 25, 131–139. https://www.nature.com/articles/s41583-023-00777-8

[5] Ori H. et al. (2023). *Observation of topological action potentials in engineered tissues*. Nature Physics 19, 290–296. https://www.nature.com/articles/s41567-022-01853-z

[6] University of Oxford (2025). *Creating brain circuits with human neurons and fluid walls*. https://eng.ox.ac.uk/news/creating-brain-circuits-with-human-neurons-and-fluid-walls

[7] Cohen Lab, Harvard University. *Voltage imaging throughout life* (research overview). https://cohenweb.rc.fas.harvard.edu/Research/research.html

[8] Levin Lab, Tufts University. *Direction of Lab*. https://as.tufts.edu/biology/levin-lab/research/direction-lab

## 12. Open research questions
- What geometry would provide sufficient electrical isolation between two short membrane extensions?
- Which biological transduction mechanism could couple one logic state to ionic current production in two drivers?
- How do A and B compare in speed, energy, variability, and manufacturing complexity?
- What are the transmission asymmetry and feedback characteristics of candidate selective connexin pairs?
- What are the minimum logic-element, interconnect, and support-area requirements for a sub-20-mm, RISC-compatible ALU?

**Conclusion:** Phase 1 presents a literature-grounded, falsifiable design hypothesis—not a completed biological device.