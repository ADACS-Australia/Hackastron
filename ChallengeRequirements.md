
# Astrohack Challenge Requirements


## 1 Efficient catalogue cross-matching 
Variations in the brightness of objects in the sky over time can be the result of a range of exciting astronomical phenomena – from 
exploding stars to black holes. Identification of these events from their light curves means that we need to first form these light 
curves by joining many catalogues.

This joining, or cross-matching, process presents a number of challenges – uncertainties in position, source confusion, missing data, 
and weird shaped sources. We currently have a few methods that work OK when the catalogues are very well behaved, but which are either 
very slow, or make many errors.

**Creating an effective, efficient, and scalable solution would greatly assist in the ongoing research into these objects. 
An ideal solution would be something that could run within a database and be updated as new catalogues are added, but even a 
stand-alone script would be of great benefit.**

### Challenge Owner
Paul Hancock (Curtin University)

### Challenge specifics
_Technical info_

- You can work on your own computer or work on a Nimbus VM provided by Pawsey
- Sample catalogs for crossmatching are provided (csv format) in this repo
- No specific software is needed to read the data

*Background reading/info:*
- additional info is provided in this repo

*Challenge specific judging criteria*
- Who gets the highest correct cross-matching score
- This is assessed automatically by software

## 2 De-noising of spectra
Decomposing complex spectra made up of multiple, potentially overlapping Gaussian components is a challenge for Galactic and 
extragalactic astrophysics, but is critical for understanding the properties of gas within galaxies.

Our team is currently using a code called GaussPy (Lindner et al. 2015) that autonomously decomposes spectra into Gaussian components, 
which improves upon previous methodologies (namely by-hand decomposition) by removing the need for human input (and subjectivity!), 
increasing the reproducibility, and allowing for the decomposition of large samples of data. GaussPy identifies different Gaussian 
components by finding inversions in the second derivative of the data, but since the data includes noise that mimics inversions, it 
uses a machine learning algorithm to determine the optimal parameters for first smoothing the data. For lower signal-to-noise data, 
the maximum confidence level of the decomposition produced by GaussPy is low (at best ~70%, Murray et al. 2017) and primarily due to 
the difficulty in separating the noise from the spectral signal using only smoothing.

**We would like to improve the performance of the Gaussian decomposition algorithm by first devising a way to isolate the noise from 
the spectral features or ”de-noise” the spectra (e.g. using wavelet transforms) in order to improve the confidence level of the 
decomposition. Such an application will be extremely valuable to use on the large number of spectra produced by the upcoming large 
all sky surveys such as GASKAP and WALLABY. Additionally, an easy to use ”de-noising” software would be useful for other astronomical 
data.**

### Challenge Owner
On behalf of Helga Denes (ANU), Boyang Liu, University of Western Australia

### Challenge specifics
*Technical info/skills*

- You can work on your own computer or work on a Nimbus VM provided by Pawsey
- data is provided in this repo

*Background reading/info:*
- additional info is provided in this repo

*Challenge specific judging criteria*
- TBC

## 3 (Space) Weather database and visualisation 
One of the main goals of the Murchison Widefield Array (MWA) is the detection of the emission line of neutral hydrogen 
(also known as the 21cm line) during the Epoch of Reionisation (the dawn of the first galaxies in the universe). As this signal will 
be very weak,  a comprehensive characterisation of everything between us and this signal, including many astronomical sources, as well 
as the behaviour of the Earth’s ionosphere is vital.

The MWA team has begun working on characterising the ionosphere, however, in order to identify triggers of ionospheric activity, our 
own data needs to be compared and correlated with various weather data, including space weather (e.g. solar activity, meteor showers), 
earth weather (e.g. thunderstorm activity) and other possible actors (e.g. earthquakes, volcano eruptions).

**This challenge is to design a tool that parses information on various types of weather to be displayed for a time and area. For example, 
if one was interested in what was happening around Perth on the 1st of September 2015, then this tool would tell me what had occurred: 
a meteor shower, solar activity, thunderstorms, earthquakes. As the MWA has a big field of view a bonus outcome for this challenge would 
be an app which could also display the area over which the weather acted.**
 
### Challenge Owner
Christopher Jordan (Curtin University)

### Challenge specifics
*Technical info/skills*
- You can work on your own computer or work on a Nimbus VM provided by Pawsey
- No specific software is required
- Data mining, connecting to api
- Presenting data in an interrogatable app

*Background reading/info:*
- Requesting data from api
- Identifying sources of useful data, e.g. http://www.ga.gov.au/oracle/geomag/k_form.jsp

*Challenge specific judging criteria*
- a tool that interrogates at least 3 services
- possibility to expand tool by including new service connections later on

## 4 Using Machine Learning to characterise galaxy components 
There are many sub-components to a galaxy, e.g. bars, nuclei, thin disk, thick disk, spiral arms or shells to name a few. 
Each of these component is potentially a result of different formation mechanisms and will reflect distinct events in a 
galaxy’s evolutionary history.

However, even though some components are prominent in a galaxy’s light profile they may only contain a modest fraction of the total mass. 
Some components can therefore be thought of as primary (e.g. bulges and disks), and others as secondary perturbations 
of these primary structures (e.g.bars, pseudo-bulges, rings etc). Understanding how the fraction of mass in each component 
changes with galaxy type and over time is an integral part of understanding how galaxies assemble their mass and grow.

**There are various fitting codes available to fit a galaxy’s light profile, however, it is inherently problematic to decompose 
a galaxy into its bulge and disk components and return reliable bulge-to-disk fractions 
(i.e. the fraction of mass found in each component). Another approach to this problem is applying machine learning 
techniques to the images of galaxies directly. This challenge will create and use a sample of simulated galaxy images to train 
machine learning models and test whether this results in a viable model for bulge-disk decomposition on actual galaxy images.**

### Challenge Owner
Rebecca Lange (Curtin University)

### Challenge specifics
*Technical info*
- You can work on your own computer or work on a Nimbus VM provided by Pawsey
- Sample simulated images with multi-labels are provided on Nimbus
- Real image data is provided for testing of the algorithm

*Background reading:*
- Galaxy And Mass Assembly (GAMA): mass-size relations of z = 0 bulges, discs and spheroids - http://adsabs.harvard.edu/abs/2016MNRAS.462.1470L
- Note, we think bulge fraction for real images can only be measured within 10% accuracy, simulated images are far more accurate
- ML image classification, transfer learning

*Challenge specific judging criteria*
- Implement an ML algorithm to classify galaxies according their bulge-to-total (B/T) ratio 
(ie the amount of light/mass in the bulge when compared to the total)
- Achieve 80+% accuracy on sample data
- Added challenge -> achieve as high as possible accuracy on real image data
 
## 5 Looking the other way, a weather warning system for telescopes
Looking the other way: New interferometric dish based telescope facilities executing unsupervised observations such as ASKAP and SKA 
face a multitude of new challenges in the way of equipment protection from severe weather.
Using near real-time high resolution satellite imagery as obtained from the Japanese Himawari 8 satellite, 
it is possible to detect convective developments early, and quickly, using the “overshooting tops” algorithm 
(will be provided, along with sample data). 

**Develop a python code that identifies new cells as they develop, and track the 
convective cells’ centers, dimensions, determine their movement, and predict position, size, and severity for time steps 
of 10, 30, and 60 minutes into the future.**
 
### Challenge Owner
Balthasar Indermuehle (CSIRO)

### Challenge specifics
*Technical info*
- The required data and software are made available through an NCI instance, log in details will be handed out in person

*Background reading:*
- “overshooting tops” algorithm and its outputs
- please find the instructions in the powerpoint downloadable from this site:
   http://hackathon.inside.net/ 

*Challenge specific judging criteria*
- TBC

## 6 Code optimisation for the MWA tied-array beam pattern simulation 
The Murchison Widefield Array (MWA) is a low-frequency Square Kilometre Array (SKA) precursor radio telescope located in the 
Western Australian outback, approximately 800 km north of Perth. The MWA consists of 128 elements (called tiles) which each 
contain 16 dipoles in a 4 × 4 m grid. One of the MWA recording modes is the Voltage Capture System (VCS) which allows us to 
capture data in its most flexible form and then post-process it to get the desired science product.

One of our challenges is accurately calibrating the VCS data to get meaningful estimates of the brightness of objects, such as 
pulsars, allowing us to pursue more detailed scientific analysis. To calibrate the VCS data we currently use a simulation of the 
telescope’s “beam pattern” to calculate the relevant parameters for the instrument calibration. A beam pattern (or radiation pattern) 
is a map of the radio telescope’s sensitivity across the sky and is a function of where you are pointing on the sky, the wavelength 
at which you are observing, and the separation of each of your array elements. In our case, the separation of elements ranges 
from ∼1 m to >3 km, the observing wavelengths range from 1 – 4 metres, and the possible observing directions are effectively 
anywhere on the visible sky.

While there is Python code available to do this kind of simulation on a per element (tile) basis, there was previously no code 
that would simulate the radiation pattern when using all 128 elements combined (i.e. a tied-array beam). The individual tile 
simulation does not require high-resolution simulations and we can sample on a∼ 5 × 5 degrees scale and still get excellent results. 
However, when moving to the tied-array beam simulation, we need the simulation grid to be fine enough to resolve differences on scales 
less than 0.02 × 0.02 degrees. Furthermore, to accurately model the response, this grid needs to sample the entire southern sky, i.e. 
zenith angle θ = [0, π], azimuthal angle φ = [0, 2π]. The whole process is embarrassingly parallel, as we are effectively just 
computing some function F (θ, φ) over the whole sky.

**For this hackathon challenge there a two possible pathways: working on optimising/speeding up either the Python or the 
C/C++/CUDA implementations of the calibration software.**

### Challenge Owners
Bradley Meyers, Marcin Sokolowski, Paul Hancock (Curtin University)

### Challenge specifics
*Technical info*
- A computer with the required software (and hardware) and data has been set up, log in info will be handed out in person

- **Python:**
We currently have a MPI-enabled Python script that is able to do these computations, but it is relatively slow, taking hours 
to complete. The primary issue is that we are required to calculate the beam pattern for each “direction” on the sky, which 
amounts to computing values for over 3 billion points. This also poses an interesting issue surrounding effective memory management 
and worker load within Python which typically removes the user from any direct memory control. Currently, the calculations are 
implemented such that if we have N workers, then the sky is split into N chunks and each worker then evaluates the beam pattern 
for every point on the grid within its allocated range. Optimising this code to be faster or more efficient would be of great benefit 
to the processing of MWA VCS data.
- **C/C++/CUDA:**
There is also a C/CUDA version for part of this code, which drastically reduces the computation time for some calculations, and 
again acts to split the sky up (based on device memory constraints). This part of the code takes roughly 5 minutes (including file I/O) 
to form the tied-array beam pattern over the whole sky, but it does not include the weighting provided by the individual tile beam 
pattern. The other half of the code (which calculates the individual antenna element radiation pattern), written in C++ is not 
CUDA-enabled and does not employ any form of interpolation. This ultimately causes it to be much slower that the Python/MPI version. 
Simulating the tile beam is therefore the area where we need to optimize and/or include new functionality. One way to do this would be 
to include some form of interpolation, because the tile beam pattern changes on scales much larger than the tied-array beam. Because the 
tied-array beam will potentially be calculated in independent chunks, the interpolation would need to be intelligent enough to figure 
out what parts of the coarse tile beam grid need to be mapped to the finer tied-array beam grid and do this self-consistently, such 
that there are no edge effects. Additionally, the tile beam code employs spherical harmonics and currently computes the beam power for 
an individual azimuth and zenith angle (φ, θ), so converting these functions to be done on a GPU and/or implementing it in a more 
vectorized manner could also provide a much faster interface.

*Background reading:*
- Tile beam pattern simulation (C++/CUDA challenge): https://arxiv.org/abs/1710.07478
- Tied-array beam simulation (Python challenge): the Appendix of https://arxiv.org/abs/1709.03651

*Challenge specific judging criteria*
- do we get the same numbers out in the end, and 
- was it faster than before?
If the answer is yes to both of those, then we consider that a success.


