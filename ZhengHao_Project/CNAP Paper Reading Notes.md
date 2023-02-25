# Complex Networks for Asynchronous Representation Paper Reading Notes

## Polychronization: Computation with Spikes

Author: Eugene M. Izhikevich

### 知识积累

○ [突触](https://zh.wikipedia.org/wiki/%E7%AA%81%E8%A7%A6)、[STDP (Spike-timing-dependent plasticity, or Hebbian temporally asymmetric synaptic plasticity)](https://en.wikipedia.org/wiki/Spike-timing-dependent_plasticity)、[Hebbian Theory](https://en.wikipedia.org/wiki/Hebbian_theory)

○ **What do atteactors mean in neural networks?**

Attractors in neural networks refer to stable states or patterns of activity that the network converges to over time. These attractors can be thought of as the network's "memorized" patterns, and can be used for tasks such as pattern recognition or image classification. Attractors can be found by running simulations of the network and observing the activity of the neurons over time. They can also be characterized by their basins of attraction, which is the set of initial conditions that lead to the attractor.

○ **What does a synfire braid mean in neural networks?**

A synfire chain or synfire braid is a concept in neural networks that refers to a sequence of neurons that fire in a specific order, creating a pattern of activity that is propagated through the network. The concept was first introduced by Abbot and Sejnowski in 1997 and it describes a pattern of activity where a group of neurons fire synchronously, creating a spike train, which then activates another group of neurons, and so on. This pattern of activity can be thought of as a "wave" that propagates through the network. Synfire chains have been proposed as a possible mechanism for information processing in the brain and have been used to model various cognitive tasks such as sequence learning, pattern completion and speech recognition.

○ **What is TNGS?**

The theory of neuronal group selection (TNGS, Neural Darwinism) is a hypothesis about how the brain functions. It proposes that groups of neurons, rather than individual neurons, are the basic functional units of the brain. According to this theory, the brain is composed of a large number of neuronal groups, each of which has a specific function. These groups of neurons are thought to compete with each other for resources, such as blood flow and glucose, and the groups that are most successful at competing will become stronger and more influential, while those that are less successful will become weaker and less influential. This process of competition and selection among neuronal groups is thought to underlie the development and function of the brain.

○ **What is binding in neural networks?**

Binding in neural networks refers to the process of combining multiple pieces of information, such as the features of an object, into a single, cohesive representation. This is a key aspect of neural processing in the brain, and is thought to play a crucial role in tasks such as object recognition, scene perception, and working memory.

There are different ways to implement binding in neural networks, but one common approach is to use a mechanism called "feature binding" which refers to the process of combining information from different sensory modalities, such as vision and audition, into a single representation. This can be achieved by creating a population of neurons that respond selectively to different features of an object, such as its shape, color, and texture, and then linking these neurons together in a network so that they can interact and work together.

Another approach is to use recurrent neural networks (RNNs) where the recurrent connections allow information to flow within the network, creating a kind of "memory" that can be used to bind different features together over time.

In summary, binding in neural networks is the process of creating a single cohesive representation of different pieces of information and it can be achieved through different mechanisms such as feature binding or recurrent neural networks.

○ **dimensionality怎么理解？**

dimensionality理解为“维度性”，an infinite dimensionality解释为“具有无线维度的性质”，主语为性质。

○ **What is the corpus callosum? Why is the corpus callosum called corpus callosum?**

The corpus callosum is a large bundle of nerve fibers that connects the left and right hemispheres of the brain. It allows for communication and coordination between the two hemispheres. Damage to the corpus callosum can result in a condition called agenesis of the corpus callosum, which can cause a variety of neurological symptoms.

The corpus callosum is called corpus callosum in Latin, which means "tough body" or "tough cord". The name is likely a reference to the thick bundle of nerve fibers that make up the structure. It is also because the corpus callosum is one of the most robust structure in the brain and it helps to connect the two hemispheres of the brain and allows for communication and coordination between them.

corpus这个单词单独使用时表示“a collection of written or spoken texts （书面或口语的）文集，文献，汇编；语料库”；而collasum没有单独的意思，只有这种组合使用方式。

复数： corpora callosa （但一般也用不到复数吧）。

中文名：胼胝体。

○ **What do "statistically significant" and "statistically significant events" mean?**

Statistically significant refers to a result or relationship that is unlikely to have occurred by chance. In a statistical test, this means that the probability of observing the result or relationship if the null hypothesis (i.e. no relationship or effect) is true is very low. Typically, a threshold of less than 5% (p < 0.05) is used to determine statistical significance. This means that there is less than a 5% chance that the result or relationship is due to chance.

Statistically significant events refers to events or outcomes that have been shown to have a low probability of occurring by chance, based on statistical analysis. For example, in a scientific study, a statistically significant event might be a treatment or intervention that leads to a significant improvement in a certain outcome, when compared to a control group. In this context, the event or outcome would be considered statistically significant if the probability of observing it if the treatment or intervention had no effect is very low (usually less than 5%). It could also refer to events which are shown to have a low probability of being random or not meaningful.

○ **What is thalamus?**

The thalamus is a small, egg-shaped structure located in the center of the brain, just above the brainstem. It acts as a relay station for incoming sensory information, directing it to the appropriate areas of the cerebral cortex for further processing. The thalamus receives inputs from all of the senses except for smell, which is processed in the olfactory bulb. It also plays a role in regulating sleep, consciousness, and attention. Damage to the thalamus can result in a variety of neurological symptoms, such as loss of sensation, difficulty with movement, and problems with attention and memory.

○ **What are the reentrant connections in human neural networks?**

Reentrant connections in human neural networks refer to the feedback loops that exist between different regions of the brain. These loops involve the transmission of neural activity from one region to another, which can then influence the activity of the original region.

Reentrant connections are thought to play an important role in the way the brain processes information. They are thought to allow for the integration of information from different parts of the brain, which is necessary for tasks such as perception, decision making, and motor control.

Research in neuroscience has shown that reentrant connections are present throughout the brain, and are particularly prevalent in the cerebral cortex, the part of the brain responsible for higher cognitive functions. Studies have also found that different regions of the brain are connected to each other via reentrant loops in specific patterns that are related to specific functions, such as visual processing or language.

Additionally, reentrant connections have been shown to be affected in various neurological and psychiatric disorders such as schizophrenia, autism, and Alzheimer's disease, making it a topic of interest for research in neuroscience.

### 科研观点

The propagation delay between any individual pair of neurons is precise and reproducible with a submillisecond precision.

The majority of computational neuroscientists discard delays as a nuisance that only complicates modeling. From a mathematical point of view, a system with delays is not finite- but infinite-dimensional,1 which poses some mathematical and simulation difficulties.

We argue that an infinite dimensionality of spiking networks with axonal delays is not a nuisance but an immense advantage that results in an unprecedented information capacity.

## Simple Model of Spiking Neurons  

Author: Eugene M. Izhikevich

### 知识积累

○ **What is a cortical neuron? Are there other types of neurons?**

A cortical neuron is a type of neuron that is found in the cerebral cortex, which is the outermost layer of the brain. The cerebral cortex is responsible for a wide range of functions, including perception, thought, memory, and voluntary movement. Cortical neurons are characterized by their complex dendritic arbors (also known as dendritic trees, "arbor" is borrowed from the Latin, meaning "tree"), which are branching structures that receive input from other neurons, and their ability to generate large and diverse patterns of action potentials.

There are many other types of neurons found in the nervous system, including:

Spinal cord neurons: These neurons are found in the spinal cord and are involved in the reflexes, motor control and sensation.

Motor neurons: These neurons are found in the spinal cord and brainstem, and they control the contraction of muscles.

Sensory neurons: These neurons are found in sensory organs and are responsible for detecting changes in the environment, such as light, sound, and pressure.

Interneurons: These neurons are found within the central nervous system and they integrate and process information from other neurons.

Ganglion neurons: These neurons are located in the ganglia, masses of nerve cell bodies outside the central nervous system.

Purkinje neurons: These neurons are found in cerebellum and they play a role in motor coordination and balance.

Retinal neurons: These neurons are found in the retina and are responsible for processing visual information.

Hippocampal neurons: These neurons are found in the hippocampus, which is involved in memory and spatial navigation.

All these different types of neurons have distinct characteristics and functions, and their specific roles are still being studied and understood by neuroscientists.

○ **What is the a ganglion (plural: ganglia)?**

ganglion: **an encapsulated collection of nerve-cell bodies**, usually located outside the brain and spinal cord 神经节 （大概是因为一堆细胞体被包裹在一起，所以叫神经节吧）

A ganglion is a group of nerve cells that are located outside of the brain and spinal cord, in the peripheral nervous system. Ganglia are clusters of nerve cell bodies that act as relay stations, where information is processed and then sent on to other parts of the nervous system. They can be found in different locations in the body and have different functions depending on the type of ganglia. Ganglia are also called a "nerve cluster" or "nerve plexus" and they are important in the processing and integration of information in the peripheral nervous system. They have been the focus of studies related to various neurological disorders, such as migraine and chronic pain.

○ **Is the basal ganglia located in the central nervous system or the peripheral nervous system?**

**The basal ganglia is located in the central nervous system (CNS).** The central nervous system is made up of the brain and spinal cord, and is responsible for receiving, processing, and interpreting information from the body's senses, and for controlling the body's responses to that information. The basal ganglia is a group of nuclei located deep within the cerebral hemispheres of the brain, and it is involved in the regulation of voluntary movement and motor control. It receives input from the cerebral cortex and other brain areas and sends output to the thalamus and other motor-related structures. In contrast, the peripheral nervous system is made up of nerves and ganglia that are located outside of the brain and spinal cord, and it is responsible for carrying information to and from the central nervous system and the rest of the body.

**Note**: The term "basal" comes from the fact that most of its elements are located in the basal part of the forebrain. The term ganglia is a **misnomer**: **In modern usage, neural clusters are called "ganglia" only in the peripheral nervous system; in the central nervous system they are called "nuclei".** 

Ganglia位于peripheral nervous system（周围神经系统），但basal ganglia却位于central nervous peripheral system。后者的ganglia可以理解为误用词。

See: [Basal ganglia - wikipedia](https://en.wikipedia.org/wiki/Basal_ganglia).

○ **In modern usage, neural clusters are called "ganglia" only in the peripheral nervous system; in the central nervous system they are called "nuclei". We know that a ganglion is an encapsulated collection of nerve-cell bodies. So, is a nucleus encapsulated?**

In modern usage, the term "ganglion" is typically used to refer to clusters of nerve cell bodies in the peripheral nervous system, while the term "nucleus" is typically used to refer to clusters of nerve cell bodies in the central nervous system.

A nucleus is generally considered to be encapsulated, meaning that it is surrounded by a distinct and well-defined boundary, often formed by a layer of specialized cells called glia. The term "nucleus" is usually used to refer to a distinct, circumscribed group of nerve cells that are located within the brain or spinal cord. These nuclei can be found in different locations in the brain and have different functions depending on the type of nucleus.

A ganglion, on the other hand, is an encapsulated collection of nerve-cell bodies located in the peripheral nervous system and outside of the brain and spinal cord, They often form relay stations, where information is processed and then sent on to other parts of the nervous system.

Overall, the terms "ganglion" and "nucleus" are used to describe clusters of nerve cell bodies in different parts of the nervous system, but the concept is similar in both cases.

○ **What do firing regimes mean for neurons?**

In neuroscience, the firing regime of a neuron refers to the pattern of electrical activity that the neuron produces in response to different inputs. There are several different types of firing regimes that neurons can exhibit, including:

Regular spiking: The neuron fires at a consistent rate, regardless of the input.
Irregular spiking: The neuron's firing rate varies in response to different inputs.
Bursting: The neuron fires in rapid bursts, with intervals of silence in between.
Tonic firing: The neuron maintains a relatively high level of firing activity over time.
The firing regime of a neuron can have important implications for its role in the nervous system. For example, regular spiking neurons are thought to be involved in encoding information about the intensity of a stimulus, while bursting neurons are thought to be involved in signaling the onset or offset of a stimulus.

It is also important to note that, different firing regimes have different temporal dynamics,and the firing regime of a neuron can change depending on the specific physiological or pathological conditions, in which it is functioning.

○ **Why do people use the word "regime" in "firing regimes"?**

The word "regime" is used in neuroscience to describe the pattern of electrical activity exhibited by a neuron because it implies a consistent and orderly pattern of activity, similar to the way a government or organization operates under a specific set of rules or regulations.

In this context, the "firing regime" of a neuron refers to the specific pattern or set of rules that govern the neuron's electrical activity in response to different inputs. Just like different political regimes can have different characteristics, different firing regimes can have different characteristics and play different roles in the nervous system.

The use of the word "regime" in this context is a metaphor borrowed from other fields, such as political science or engineering, to describe a consistent pattern of activity in the nervous system.

### 科研观点

This paper basically gives a simple “one-fits-all” function that can mimic different types of neurons with different firing regimes by changing the parameters a, b, c, and d of the function. The function can be viewed as a reduction form of the Hodgkin–Huxley-type neuronal models, which are complex and accurate. More detailed derivation and analysis of the simple mode is included in the author's book "Dynamical Systems in Neuroscience: The Geometry of Excitability and Bursting".

