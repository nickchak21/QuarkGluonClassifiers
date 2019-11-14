# Notes and Results of Quark Gluon Classifiers

**Summary** 

In this document, I compare several types of quark and gluon classifiers using a metric called AUC, the area under a ROC curve for a classifier.

**EMD Tagger**

The EMD (Energy Mover's Distance) tagger algorithm works by calculating EMDs between a quark/gluon candidate and the surrounding particles. It will then take the closest n surrounding particles, and based on whether those particles are quarks or gluons, it calculates the probability that the candidate is a gluon.

Setting n from 10 - 200, we achieve the following AUC score graph:

![image](https://user-images.githubusercontent.com/55861445/68832614-6eef2100-067f-11ea-8656-97ee88efc035.png)

The highest AUC is achieved when n = 40, at a value of 0.84855.  

**CNN**

The CNN algorithm works by creating images from the jet data.

- Took up a lot of RAM because it was creating the images, was only able to use 220,000 jets in total or RAM would run out
- Results were alright, optimized to around 0.859 with 20 epochs. In general, CNN is very inefficient
- Default batch sizes seemed to be already optimized, changing them didn’t improve results

**EFN**

- Very efficient, each epoch only took 2-3 seconds when working with 100,000 jets
- Used 35 epochs (which we could do, since it was computationally inexpensive) raised the AUC to over 0.87
- Used 500,000 jets to get AUC of over 0.875, didn’t try optimizing further
- Didn’t mess much with batch sizes, assumed that they were automatically optimized

**PFN**

- This classifier was by far the best in terms of accuracy/AUC, started at over 0.87 even with 100,000 jets and just 5 epochs
- Slightly less efficient than the EFN, but much better than the CNN
- 20 epochs seemed to be good enough to train the PFN to convergence
- This seemed to have the potential to cross the 0.9 barrier for AUC, so I trained/validated/tested with 900,000 jets and 20 epochs. I got an AUC of 0.901684019627313! It does take forever though (12 minutes) to train.
- Didn’t mess much with batch sizes, assumed that they were automatically optimized

**DNN**


**EFP**
