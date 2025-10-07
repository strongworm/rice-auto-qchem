<p align="center">
  <img src="https://github.com/beef-broccoli/misc-files/blob/9332ec68f7f798a3c2819dad9a0d2280769985ee/autoqchem.png" alt="logo" width="600">
</p>

---
## Welcome to Auto-QChem Rice Fork!

This version of Auto-QChem has been modified to work for the Rice Supercomputing Cluster (NOTS).  Before using this package, make sure to get a CRC NOTS Account, which you can apply for here: https://www.crc.rice.edu/app/ricelogin.php

It may also be helpful in some cases to consult the NOTS Documentation: https://kb.rice.edu/page.php?id=147970

Many thanks to Kirk Anne and Bryan Raney at the Rice CRC for helping me troubleshoot Auto-QChem and get it running on NOTS.  If you have issues with Auto-QChem on Rice NOTS I highly recommend reaching out to them.  Also thanks to Sven Roediger from the Doyle Lab for all his help! 

## How to Install (modified from regular Auto-QChem Install instructions)

1. Install conda: https://www.anaconda.com. I find it easier to just download the installer and install like how you would with any software.

2. Conda allows you to create separate software development environments for different purposes. We will create an environment just for auto-qchem. Open terminal and run this, and answer "y" to the prompt:

conda create --name autoqchem python=3.8 ipython

3. With conda environments, you need to activate them before you use. Run this in terminal:

conda activate autoqchem 

4. We have some separate packages to install first. (OpenBabel does not work on pip). Run the following commands in terminal one by one, and answer "y":

conda install -c conda-forge openbabel

5. Download the zip file of this package onto your computer, open the Rice Tutorial Jupyter Notebook, and use as usual.  Do not install Auto-QChem using pip, this will not work for Rice NOTS.  


## Quick links

[Database user instructions](https://github.com/doyle-lab-ucla/auto-qchem/blob/master/DB.md)

[Code base documentation](https://doyle-lab-ucla.github.io/auto-qchem)

[What exactly are all the descriptors?](https://github.com/doyle-lab-ucla/auto-qchem/blob/master/DESCRIPTOR.md)

---
[Repo with example jupyter notebooks](https://github.com/doyle-lab-ucla/auto-qchem-notebook-examples)

[Database link](https://autoqchem.org)

[Auto-QChem paper (publisher)](https://pubs.rsc.org/en/content/articlelanding/2022/re/d2re00030j#!divCitation), [free pdf](https://drive.google.com/file/d/1M8Ydqlk5Kbc_8WoR5dAm_JIbf2IBJTlU/view?usp=share_link)

## Note on the changes I've made to adjust Auto-QChem for NOTS:

All of the changes are to the slurm_manager.py file  I adjusted the "_create_slurm_file_from_gaussian_file" function to create sh files that Slurm on NOTS can understand.  The main thing to make note of for users is that the time it takes for jobs to complete can be adjusted by changing line 612 (this will allow Slurm to fit in jobs between other jobs if you give it an accurate estimate of how long the jobs will take) and the amount of memory available can also be adjusted by changing line 608. When you are adjusting the number of cpus, take care that the number of processors multipled by cpus per task does not exceed 96, as that is the maximum number of cpu's available on any node on NOTS.  
