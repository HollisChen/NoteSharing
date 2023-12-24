# Paper Reading Notes - Liang Lab

![Neuron](.\pics\Neuron.png)

## Basic knowledge

#### Amacrine cells, horizontal cells, bipolar cells

Amacrine cells, horizontal cells, and bipolar cells are three types of interneurons found in the retina of the eye. These cells play important roles in visual processing and contribute to the transmission of visual information from photoreceptor cells (rods and cones) to retinal ganglion cells.

1. Amacrine Cells: Amacrine cells are interneurons found in the inner nuclear layer of the retina. They are responsible for lateral processing and modulation of visual signals. Amacrine cells receive input from bipolar cells and provide inhibitory or excitatory signals to other bipolar cells, ganglion cells, or other amacrine cells. They help in adjusting contrast, detecting motion, and enhancing specific visual features.

2. Horizontal Cells: Horizontal cells are another type of interneuron located in the outer plexiform layer of the retina. They receive input from photoreceptor cells (rods and cones) and provide inhibitory feedback to modulate the activity of these cells. Horizontal cells facilitate lateral inhibition, which enhances contrast and sharpens the perception of edges in the visual scene. They also play a role in adjusting the sensitivity of photoreceptor cells to different levels of light.

3. Bipolar Cells: Bipolar cells are interneurons located in the inner nuclear layer of the retina, between the photoreceptor cells and ganglion cells. They transmit visual signals from photoreceptor cells to retinal ganglion cells. Bipolar cells receive input from photoreceptor cells (rods and cones) and, based on the type of bipolar cell, can convey information about light intensity, color, or specific spatial features. Different types of bipolar cells have distinct receptive field properties and contribute to various aspects of visual processing.

Together, amacrine cells, horizontal cells, and bipolar cells play crucial roles in shaping visual signals within the retina. They contribute to processes such as contrast enhancement, lateral inhibition, spatial filtering, and the modulation of visual information before it is transmitted to the retinal ganglion cells and further processed in the visual pathway.

#### Motif

In neuroscience, a motif is a recurring pattern of connectivity between neurons.

#### Axonal bouton

An axonal bouton, also known as a synaptic bouton or axon terminal, is a specialized structure located at the end of an axon. It is involved in transmitting signals to other neurons or target cells in the form of chemical or electrical signals. Axonal boutons are the sites of synapses, which are connections between neurons where information is exchanged. Refer to [here](https://synapseweb.clm.utexas.edu/axons).

#### Temple (颞)

Each of the flat parts at the sides of the head, at the same level as the eyes and higher. 指**头颅两侧靠近耳朵的部分**。

temporal adj.

#### Projection neurons vs interneurons

Projection neurons and interneurons are two distinct types of neurons based on their roles and connectivity within neural circuits.

1. Projection Neurons: Projection neurons, also known as output neurons or efferent neurons, are responsible for sending signals from one region of the nervous system to another. These neurons receive input from other neurons, process the information, and transmit it to distant target areas. Projection neurons typically have long axons that extend over long distances to reach their target regions. Examples of projection neurons include retinal ganglion cells, which transmit visual information from the retina to the brain, and pyramidal neurons in the cortex, which send signals to other brain regions.

2. Interneurons: Interneurons, also known as local circuit neurons or association neurons, are neurons that primarily communicate within a local region of the nervous system. They form connections with nearby neurons and participate in local processing, integration, and modulation of signals. Interneurons are responsible for coordinating the activity of different populations of neurons and mediating interactions between them. They are typically involved in information processing, integration of sensory inputs, and the regulation of neuronal activity within a specific circuit. Examples of interneurons include amacrine cells and horizontal cells in the retina, as well as inhibitory interneurons in the cortex.

In summary, projection neurons are responsible for transmitting signals from one region of the nervous system to another, often over long distances, while interneurons facilitate local processing and communication within a specific circuit or region. Both types of neurons play crucial roles in information processing and communication within the nervous system, but they differ in their connectivity and functional roles within neural networks.

#### Photoreceptor cells (rods and cones)

Photoreceptor cells, including rods and cones, are specialized sensory cells in the retina of the eye. While they are not classified as neurons, they are considered as specialized cells that convert light energy into electrical signals, which are then transmitted to the neighboring retinal neurons, including bipolar cells and retinal ganglion cells.

Photoreceptor cells contain light-sensitive pigments that enable them to detect and respond to different wavelengths of light. Rods are responsible for vision in low-light conditions and are more sensitive to dim light, while cones are responsible for color vision and visual acuity in bright light.

When light strikes the photoreceptor cells, it triggers a cascade of biochemical reactions that lead to changes in the electrical potential of the cell membrane. These changes in electrical potential result in the release of neurotransmitters, such as glutamate, which then communicate with the interconnected neurons in the retina.

Although photoreceptor cells themselves are not classified as neurons, they play a critical role in the initial transduction of light into electrical signals, which are then transmitted through the retinal neural circuitry via synapses between photoreceptor cells, bipolar cells, and ultimately to the retinal ganglion cells. The electrical signals generated by photoreceptor cells initiate the processing of visual information that is ultimately transmitted to the brain for further analysis and perception.

#### ChR2 (Channelrhodopsin-2) and Arch (Archaerhodopsin)

ChR2 (Channelrhodopsin-2) and Arch (Archaerhodopsin) are two types of optogenetic tools used in neuroscience research to manipulate the activity of neurons with light. Both ChR2 and Arch are light-sensitive proteins that are introduced into specific neurons through genetic modification, allowing researchers to control neuronal activity using light stimulation.

1. ChR2 (Channelrhodopsin-2): ChR2 is a light-sensitive protein derived from green algae. When exposed to blue light, ChR2 allows the influx of positive ions (usually sodium or calcium) into the neuron, leading to depolarization of the cell membrane and triggering action potentials or neuronal firing. ChR2 is commonly used to activate neurons and study their function in real-time by precisely controlling their firing patterns.

2. Arch (Archaerhodopsin): Arch is a light-sensitive protein derived from archaea, which are single-celled microorganisms. When exposed to yellow or red light, Arch allows the influx of negative ions (usually chloride) into the neuron, leading to hyperpolarization of the cell membrane and inhibiting neuronal firing. Arch is commonly used to suppress or silence the activity of specific neurons in order to study their role in neural circuits and behavior.

By using these optogenetic tools, neuroscientists can selectively activate or inhibit specific populations of neurons with precise spatial and temporal control. This allows for a deeper understanding of how neural circuits function and how they contribute to various physiological and behavioral processes.

#### ChRimson stimulation and GCaMP imaging

The combination of ChRimson stimulation and GCaMP imaging is a popular experimental approach used in neuroscience research to study neuronal activity and circuit dynamics. Here's a brief explanation of each component:

1. ChRimson stimulation: ChRimson is a genetically encoded protein known as a channelrhodopsin, which is sensitive to light. It can be selectively expressed in specific neurons or neuronal populations using genetic techniques. When activated by a specific wavelength of light (usually in the red spectrum), ChRimson allows for precise control of neuronal activation. By shining light onto the ChRimson-expressing neurons, researchers can evoke action potentials and study the effects of neuronal activation on circuit function.

   The name "ChRimson" is a portmanteau combining "channelrhodopsin" (ChR) and "crimson." Channelrhodopsins are a family of light-sensitive proteins derived from microbial organisms, commonly used in optogenetics to control the activity of neurons using light stimulation. ChRimson is a specific variant of channelrhodopsin that emits a red fluorescence when activated by light, hence the inclusion of "crimson" in its name.

2. GCaMP imaging: GCaMP is a genetically encoded calcium indicator protein that emits fluorescence in response to changes in intracellular calcium levels. Calcium ions play a crucial role in neuronal activity, and fluctuations in calcium levels are closely associated with neuronal firing and synaptic activity. By expressing GCaMP in neurons, researchers can monitor changes in calcium levels, which serve as a proxy for neuronal activity. GCaMP imaging allows for the visualization and quantification of neural responses in real-time and can provide insights into the dynamics of neural circuits. In "GCaMP", "G" stands for "green"; "Ca" stands for "calcium"; "MP" portion stands for "molecular probe" or "molecular indicator", which indicates that GCaMP is a genetically encoded protein that serves as a probe or indicator for calcium levels.

When ChRimson stimulation is combined with GCaMP imaging, it enables researchers to both activate specific neurons and simultaneously monitor the resulting calcium responses in those neurons and potentially surrounding cells. ChRimson's distinct red fluorescence properties make it useful for experiments that involve simultaneous optogenetic stimulation and fluorescent imaging using red-light-sensitive indicators like GCaMP.

#### PMT

PMT stands for "Photomultiplier Tube." It is a highly sensitive electronic device used for detecting and measuring light intensity in various scientific and technical applications, including neuroscience and optogenetics.

A PMT consists of a vacuum-sealed glass or metal enclosure that contains a series of dynodes and a photocathode. When photons strike the photocathode, they generate photoelectrons through the photoelectric effect. These photoelectrons are then accelerated and multiplied through a series of dynodes, producing an amplified electrical signal proportional to the intensity of the incident light.

PMTs are commonly used in fluorescence microscopy, where they are used to detect and quantify the fluorescence emitted by fluorophores in biological samples. In optogenetics, PMTs are often employed to measure the fluorescence signals emitted by genetically encoded calcium indicators (such as GCaMP) or other fluorescent reporters that monitor neuronal activity.

The high sensitivity and fast response time of PMTs make them well-suited for detecting low light levels and capturing rapid changes in fluorescence intensity. They are a valuable tool in many optical measurement systems, providing precise and reliable detection of light signals in various scientific disciplines.

#### Cerebral cortex

The cerebral cortex mostly consists of the six-layered neocortex, with just 10% consisting of allocortex.

Six layers in neocortex:

- Molecular (plexiform) layer.
- External granular layer.
- External pyramidal layer.
- Internal granular layer.
- Internal pyramidal layer.
- Multiform (fusiform) layer.

#### Perfusion and sectioning

Perfusion and sectioning are typically procedures conducted after the death of an animal, usually a laboratory mouse or rat, in the context of neuroscience research.

1. **Perfusion**: Perfusion is a process of flushing out the blood from an animal's vascular system and replacing it with a fixative solution. This fixation process helps preserve the brain's structure and biochemical properties for further analysis. Perfusion is often done using a pump to push a fixative solution through the animal's circulatory system. The fixative solution usually contains chemicals that prevent cellular degradation, allowing researchers to study the brain's anatomy and molecular composition.

2. **Sectioning**: Sectioning involves slicing the preserved brain into thin sections for examination under a microscope. These sections can be cut using specialized equipment, such as a microtome, which allows researchers to obtain precise slices. The thickness of the sections depends on the research objectives and the specific techniques being used. Once the brain is sliced, researchers can analyze different regions and layers to understand its structure and potentially study various features, like cell types, connectivity, and protein distribution.

Both perfusion and sectioning are crucial steps in preparing brain tissue for further analysis in neuroscientific studies. They provide researchers with the means to investigate the brain's structure, function, and connectivity after the animal's death.

Note: Paraformaldehyde (PFA) is a commonly used fixative solution for perfusion in many neuroscience studies. PFA is a chemical compound that helps preserve tissue by cross-linking proteins and preventing their degradation. When used as a fixative, PFA stabilizes cellular structures, including neurons and their connections, allowing researchers to analyze the tissue's morphology, connectivity, and other characteristics.

During perfusion, PFA is often mixed with a buffer solution (such as phosphate-buffered saline) to create a perfusate. The perfusate is pumped into the circulatory system of the animal, effectively replacing the blood with the fixative solution. This process helps rapidly halt cellular activity and preserve the tissue's state at the time of perfusion.

After perfusion, the brain is usually removed from the animal and further processed, which may include additional fixation, sectioning, and staining steps depending on the specific experimental goals.

#### Confocal imaging and coregistration

Confocal imaging is an advanced microscopy technique used to capture high-resolution, three-dimensional images of biological specimens. It provides better optical sectioning and reduces out-of-focus light, resulting in clearer and more detailed images compared to conventional widefield microscopy.

The core principle of confocal imaging involves using a pinhole aperture to block out-of-focus light, allowing only the light emitted from the focal plane of the specimen to pass through. This results in improved contrast and resolution, particularly in thick or densely labeled samples.

Confocal microscopes use lasers to illuminate the sample, and the emitted light is collected through a detector. By scanning the laser across the specimen and collecting the emitted light at different depths, a series of optical sections can be obtained. These sections can then be reconstructed into a three-dimensional image, providing insights into the spatial arrangement of structures within the specimen.

Confocal imaging is widely used in various fields of biology, including neuroscience, cell biology, developmental biology, and more, to study cellular structures, protein localization, and dynamic processes in living or fixed samples.

Coregistration, also known as image registration or image alignment, is a process used in various imaging techniques, including neuroimaging, to align two or more images of the same subject or scene. The goal of coregistration is to ensure that the images are spatially matched, allowing for accurate comparison, analysis, and integration of data from different sources or modalities.

In the context of neuroimaging, coregistration often refers to aligning images from different imaging modalities, such as MRI (structural) and PET or fMRI (functional), to precisely overlay the structural and functional information. This alignment enables researchers to accurately correlate brain activity with specific anatomical regions.

Coregistration involves identifying common landmarks or features present in both images and using mathematical algorithms to calculate the transformation needed to align them. This transformation includes translation, rotation, scaling, and distortion adjustments. The process aims to minimize differences between the images, optimizing the spatial correspondence between corresponding points or regions.

Coregistration is essential for many applications, such as:

1. Combining structural and functional data in functional neuroimaging studies.
2. Integrating information from multiple imaging modalities to gain a comprehensive view of the subject.
3. Comparing images acquired at different time points or under different conditions.
4. Fusing data from different imaging techniques, such as combining MRI with histological data.

Overall, coregistration enhances the accuracy and reliability of data analysis and interpretation by ensuring that the images being compared or integrated are accurately aligned in space.

#### Pia mater

The pia mater (often referred to as just "pia") is a thin, delicate layer of connective tissue that is located on the surface of the cerebral cortex. It is the innermost layer of the three membranes (meninges), which are the protective membranes that cover the brain and spinal cord. It is a thin, delicate membrane that is closely adhered to the underlying nervous tissue. The pia mater is in direct contact with the brain tissue and follows the contours of the cerebral cortex, providing support and protection to the brain.

#### NMDA receptors and AMPA receptors

NMDA receptors and AMPA receptors are two major types of glutamate receptors that mediate excitatory synaptic transmission in the brain.

1. **Activation** 
  - NMDA receptors require binding of both glutamate (the neurotransmitter) and a co-agonist (such as glycine or D-serine) to be fully activated (open the channel pore and allow cation influx). This requirement is often referred to as a "coincidence detection" mechanism. 
  - AMPA receptors are activated by the neurotransmitter glutamate alone, without the need for additional co-agonists.

2. **Ion Selectivity**

- NMDA receptor activation leads to larger cation influx, especially of calcium ions (Ca2+).  NMDA receptors also allow the passage of sodium ions (Na+), and potassium ions (K+) when activated. NMDA receptors have a much higher permeability to Ca2+ compared to Na+ or K+.
- AMPA receptors are primarily selective for sodium ions (Na+), meaning they allow a significant influx of sodium ions when activated by the neurotransmitter glutamate. While they do allow some passage of potassium ions (K+), the permeability for sodium is much higher compared to potassium. 

3. **Slow/Fast Kinetics**

- NMDA receptors have a slower kinetic response, with channel openings in the range of 50-100 ms.
- AMPA receptors have faster kinetics of around 1 ms.

4. **Voltage Dependency/Independence**

- NMDA receptors are voltage-dependent and require membrane depolarization (often provided by AMPA receptor activation first) to remove a magnesium (Mg2+) ion block from their ion channel. (Voltage Dependency)
- AMPA receptors are not as voltage-dependent as NMDA receptors and can open at the resting membrane potential. (Voltage Independence)

5. **Synaptic Plasticity**

- NMDA receptors play key roles in synaptic plasticity, learning, and memory due to their calcium permeability and signaling. The large influx of calcium ions through NMDA receptors triggers a cascade of biochemical events (including changes in gene expression and the formation of new synaptic structures) within the neuron, contributing to processes, e.g., LTP, of synaptic plasticity. NMDA receptors are closely associated with **the late phase of LTP**, which involves more enduring changes in synaptic strength and structural modifications of synapses.
- AMPA receptors mediate most of the fast excitatory synaptic transmission, and are involved in **the early phase of LTP** and are responsible for the initial strengthening of synapses.

Besides, NMDA receptors contribute to the integration of synaptic inputs, particularly during strong synaptic activity and coincident firing. The GluN2 subunit composition affects NMDA receptor properties such as channel kinetics and magnesium sensitivity. AMPA receptors contain GluA2 subunits that govern calcium permeability.

Also, AMPA receptors are generally more numerous than NMDA receptors at most synapses due to their role in rapid synaptic transmission. For example, hippocampal CA1 synapses contain around 50 AMPA receptors vs. 20 NMDA receptors per synapse on average.

#### Dorsal vs ventral, caudal vs rostral, medial vs lateral

In the context of neuron imaging, "caudal," "medial," and "dorsal" are terms used to describe different orientations or perspectives for viewing the brain or specific brain structures. These terms are commonly used in neuroscience to indicate different directions within the brain and its regions. Here's what each term means:

1. **Caudal** vs **rostral**: Caudal refers to the direction toward the tail end of an organism. In the context of brain imaging, caudal view means looking at the brain from a perspective where you are viewing structures that are located closer to the rear or tail end of the brain. It's the opposite of the "rostral" direction, which is towards the head.
2. **Medial** vs **lateral**: Medial refers to the direction toward the midline of the body or brain. In neuron imaging, a medial view means you are looking at the brain from an angle where you can see structures that are located closer to the center or midline of the brain. It's the opposite of the "lateral" direction, which is away from the midline.
3. **Dorsal** vs **ventral**: Dorsal refers to the direction toward the back or upper surface of an organism. In the context of brain imaging, a dorsal view means you are looking at the brain from an angle where you can see structures that are located towards the top or back of the brain. It's the opposite of the "ventral" direction, which is towards the belly or lower surface.

#### Retina waves

In the context of neurobiology and the development of the visual system, a "retina wave" refers to a specific pattern of synchronized, spontaneous electrical activity that occurs in the developing retina of the eye. These waves of activity are often observed in animal models during early stages of retinal development, typically before the onset of vision.

Here are some key characteristics of retina waves:

1. **Spontaneous Activity:** Retina waves are spontaneous, rhythmic bursts of electrical activity that occur in the absence of visual stimulation. They are generated within the retina itself.

2. **Synchronized Activity:** Retina waves often involve the synchronized firing of groups of retinal ganglion cells (RGCs) and other retinal neurons. These cells send signals to the brain via the optic nerve.

3. **Purpose:** The exact purpose of retina waves is not fully understood, but they are believed to play a role in refining and organizing the neural circuitry in the developing visual system. They may be involved in establishing connections between retinal cells and in the development of receptive fields in the visual cortex.

4. **Critical Period:** Retina waves are typically observed during a critical period in early development. As the visual system matures, spontaneous retinal activity gradually decreases and is replaced by visual responses to external stimuli.

5. **Experimental Tool:** Retina waves are used as a valuable tool in neuroscience research. They provide insights into how the visual system wires itself during development, and they can be manipulated and studied to understand the principles of neural circuit formation.

Overall, retina waves are an important phenomenon in the study of visual system development and have contributed to our understanding of how the nervous system establishes functional connections during early stages of life.

#### Membrane time constant and synaptic time constant 

The membrane time constant and synaptic time constant are important concepts in neuroscience that relate to the dynamics of neuronal communication and the behavior of individual neurons.

1. Membrane Time Constant:
   - The membrane time constant (often denoted as τ_m) represents the time it takes for the membrane potential of a neuron to reach approximately 63.2% of its final value after a step change in current. It's a measure of how quickly a neuron's membrane potential responds to input.
   - This time constant is determined by the membrane resistance (R_m) and the membrane capacitance (C_m) of the neuron and is given by the formula τ_m = R_m * C_m.
   - Neurons with longer membrane time constants respond more slowly to changes in input, while those with shorter time constants respond more rapidly.

2. Synaptic Time Constant:
   - The synaptic time constant (often denoted as τ_syn) represents the time it takes for the synaptic current in a neuron to decay to approximately 37% of its peak amplitude after the arrival of a synaptic input.
   - It is influenced by the properties of the synapse, such as the neurotransmitter dynamics and receptor kinetics.
   - Synaptic time constants can vary widely depending on the type of synapse. For example, excitatory synapses mediated by glutamate typically have shorter synaptic time constants than inhibitory synapses mediated by GABA.

Difference:
The key difference between these two time constants lies in what they measure:
- Membrane Time Constant (τ_m) primarily describes the intrinsic properties of a neuron's membrane and how quickly its membrane potential responds to changes in input currents.
- Synaptic Time Constant (τ_syn) describes the time course of synaptic currents, focusing on how quickly postsynaptic responses to neurotransmitter release decay.

In summary, while both time constants are important in understanding the dynamics of neuronal behavior, they pertain to different aspects of neuronal function: the membrane time constant is related to the neuron's electrical properties, while the synaptic time constant is related to the dynamics of neurotransmission at synapses.

## Neuron Modeling

### Pyramidal Neuron as Two-Layer Neural Network 

We found the cells firing rate could be predicted by a simple formula that maps the physical components of the cell onto those of an abstract two-layer "neural network. In the first layer synaptic inputs drive independent sigmoidal subunits corresponding to the cell's several dozen long, thin terminal dendrites. The subunit outputs are then summed within the main trunk and cell body prior to final thresholding. We conclude that insofar as the neural code is mediated by average firing rate, a two-layer neural network may provide a useful abstraction for the computing function of the individual pyramidal neuron.



## Dendritic integration papers

**Dendritic integration**: 

Dendritic integration refers to the process by which a neuron integrates synaptic inputs received on its dendrites to generate an output signal. Neurons receive numerous synaptic inputs from other neurons onto their dendrites, and these inputs can be excitatory or inhibitory in nature. The integration of these inputs at the dendrites determines whether the neuron will generate an action potential or not.

Dendritic integration involves various mechanisms that determine how synaptic inputs are combined and transformed within the dendritic tree. These mechanisms include spatial and temporal summation, as well as the properties of dendritic voltage-gated channels and active conductances.

**Spatial summation** refers to the additive effect of simultaneous synaptic inputs occurring at different locations on the dendritic tree. If the combined excitatory inputs reach a certain threshold, they can depolarize the dendrites sufficiently to generate an action potential.

**Temporal summation**, on the other hand, involves the integration of synaptic inputs occurring at different times. If excitatory inputs arrive in rapid succession, their individual effects can summate temporally to reach the threshold for action potential initiation.

The properties of dendritic voltage-gated channels and active conductances further shape the integration process. Dendrites possess various types of ion channels that can amplify or attenuate synaptic inputs, such as voltage-gated sodium and potassium channels. These channels can influence the spread of depolarization along the dendritic tree and the generation of local dendritic spikes, contributing to the integration of synaptic inputs.

Overall, dendritic integration plays a crucial role in determining the output of a neuron and is essential for information processing in neural circuits. By integrating and processing synaptic inputs, dendrites contribute to the computational capabilities of neurons and shape their firing patterns and responses to incoming stimuli.

### Dendritic integration: 60 years of progress

## Junior Journal Club

### Gain control by layer six in cortical circuits of vision  

Here we show that layer six in the primary visual cortex of the mouse has a crucial role in controlling the gain of visually evoked activity in neurons of the upper layers without changing their tuning to orientation. This gain modulation results from the coordinated action of layer six intracortical projections to superficial layers and **deep projections to the thalamus**, with a substantial role of the intracortical circuit. This study establishes layer six as a major mediator of cortical gain modulation and suggests that it could be a node through which convergent inputs from several brain areas can regulate the earliest steps of cortical visual processing.

L6 may thus influence cortical sensory responses directly through intracortical projections and indirectly through corticothalamic projections. **Corticothalamic projections were reported to be both suppressive and facilitatory on thalamic activity**, depending on the precise alignment between L6 and thalamic neurons.

Thus, these data show that stimulation of L6 excitatory neurons suppresses visually evoked responses in L2/3, L4 and L5 of V1. 

L6 activity does not affect tuning. Remarkably, photostimulation of L6 resulted in the precise scaling of the tuning curve; that is, it reduced visually evoked responses by a similar fraction irrespective of presented orientation.

### Guarding the gateway to cortex with attention in visual thalamus

The massive visual input from the eye to the brain requires selective processing of some visual information at the expense of other information, a process referred to as visual attention. 

Attention modulates visual signals before they even reach cortex by increasing responses of both magnocellular and parvocellular neurons in the first relay between retina and cortex, the lateral geniculate nucleus (LGN). At the same time, attention decreases neuronal responses in the adjacent thalamic reticular nucleus (TRN).

The visual sector of TRN receives excitatory inputs from LGN, but projects modulatory inhibitory input back to LGN. Therefore, TRN responses should instead decrease with attention, reducing the inhibitory influence of the TRN on LGN, thereby causing the increase in the responses of LGN neurons that we observe.

LGN responses increase with attention whereas TRN responses decrease.  

