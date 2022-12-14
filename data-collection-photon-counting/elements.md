# Elements of X-ray Diffraction

## Basic Diffraction

X-ray diffraction is the phenomenon resulting from scattering of photons by atoms where the positions of the atoms has translational symmetry. The correlation of atomic positions gives rise to constructive interference, which in turn gives rise to preferred directions for scattered photons. If these preferred directions are mapped on to a detector the result is positions on the detector where more photons are found - spots - and (ideally blank) regions between them - background:

![Example of X-ray diffraction from a cubic insulin crystal](./diffraction.jpg)

The positions of the spots depends on the geometry of the experimental set up and the unit cell of the crystal. The _intensity_ of the spots is dependent on the intensity of the beam, the number of unit cells illuminated by the beam, any effects from sample absorption and - of greatest interest - the arrangement of atoms within the unit cell. In practice, it is the electrons which scatter (since the scattering cross section is ~ 2000x that of protons) so we are actually measuring the positions of electrons within the unit cell, which could look something like:

![Example of electron density within a unit cell](./electrons.jpg)

These are data taken from a very well ordered small molecule. The intensity measurement itself is related to the electron density within the unit cell as the squared modulus of the Fourier transform of the density: low angle reflections depend on the bulk arrangement of electrons and higher angle scattering results from finer detail. These give rise to a number of important facts:

- the experimental geometry is critical for correctly interpreting the diffraction data
- all atoms contribute to all intensities
- atom identification is inferred from the electron densities (in the absence of additional information)

The extent to which you can measure high resolution data depends largely on the overall internal order of the crystal. A very well ordered crystal will have a very high degree of correlation across multiple unit cells of atomic positions, thus ensuring that the construcive interference is measurable. In a less well ordered crystal this correlation can break down, reducing the capability for measuring the fine detail. There is a critical point where the number of data measured match the number of free parameters required to model that data - 0.84??. If data at this resolution or higher are not observed then additional information will be needed to ensure that the refinement is well determined. Fortunately we have access to a vast amount of external information, particularly in structural biology. The fact that proteins are made from amino acids, which are very well understood and (largely) have very well characterised geometry means that we can balance the data to parameter ratio by including more _a priori_ information about the atomic positions.

## Symmetry

Anything crystalline _must_ by definition have symmetry: at the very least there will be translational symmetry between unit cells. Most crystals have some additional symmetry e.g. some rotational symmetry which may be used to map the atomic positions onto themselves. This rotational symmetry within the crystal is then observed within the diffracted intensities. In addition, this symmetry has implications for the shape of the unit cell: if there is four-fold rotation symmetry about a certain axis, then that axis must be perpendicular to a square face of the unit cell and all angles in the unit cell must be 90??. The reverse is however not necessarily true: a square face unit cell does not require four-fold symmetry though it is likely that there is.

The practical result of this symmetry is that there are multiple copies of the same diffraction intensity, related by the same rotational symmetry operations as the atomic positions. This therefore means we can afford to record fewer individual measurements for a given volume of unit cell, or we can improve the measurements by measuring and comparing multiple copies. As will be discussed [later](./strategy.md) this duplication is in fact critical for properly interpreting the data and correctly assessing the data quality. Of course there is no such thing as a free lunch: though the symmetry reduces the number of data required for a given volume of unit cell, it will increase the volume of the unit cell by a corresponding amount, which ultimately gives rise to the resolution criterion above. It does however modify the geometrical considerations of performing the experiment.

## Geometry

Understanding the geometry of an X-ray diffraction experiment is critical to successful interpretation of the data. Starting from [Bragg's law](https://en.wikipedia.org/wiki/Bragg%27s_law) it is possible to derive almost everything required to successfullt interpret a diffraction pattern, however this is a substantial body of work and out of context here. The most important aspects are:

- knowing the X-ray wavelength
- knowing the position of the detector (typically encoded as a distance and beam centre)
- knowing the orientation and rotation direction of the goniometer

This is illustrated as:

![Geometry of an X-ray diffraction experiment](./geometry.jpg)

Which shows the orientation of the detector, the origin, the fast and slow directions, the orientation of the unit cell and the goniometer direction - this image was generated with `dials.geometry_viewer` which can be useful in ensuring that the experimental metadata make sense.

The position of the detector should be given some thought: for a given wavelength moving the detector closer to the sample allows a higher resolution to be accessed at the cost of reducing the space between spots. Moving the detector back increases the space between spots, but limits the resolution which can be reached. The ideal detector position will balance these two constraints by ensuring that the spots are well separated but that the full resolution range is recorded - generally it is worth keeping the detector slightly closer than you think you need to ensure that you are not missing useful data. As mentioned above, the positions of reflections is determined by the orientation and size of the unit cell - in practice this has the most obvious impact that crystals with a small unit cell have more widely separated spots: for crystals with a large unit cell e.g. virus crystals or complexes the spacing of the spots can be a limiting factor.

## Detectors

This wil be discussed in more detal [later](./detection.md) but in general the instrument of choice is an area detector, which is usually rectangular and sufficiently large to ensure that all the data which are needed can be recorded in one "run" - i.e. with the detector in a single position. The sensitivity, pixel size and behaviour of the detector are important to the experiment, but in general do not alter the fundamental theory.

## Summary

The basic theory which defines the X-ray diffraction experiment has been well understood for over a century. In practice not all of this needs to be understood in detail to perform a diffraction experiment or to use data processing software, but the basics are useful in terms of understanding how to use the instrumentation for performing an experiment. The details of performing the experiment are usually summarised as a [data collection strategy](./strategy.md), which will be discussed in the next section.
