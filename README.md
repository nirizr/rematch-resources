# rematch-resources
A repository to store rematch related resources such as articles, papers, 
example tools, etc


# Papers

* [Parallelization of Machine Learning Applied to Call Graphs of Binaries for Malware Detection]  
  > TL;DR 
  > Use Short Path Graph Kernel to identify similarities and apply an SVM on it, parallelize with GPUs using OpenMP platform.
  > 
  > I only skimmed it. 

* [Pairwise Graph Similarities using Shortest Path Graph Kernel] 
  > They seem to use the same method as the previous paper only adding source, also from the same university
  > I didn't see any usage of OpenMP.

* [An Introduction to Graph Kernels]
  > This is a presentation about graph diffing, they start by presenting the basic problem
  >
  > "Given two graphs G and G'  from the space G. 
  > The problem of graph comparison is to find a mapping s : G x G -> R such that s9G,G') quantifies the dis/similarity of G and G'."
  > 
  > They start by presenting N methods to diff a graph:
  >  1. Graph Isomorphism 
  >  Find a subset of edges and vertices in G1 which is also present in G2. 
  > They also mention that Graph Isomorphism is NP-Complete 
  > 
  >   2. Sub-graph ismorphism
  > I didn't understand the difference here other than comparing full-graph to finding / identify sub-graph
  > e.g detect double-usage of inlined functions vs static regular ones.
  > 
  >   3. Graph Edit Distances (@nirizr, @ariel)
  > Define a way to represent a graph.
  > Define a set operation to perform on that represntation.
  > Define a cost per operation.
  >  Count the number of operations needed to tranfmogify G0 to G1,  
  > Probably, this one is good for Patch Detection and subtle similarities.
  > We need a *good* way to define a Cost function and a Graph Representation Function.
  > 
  >  4. Topoligal Descriptor 
  > Basically, just pick a set of interesting features and use distance metrics to diff them.
  > How do you pick the diffing method?
  > Can you put it on a matrix and maybe define kernels and by this way find groups? 
  > TBC
  > I want to see this talk live.

*  [Automated Attacker Correlation for Malicious Code]
   > One of the papers by Halvar and Erro which provides the fundementals for BinDiff,
   > Use MD-Indexes to hash the function, xrefs, and nodes, save it into a DB and query it/
   > Remember they're exporting it from IDA, this took a lot of effort. 
   > Use BinDiff eventually to perform the diffing.
   > Citation needed.
*  [Graph Based Comparison of Executable Objects]
   > This is a more practical paper by Halvar and Rolf, (which later became one of the main developers of BinDiff),
   > after reverse engineering the whole product by accident).
   > Unlike the previous paper, they present the problem along with a practical solution followed by pseudocode
   > TBC


# Frameworks

* [PyKernels]
   > This is a basically a library for working with kernel methods, they provide several algorithms to fiddle with.
   > It's pretty practicaal and easy to use, maybe we should consider using it in our Server? 
   > While it hasn't been updated over a year, we might consider using it. 
   > Does sklearn provide the same capabilities? 
* [OpenREIL]
   > OpenREIL is an open-source implementation of the REIL used by BinDiff, it is basically a lifter
   > of the x86_64 and ARM assembly to OpenREIL. [cr4sh] also hooked up z3 support for it, along with basic
   > PE and ELF parsing. 
* [MCSema]
  > This is another lifter released by ToB, might be worth to look at and also check [manticore].
  > Unlike most lifters they try to support most of the x86_64 subset, along with archaic instructions like FPU and SIMD.
* [GRAP]
  > Presented in REcon Brussel 2017, I've looked at it before, it's an incomplete framework which just does
  > the core operations of diffing, but lacks UX and the like.
  > I've read the code long ago but I don't quite remember much from, it's not an IDA plugin. 
  > TBC


# Still need to read:
* https://static.googleusercontent.com/media/www.zynamics.com/en//downloads/dimva_paper2.pdf
* https://www.stat.purdue.edu/~vishy/talks/Graphs.pdf
* https://www.sciencedirect.com/science/article/pii/S0893965907001012
* https://www.ncbi.nlm.nih.gov/pmc/articles/PMC110779/
* https://www.sstic.org/media/SSTIC2017/SSTIC-actes/bincat_purrfecting_binary_static_analysis/SSTIC2017-Article-bincat_purrfecting_binary_static_analysis-biondi_rigo_zennou_mehrenberger.pdf
* https://github.com/facebookresearch/faiss

[OpenREIL]: https://github.com/Cr4sh/openreil
[cr4sh]: https://twitter.com/cr4sh
[MCSema]: https://github.com/trailofbits/mcsema
[manticore]: https://github.com/trailofbits/manticore
[GRAP]: https://bitbucket.org/cybertools/grap
[Parallelization of Machine Learning Applied to Call Graphs of Binaries for Malware Detection]: https://www.eecis.udel.edu/~wkillian/latest/resources/Parallelization.of.Machine.Learning.Applied.to.Call.Graphs.of.Binaries.for.Malware.Detection.pdf
[Pairwise Graph Similarities using Shortest Path Graph Kernel]: https://github.com/tristanvdb/pairwise-graph-similarities
[An Introduction to Graph Kernels]: https://www.ethz.ch/content/dam/ethz/special-interest/bsse/borgwardt-lab/documents/slides/CA10_GraphKernels_intro.pdf
[PyKernels]: https://github.com/gmum/pykernels
[Automated Attacker Correlation for Malicious Code]:  https://www.sto.nato.int/publications/STO%20Meeting%20Proceedings/RTO-MP-IST-091/MP-IST-091-26.pdf
[Graph Based Comparison of Executable Objects]: https://static.googleusercontent.com/media/www.zynamics.com/en//downloads/bindiffsstic05-1.pdf
