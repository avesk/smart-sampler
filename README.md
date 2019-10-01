# smart-sampler
Analyze a wave form, find chords, decompose into midi notes that comprise a midi instruments

## Resources
* [Real time analysis of polyphonic guitar audio](https://pdfs.semanticscholar.org/700f/9225c19eb485448533db82e1b74130f41fac.pdf)
  * Page 16 is interesting, it starts breaking down what fft's of single notes compared to chords look like
  
## Approach
My naive approach idea is given an audio file:
* Chop it up into ~1 second time slices
* Assess if there is a chord at each timeslice
* Do an fft and extract individual notes
* Store notes in a midi array (Essentially putting the extracted note in the best fitting midi bin)
* Fill in missing octaves by pitching up or down existing notes in the array
* Fill in any missing notes that did not have octaves (notes outside of the key of the audio file) by transposing 
exisiting notes in the array.
* Apply an attack/decay envelope + EQ to the (midi array) instrument
