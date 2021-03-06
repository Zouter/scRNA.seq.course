---
output: html_document
---



## Experimental methods

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{figures/moores-law} 

}

\caption{Moore's law in single cell transcriptomics (image taken from [Svensson et al](https://arxiv.org/abs/1704.01379))}(\#fig:unnamed-chunk-2)
\end{figure}

Development of new methods and protocols for scRNA-seq is currently a very active area of research, and several protocols have been published over the last few years. An non-comprehensive list includes:

* CEL-seq [@Hashimshony2012-kd]
* CEL-seq2 [@Hashimshony2016-lx]
* Drop-seq [@Macosko2015-ix]
* InDrop-seq [@Klein2015-kz]
* MARS-seq [@Jaitin2014-ko]
* SCRB-seq [@Soumillon2014-eu]
* Seq-well [@Gierahn2017-es]
* Smart-seq [@Picelli2014-ic]
* Smart-seq2 [@Picelli2014-ic]
* [SMARTer](http://www.clontech.com/US/Products/cDNA_Synthesis_and_Library_Construction/Next_Gen_Sequencing_Kits/Total_RNA-Seq/Universal_RNA_Seq_Random_Primed)
* STRT-seq [@Islam2014-cn]

The methods can be categorized in different ways, but the two most important aspects are __quantification__ and __capture__. 

For quantification, there are two types, __full-length__ and __tag-based__. The former tries to achieve a uniform read coverage of each transcript. By contrast, tag-based protocols only capture either the 5'- or 3'-end of each RNA. The choice of quantification method has important implications for what types of analyses the data can be used for. In theory, full-length protocols should provide an even coverage of transcripts, but as we shall see, there are often biases in the coverage. The main advantage of tag-based protocol is that they can be combined with unique molecular identifiers (UMIs) which can help improve the quantification (see chapter \@ref(umichapter)). On the other hand, being restricted to one end of the transcript may reduce the mappability and it also makes it harder to distinguish different isoforms [@Archer2016-zq].

The strategy used for capture determines throughput, how the cells can be selected as well as what kind of additional information besides the sequencing that can be obtained. The three most widely used options are __microwell-__, __microfluidic-__ and __droplet-__ based.

\begin{figure}

{\centering \includegraphics[width=0.7\linewidth]{figures/300px-Microplates} 

}

\caption{Image of microwell plates (image taken from Wikipedia)}(\#fig:unnamed-chunk-3)
\end{figure}

For well-based platforms, cells are isolated using for example pipette or laser capture and placed in microfluidic wells. One advantage of well-based methods is that they can be combined with fluorescent activated cell sorting (FACS), making it possible to select cells based on surface markers. This strategy is thus very useful for situations when one wants to isolate a specific subset of cells for sequencing. Another advantage is that one can take pictures of the cells. The image provides an additional modality and a particularly useful application is to identify wells containg damaged cells or doublets. The main drawback of these methods is that they are often  low-throughput and the amount of work required per cell may be considerable.

\begin{figure}

{\centering \includegraphics[width=0.7\linewidth]{figures/fluidigmC1} 

}

\caption{Image of a 96-well Fluidigm C1 chip (image taken from Fluidigm)}(\#fig:unnamed-chunk-4)
\end{figure}

Microfluidic platforms, such as [Fluidigm's C1](https://www.fluidigm.com/products/c1-system#workflow), provide a more integrated system for capturing cells and for carrying out the reactions necessary for the library preparations. Thus, they provide a higher throughput than microwell based platforms. Typically, only around 10% of cells are captured in a microfluidic platform and thus they are not appropriate if one is dealing with rare cell-types or very small amounts of input. Moreover, the chip is relatively expensive, but since reactions can be carried out in a smaller volume money can be saved on reagents.

\begin{figure}

{\centering \includegraphics[width=0.6\linewidth]{figures/drop-seq} 

}

\caption{Schematic overview of the drop-seq method (Image taken from Macosko et al)}(\#fig:unnamed-chunk-5)
\end{figure}

The idea behind droplet based methods is to encapsulate each individual cell inside a nanoliter droplet together with a bead. The bead is loaded with the enzymes required to construct the library. In particular, each bead contains a unique barcode which is attached to all of the reads originating from that cell. Thus, all of the droplets can be pooled, sequenced together and the reads can subsequently be assigned to the cell of origin based on the barcodes. Droplet platforms typically have the highest throughput since the library preparation costs are on the order of $.05$ USD/cell. Instead, sequencing costs often become the limiting factor and a typical experiment the coverage is low with only a few thousand different transcripts detected [@Ziegenhain2017-cu].

## What platform to use for my experiment?

The most suitable platform depends on the biological question at hand. For example, if one is interested in characterizing the composition of a tissue, then a droplet-based method which will allow a very large number of cells to be captured is likely to be the most appropriate. On the other hand, if one is interesting in characterizing a rare cell-population for which there is a known surface marker, then it is probably best to enrich using FACS and then sequence a smaller number of cells.

Clearly, full-length transcript quantification will be more appropriate if one is interested in studying different isoforms since tagged protocols are much more limited. By contrast, UMIs can only be used with tagged protocols and they can facilitate gene-level quantification.

Two recent studies from the Enard group [@Ziegenhain2017-cu] and the Teichmann group [@Svensson2017-op] have compared several different protocols. In their study, Ziegenhain et al compared five different protocols on the same sample of mouse embryonic stem cells (mESCs). By controlling for the number of cells as well as the sequencing depth, the authors were able to directly compare the sensitivity, noise-levels and costs of the different protocols. One example of their conclusions is illustrated in the figure below which shows the number of genes detected (for a given detection threshold) for the different methods. As you can see, there is almost a two-fold difference between drop-seq and Smart-seq2, suggesting that the choice of protocol can have a major impact on the study

\begin{figure}

{\centering \includegraphics[width=0.6\linewidth]{figures/ziegenhainEnardFig1} 

}

\caption{Enard group study}(\#fig:unnamed-chunk-6)
\end{figure}

Svensson et al take a different approach by using synthetic transcripts (spike-ins, more about these later) with known concentrations to measure the accuracy and sensitivity of different protocols. Comparing a wide range of studies, they also reported substantial differences between the protocols.

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{figures/svenssonTeichmannFig2} 

}

\caption{Teichmann group study}(\#fig:unnamed-chunk-7)
\end{figure}

As protocols are developed and computational methods for quantifying the technical noise are improved, it is likely that future studies will help us gain further insights regarding the strengths of the different methods. These comparative studies are helpful not only for helping researchers decide which protocol to use, but also for developing new methods as the benchmarking makes it possible to determine what strategies are the most useful ones.
