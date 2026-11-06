# Clayton Hammen Tan

**Email:** [clt005@ucsd.edu](mailto:clt005@ucsd.edu)

**Section:** D11 – Cotality Property Intelligence

**Mentor:** Lawrence Vulis (Cotality)

---

**What is the most interesting topic covered in your domain this quarter?**

How small location errors in property data snowball in catastrophe models. A model's loss is roughly damage % (from things like flood depth) × rebuild cost, so if a building is drawn or placed in the wrong spot, the model reads the wrong hazard and every number after that is off. Pollack et al. (2025) found location errors drove most of the damage difference between two building inventories. Tracing buildings in North Park myself also showed me how much of this data is just people (or AI) outlining roofs from satellite photos, so errors like that are built in from the start.

**Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

Check how well building footprints line up with parcel (property) boundaries. For each parcel I'd find which footprints sit inside it, flag footprints that spill into a neighbour's lot or the street, and measure how far off they are. Then I'd test whether those offsets are big enough to change a building's flood zone or hazard cell. A related idea is comparing footprints from two years (e.g. 2021 vs 2025) and sorting the differences into real changes (demolished or new buildings) versus differences caused by the extraction method.

**What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

Right now we apply the same change to every building (e.g. shift all of them 5 m, or shrink all of them by 2 m) and look at the result. That shows what the error looks like, but not whether we could catch it. I'd instead plant errors of known size in a random sample of buildings, run our checks (overlaps, negative buffers, centroid tests), and measure how many of the planted errors get flagged and how many false alarms we get.

**What other techniques would you be interested in using in your project?**

- Spatial SQL in DuckDB (`ST_Intersects`, `ST_Distance`, `ST_Area`) to run the checks on whole zip codes or counties
- Matching footprints between two sources by overlap (intersection over union) to see which buildings agree
- Image segmentation models to extract footprints from satellite imagery ourselves
- Outlier detection (e.g. isolation forest) on shape features like area, vertex count and compactness to flag odd footprints
- Lidar height data to estimate building height or number of stories
