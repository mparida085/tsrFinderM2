# tsrFinderM2
tsrFinderM2 identifies transcription start regions (TSRs) from PRO-Cap and similar nascent transcript sequencing datasets.

Author: Mrutyunjaya Parida, David Price Lab, UIOWA

## Usage:
tsrFinderM2 runs on Python v2.7+. The tsrFinderM2 evaluates every TSR window across the genome for the maximum 5' read density (max transcription start site) at the center of the window. tsrFinderM2I is an interface program that runs the tsrFinderM2 program. It checks for errors in a user's input. If errors are found the tsrFinderM2I program displays the usage example and parameter description prior to exiting the run. If no use input errors are found tsrFinderM2I runs tsrFinderM2 program automatically.

Both tsrFinderM2 and tsrFinderM2I are intended to be run via a Python v2.7+ interpreter installed on your desired operating system of choice such as Windows, Mac or Linux. Additionally, tsrFinderM2I requires the joblib python module installed prior to the tsrFinderM2 run. If the module is missing tsrFinderM2I will guide you on installing the module. Finally, tsrFinderv2I expects the following syntax on a linux command-line interface:

```
python tsrFinderM2I <mapped-fragments.bed file> <TSR window size> <TSR read depth> <maximum fragment size> <chromosome sizes file>

Example run: python tsrFinderM2I mapped-fragment.bed 200 10 600 hg38.chrom.sizes.txt

```
Maintain the program files under the tsrFinderM2_dir folder.

### Parameter description:
```
mapped-fragments.bed file: A mapped fragment bed file can be generated from alignment files in sam
                           format using samtools and bedtools.

TSR window size:           A desired size of the TSR window (an integer). We found TSRs are usually
                           20bp in width and are often clustered. This parameter can be increased or
			   decreased to find longer or shorter sized TSRs.

TSR read depth:            The minimum amount of reads per TSR (an integer). This determination of
                           this parameter can vary depending on sequencing depth and the amount of
			   background signal in your dataset.

maximum fragment size:     This parameter (an integer) allows exclusion of excessively long PRO-Seq
                           reads. 

chromosome sizes file:     tsrFinderM2I requires a chromosome sizes file. This file can be obtained
                           using [fetchChromSizes](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/)
			   utility.
```

### Output:
The final output is a comprehensive tab-delimited text file which contains information about both FW and RV strand non-overlapping TSR boundaries, the MaxTSS position, # of MaxTSS reads, sum of MaxTSS read lengths, # of MaxTSS reads, and strand.
