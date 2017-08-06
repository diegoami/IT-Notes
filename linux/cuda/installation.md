# INSTALLING CUDA ON UBUNT 16.06

* Make sure you execute the steps in the manual
* Use the third method installation (Deb remote) - no need to leave the GUI
* one example in Cuda samples will not compile - filter it out in the Makefile
* remember to add PATH in .profilerc

```
FILTER_OUT := 3_Imaging/cudaDecodeGL/Makefile
```