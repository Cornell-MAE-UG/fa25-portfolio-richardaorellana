---
layout: project
title: Torque Wrench CAD and FEA
description: Introductory FEA Project
technologies: ["Autodesk Fusion", "Ansys Mechanical"]
image: /assets/images/LongWrench3.jpg
---

For my "Mechanics of Engineering Materials Class" (MAE 3270), we were asked to design a torque wrench capable of applying up to 600 Nm of torque while also meeting certain safety criterion. The wrench had to be modeled in a CAD software and then analyzed using FEA. The goal was not to create an aesthetically pleasing wrench, it was to create a functional one. 

![LongWrench1]({{ "/assets/images/LongWrench1.png" | relative_url }}){: .inline-image-l}
![LongWrench2]({{ "/assets/images/LongWrench2.png" | relative_url }}){: .inline-image-l}
![LongWrench3]({{ "/assets/images/LongWrench3.png" | relative_url }}){: .inline-image-l}

The material chosen for this wrench was Ti-4Al-6V, one of the most commonly used titanium alloys. It was chosen for its low stiffness and high strength. The high strength ensures that it met the relevant safety criterion while the low stiffness makes it more ductile. Ductility was important for this project as a minimum strain gauge reading of 1 mV/V was required somewhere on the wrench when at maximum load. 

This model was then imported into Ansys Mechanical and a finite element analysis was done of it. The meshing for this model had around ~30k nodes arranged into rectangles on the relevant faces. While Ansys does not make use of the plane strain assumption used in beam theory, all hand calculations were based on planar stress elements. The top 0.4 inches of the drive were clamped down using a zero displacement condition and a force of 30 lbf was applied to the end of the wrench, perpendicular to its length. 

![TipDisplacement]({{ "/assets/images/TipDisplacement.png" | relative_url }}){: .inline-image-l}

Here are some photos of the results!

![NormalStrain]({{ "/assets/images/NormalStrain.png" | relative_url }}){: .inline-image-l}
![MaxPrincipal]({{ "/assets/images/MaxPrincipal.png" | relative_url }}){: .inline-image-l}

The maximum normal stress occurs on the lower part of the drive. There is some stress near the boundary between the clamped section and the rest of the drive but there are stress concentrations where the drive meets the handle. These reach a highest magnitude of 77559 psi! This is multiple times greater than the hand calculated value of 19200 psi. The deflection of the tip was also larger being 0.780 inches instead of the calculated 0.640 inches. Assuming a strain gauge was placed one inch from the drive on the portion of the handle that experiences stress, the hand calcualtions say that it would experience 18240 psi of normal stress and 1140 microstrain. The FEA results almost completely match these numbers, as determined by probing!!

Since this is a purely hypothetical wrench, I looked for an incredibly expensive half-bridge strain gauge. An average half-bridge strain gauge provides 1mV/V per 1000 microstrain, so this is the perfect device to meet the requirement. A full bridge could double that number if higher sensitivity was desired. The device I chose is the Omega SGT-8/350-LD41 Half-Bridge Diaphragm Strain Gauge. A pack of 5 costs around $140 but its the perfect size to place all over the wrench handle. Being 1.1 mm x 4.3 mm means that it would fit anywhere on the centerline of the handle, regardless of orientation. Based on the strain and type of gauge chosen, this wrench design would read 1.14 mV/V.
