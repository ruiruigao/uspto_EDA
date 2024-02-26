# "Patent Pending": Exploratory analysis of the biotech patent landscape and patent processing times

Though not a cornerstone of all industries, patents are extremely **valuable to the biotechnology and pharmaceutical industries** in particular, given the astronomical costs of pharmaceutical research and development (R&D) and the low overall probability of clinical success (i.e., regulatory approval). In these industries, securing robust patent protection is a *key* mechanism for companies to recoup the massive upfront investment that drug development requires. In the U.S., the government entity that oversees the regulation and issuance of patents is the United States Patent and Trademark Office (USPTO). 

Using Python, I conducted an exploratory analysis of the USPTO's patent records, focusing specifically on biotech- and pharma-related patents. I investigated historical trends in the processing times of these patents, uncovering insights about how factors such as market shifts, patent law/policy changes, examiner "difficulty", and different technology categories are linked to patent processing times at the USPTO. These insights, summarized below, can be leveraged by life sciences companies to make patent-related business decisions, e.g., planning patent filing timelines as a part of wider business development activities like licensing and R&D strategy. 

## Technical overview

**Main packages:** pandas, numpy, matplotlib, seaborn.

**Other packages:** geopandas, geoplot.

A Jupyter notebook containing code and writeup for the analysis can be found [here](https://github.com/ruiruigao/uspto_EDA/blob/main/uspto_EDA.ipynb).

A slide deck that summarizes the main findings of my analysis can be found [here](https://github.com/ruiruigao/uspto_EDA/blob/main/USPTO_EDA_Python.pdf).

---
## Data

The main dataset used in this analysis contains **~270K** records of cancer research-related patents that were filed at the USPTO from **1976-2016**. To increase the richness and depth of the analysis, additional features from a separate USPTO dataset were pulled in by joining three additional tables to the main dataset on patent application numbers (unique IDs assigned to patent applications).

**USPTO datasets:**
* [Cancer Moonshot Patent Data](https://www.uspto.gov/ip-policy/economic-research/research-datasets/cancer-moonshot-patent-data) 
* Patent Examination Research Dataset -- [2022 release](https://www.uspto.gov/ip-policy/economic-research/research-datasets/patent-examination-research-dataset-public-pair)

**Additional datasets:**
* [2014 Cities and Towns of the United States](https://geodata.lib.utexas.edu/catalog/stanford-bx729wr3020)
* The analysis also produces two small CSV files containing processed data, which are downloadable via the following Google Drive links:
    - `random_sample_examiners.csv`: [download](https://drive.google.com/file/d/1mGrZPvld78x3kFc8xAAiZkvlWtutGvRy/view?usp=sharing)
    - `stratified_sample_examiners.csv`: [download](https://drive.google.com/file/d/1qI618WNMovnz7QraC8Ylp2RcH3GQABJc/view?usp=sharing)

**Note:** Downloaded datasets can be moved into the empty `data/` subfolder in this repo.

---
# Summary of Insights

Every patent begins as a _patent application_ filed at the USPTO. Patent applications need to be _granted_ by an examiner to become legally enforceable; this is a legal decision, and not all patent applications become granted (a sizeable portion are abandoned). For conciseness, the industry term "_pendency_" is used in this analysis to describe the processing time for a patent application to become a granted patent. 

<p align="center" width="100%">
  <img width="70%" src="results/prop-categories-by-year"><br>
</p>

**Trends in patent categories:** Overall, biotech and pharma patents fall into **9 broad technology categories**. The graph above captures the **emergence of technologies** such as **DNA-related patents** starting in the late 1990's, while technology related to **pharmaceutical drugs and chemistry**, which dominated biotech patent filings before 2000, shows a decreasing trend in more recent years. **Data science-related patents are beginning to emerge** and are expected to continue gaining ground as the industry continues to incorporate wider use of AI to accelerate drug discovery and development.

<p align="center" width="100%">
  <img width="70%" src="results/pendency-by-category-by-year"><br>
</p>

**Processing times can vary depending on technology:** Patents related to **radiation detectors** had the **shortest processing times** (median 30 months), while patents related to **living organisms and model systems** had the **longest processing times** (median 42 months). The difference is **statistically significant**. Patents related to more **abstract concepts and natural phenomena** such as **cells, DNA, diagnostics, data science, and living organisms** typically face **longer approval times**, reflecting that U.S. law restricts patents on certain types of inventions, such as those related to abstract concepts and non-manmade objects.

<p align="center" width="100%">
  <img width="70%" src="results/patex-pendency-vs-filing-year"><br>
</p>

**Pendency is affected by changes in patent law and market behavior:** A sharp spike in the number of filed applications can be observed in 1995 in the graph above (right), which could be attributed to **a change in patent term from 17 years from grant to 20 years from filing**. This change potentially **disadvantaged patents** that took longer than three years to be approved by the USPTO. The sharp rise in applications in 1995 suggests that companies **rushed to file** before the new law took affect. **Pendency (processing time) also spiked** in 1995, possibly due to the sudden **influx of applications.** However, the graphs also show a positive outcome. Despite **steadily increasing filings**, the USPTO has managed to **maintain consistent processing times** since 2005. This reflects their ability to **adapt to changing market demand**.



