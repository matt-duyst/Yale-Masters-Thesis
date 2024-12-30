# Urban-Methane Transfers (2000 - 2018): A Convolutional Neural Network (CNN) Approach at Forecasting Historical XCH<sub>4</sub> Emissions through Urban Boundaries and Paddied Rice Extents Along China's YRD

## Overview
This repository presents the findings and methodologies from a comprehensive study integrating remote sensing and machine learning to understand atmospheric methane (CH<sub>4</sub>) emissions in China's Yangtze River Delta (YRD). The project bridges gaps in historical data using Convolutional Neural Networks (CNNs) to reconstruct emission distributions, providing insights into the interplay between urban expansion, rice cultivation, and CH<sub>4</sub> emissions.

## Table of Contents

- **Abstract**
- **Introduction**
- **Objectives and Hypotheses**
- **Methodology**
  - **Urban Expansion Analysis:** Utilizing GAIA data to map urban growth in the YRD.
  - **Rice Cultivation Extent Mapping:** Applying the PPPM algorithm for agricultural monitoring.
  - **Historical XCH<sub>4</sub> Emission Reconstruction:** Using DeepLabv3+ for spatiotemporal methane analysis.
- **Results**
  - **Urbanization Trends:** Quantifying urban growth across the YRD.
  - **Agricultural Land Dynamics:** Mapping and characterizing changes in paddied rice extents.
  - **Integrated Land-Use Analysis:** Assessing urban-agricultural tradeoffs and implications.
  - **XCH<sub>4</sub> Emission Patterns:** Spatial trends and historical reconstructions of CH<sub>4</sub> hotspots.
- **Discussion**
  - **Urban and Agricultural Dynamics:** Key drivers, trends, and implications of land-use changes.
  - **Methane Emission Insights:** Linking urbanization, agriculture, and atmospheric CH<sub>4</sub>.
  - **Limitations and Future Directions:** Methodological challenges and recommendations for advancement.
- **Conclusion**
- **Code and Data Availability**
- **References**

---

## Abstract

This study explores the intersection of remote sensing and machine learning to explore the dynamic interplay between urban expansion, agricultural transformations (i.e., rice cultivation), and atmospheric methane (CH<sub>4</sub>) emissions in China’s Yangtze River Delta (YRD). As a global epicenter of dense urbanization and agricultural productivity, the YRD provides a unique lens to investigate the effects of land-use changes on greenhouse gas (GHG) emissions. Using high-resolution Landsat imagery processed through the Global Artificial Impervious Area (GAIA) dataset and the Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm, this research provides precise mapping of urban boundaries and paddied rice extents. These results are validated against provincial agricultural statistics, ensuring a robust and reliable foundation for examining regional land-use impacts.

To address gaps in temporal CH<sub>4</sub> observations, this research reconstructs historical emission patterns (2000, 2010) by integrating land-use data spanning 2000–2018 with atmospheric CH<sub>4</sub> observations, available only post-2017 through the Sentinel-5 Precursor’s (S-5P) TROPOspheric Monitoring Instrument (TROPOMI). Building on the spatial correlations identified in 2018 among urban boundaries, rice cultivation shifts, and CH<sub>4</sub> emissions, this study developed a Convolutional Neural Network (CNN) employing the DeepLabv3+ architecture. Integrating advanced semantic segmentation techniques with spatiotemporal modeling, the CNN effectively reconstructs emission distributions for 2000 and 2010, yielding high-resolution historical CH<sub>4</sub> maps. 

By bridging temporal gaps in datasets, this study establishes an innovative machine learning framework that leverages spatial relationships between urban expansion and the geographic distribution of rice paddies to reconstruct and understand past CH<sub>4</sub> emissions. Through the integration of satellite imagery, deep learning architectures, and spatiotemporal modeling, this framework provides a regional viewpoint into how land-use transitions have influenced CH<sub>4</sub> emissions. These findings illuminate the YRD's evolving contribution to global CH<sub>4</sub> cycles over the past two decades (2000-2018), offering a foundation for advancing sustainable land-use planning and informing regional emissions mitigation strategies.

---

## Project Summary

This project explores land-use transformations in China’s YRD, a region characterized by its dense urban centers and vital agricultural systems. As one of China’s most critical agricultural landscapes, the YRD epitomizes the environmental tradeoffs arising from rapid urbanization and the persistence of agricultural practices. Encompassing the provinces of Anhui, Zhejiang, Jiangsu, and Shanghai, this study examines nearly two decades of change (2000, 2010, and 2018) and offers a comprehensive perspective on how urban expansion reshapes agricultural landscapes. By linking these transformations to CH<sub>4</sub> emissions, the study provides a unique lens into environmental implications of land-use change.

To capture these land-use shifts, the study employs supervised machine learning algorithms to analyze high-resolution Landsat imagery (Landsat 5, 7, and 8), enabling automated classification of urban boundaries and rice paddy extents. These 30-meter spatial resolution classifications provide a detailed view of land-use dynamics, uncovering intricate trends in the relationship between urban growth and agricultural persistence. While prior studies have documented the interdependencies of urbanization and agriculture along the YRD, this research expands the scope by integrating an atmospheric perspective – mapping spatiotemporal distributions of CH<sub>4</sub> emissions to contextualize land-use changes within their broader environmental impacts.

To quantify the spatiotemporal distribution of CH<sub>4</sub> concentrations, this study utilizes column-averaged dry air mixing ratio of methane (XCH<sub>4</sub>) data from the TROPOspheric Monitoring Instrument (TROPOMI) onboard the Sentinel-5 Precursor (S5-P) satellite. With a spatial resolution of 7 km², the TROPOMI dataset is well-suited for detecting CH<sub>4</sub> sources and sinks across heterogeneous landscapes (Zhang et al., 2023), offering a regional perspective on emission patterns in the YRD. However, its temporal coverage is constrained by the late-2017 launch of S-5P, restricting CH<sub>4</sub> data availability to 2018 and necessitating innovative approaches to bridge historical data gaps.

### Drivers of Atmospheric CH<sub>4</sub>: Rice Paddies and NGVs

Agriculture and urbanization are pivotal drivers of atmospheric CH<sub>4</sub> emissions, with biogenic and anthropogenic sources intricately interwoven within the YRD's complex landscape. Among these, rice paddies persist as significant contributors due to water-intensive cultivation methods such as flooding, which fosters anaerobic conditions conducive to CH<sub>4</sub> production (G. Zhang et al., 2020). This positions rice as a unique paradox: both an economic cornerstone of China’s agricultural exports and a consistent source of CH<sub>4</sub> emissions.

Compounding these agricultural emissions is an emerging urban-linked contributor: retrofitted Natural Gas Vehicles (NGVs). Over the past two decades, NGV production in China has surged from 6,000 vehicles in 2000 to 6 million by 2017 (Da Pan et al., 2020). Although NGVs pose a cleaner alternative to traditional fossil fuels, retrofitted vehicles frequently suffer from faulty tailpipes, releasing an estimated 196 kg of CH<sub>4</sub> per vehicle annually (Hu et al., 2018). This study leverages NGVs as an urbanization proxy, analyzing their fleet-wide contributions to atmospheric CH<sub>4</sub> emissions.

Together, these systems illustrate the convergence of agricultural persistence and urban expansion in shaping CH<sub>4</sub> dynamics. By examining the interplay between rice paddies and urban growth – including the rising demand for NGVs – the study underscores the dual pressures of sustaining agricultural productivity while managing emissions amid rapid urbanization. This interdisciplinary approach provides a nuanced understanding of regional spatiotemporal CH<sub>4</sub> dynamics, linking localized emission sources to broader environmental challenges. By framing these findings within the context of land-use transitions, the study contributes to global emission monitoring efforts and supports the development of targeted mitigation strategies.

### Spatial Analysis of XCH<sub>4</sub> Emissions: Insights from TROPOMI Observations

CH<sub>4</sub> is a potent GHG with a global warming potential 25–30 times greater than carbon dioxide (CO₂) over a 100-year period (Y. Zhang et al., 2011). To elucidate the spatial distribution of column-averaged CH<sub>4</sub> concentrations, this study employs advanced statistical techniques. Using the Getis-Ord Gi* statistic to identify statistically significant clusters of high or low XCH<sub>4</sub> concentrations, and Global Moran’s I to quantify spatial autocorrelation, this analysis uncovers the relationships between emission values and their geographic distributions. These methods help distinguish meaningful emission patterns from randomness, providing a spatially explicit understanding of CH<sub>4</sub> emissions by revealing critical hotspots and clusters that shape the regional emission landscape.

With the late-2017 launch of the S-5P satellite, XCH<sub>4</sub> observations are temporally constrained to 2018. To alleviate this constraint, the study integrates XCH<sub>4</sub> visualizations with previously mapped urban boundaries and rice paddy extents, creating a consistent provincial-scale framework for analysis. This spatial overlay connects land-use changes to atmospheric CH<sub>4</sub> concentrations, providing an integrative view of urban growth and environmental processes interacting along the YRD. By integrating TROPOMI-derived XCH<sub>4</sub> data with detailed land-use classifications, this study provides a nuanced perspective on the YRD’s contribution to regional and global CH<sub>4</sub> cycles. The findings highlight the power of combining remote sensing with advanced statistical analyses to uncover intricate emission patterns and their broader environmental implications. This approach not only deepens our understanding of CH<sub>4</sub> dynamics but also establishes a scalable framework for exploring the interconnected relationships between land-use and atmospheric processes across complex and diverse landscapes.

### Reconstructing CH<sub>4</sub> Emissions: Deep Learning with Encoder-Decoder CNNs

To address temporal gaps in satellite-derived CH<sub>4</sub> observations, this study employs a Convolutional Neural Network (CNN) built on the DeepLabv3+ architecture, a cutting-edge model designed for semantic segmentation tasks. The encoder-decoder architecture of the CNN is particularly well-suited to this study’s objectives, as it integrates multi-scale contextual information from input data while recovering fine-grained details through skip connections in the decoder module. The encoder module extracts multi-scale features, capturing both broad contextual information and localized details from the inputs. Meanwhile, the decoder module refines segmentation maps to accurately delineate emission boundaries. Key innovations,  like atrous convolution with spatial pyramid pooling (ASPP) to enhance the model’s sensitivity to spatial variations and overall segmenting of complex spatial patterns, and skip connections to recover high-resolution details like object boundaries, bolster the model’s robustness for analyzing heterogeneous land-use data (Long et al., 2015). 

The model is trained and validated using a dataset combining 2018 Landsat-derived urban and rice paddy maps with CH<sub>4</sub> data captured by the S-5P satellite at 7 km² spatial resolution. By learning the spatial relationships between urban growth, rice cultivation shifts, and CH<sub>4</sub> emissions, the CNN extrapolates patterns to predict historical CH<sub>4</sub> distributions for 2000 and 2010, addressing the absence of direct CH<sub>4</sub> data for these years. 

Essentially, the model generates high-resolution segmentation maps of historical CH<sub>4</sub> concentrations by reconstructing CH<sub>4</sub> emission trajectories over time through the spatial relationships between urban boundaries and rice paddy distributions. This advancement provides insights into the spatiotemporal dynamics of CH<sub>4</sub> emissions along the YRD and establishes a scalable framework for overcoming data limitations in environmental monitoring. By integrating satellite observations with machine learning, the study underscores the transformative potential of emerging technologies in shaping earth monitoring and climate modeling.

### Novelty of Study

This study bridges the traditionally separate analyses of urbanization and agriculture by linking urban expansion with rice paddy distributions to estimate atmospheric CH<sub>4</sub> emissions across the YRD. This integrated framework offers a perspective on the combined impacts of these opposing land-use dynamics, addressing a gap in understanding the spatiotemporal drivers of GHG emissions. To the best of our knowledge, this represents one of the first large-scale efforts to quantify the collective influence of urbanization and agriculture on CH<sub>4</sub> cycles, leveraging the synergy of remote sensing and machine learning to unravel their interdependencies.

At the core of this innovation lies the implementation of an encoder-decoder CNN architecture to reconstruct historical XCH<sub>4</sub> emissions for 2000 and 2010. Using urban boundaries and rice paddy extents as inputs, the model bridges temporal gaps in satellite data by predicting CH<sub>4</sub> distributions for years without direct observations. This approach underscores the versatility of machine learning in environmental monitoring, extending its applicability to address longstanding challenges in historical emissions data.

The study also exemplifies the potential of data fusion techniques by integrating diverse datasets – high-resolution Landsat imagery and S-5P TROPOMI observations – through rigorous preprocessing and post-processing workflows. By synthesizing spatial, temporal, and atmospheric dimensions, this research offers a new lens for examining how land-use transitions influence CH<sub>4</sub> emissions. Beyond its technical advancements, the study highlights the power of interdisciplinary approaches in tackling complex environmental challenges, providing a scalable framework for future innovations in land-use and emissions research.

### Related-Works and Contributions

This study builds upon two fundamental methodologies: the Global Artificial Impervious Area (GAIA) framework (Gong et al., 2019) and the Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm (Zhu et al., 2021). These seminal works provide the tools for accurately delineating urban extents and isolating rice paddy fields, setting the stage for this research’s integrated analysis of land-use transitions and CH<sub>4</sub> emissions.

The GAIA framework serves as a cornerstone for urban boundary mapping, precisely detecting impervious surfaces in spatially complex and rapidly urbanizing regions. Leveraging spectral indices and machine learning techniques, GAIA processes high-resolution satellite imagery to delineate urban boundaries with annual updates. This potential is instrumental in assessing nuanced growth patterns, like the densification of city centers or the expansion of peri-urban areas, delivering an evolving demonstration of urban transformations along the YRD.

Complementing this is the PPPM algorithm, which specializes in refining rice paddy mapping by incorporating phenological cycles, distinct seasonal variations associated with transplanting and harvesting, and pixel-based analyses. Utilizing vegetation indices like NDVI, LSWI, and EVI, the PPPM algorithm distinguishes rice paddies from other water-intensive crops, like duckweed, even in regions with overlapping land uses. This granular approach enhances the understanding of agricultural persistence, enabling the study to capture alterations in cropping systems and evaluate the resilience of rice cultivation amid urban encroachment.

By integrating GAIA’s urban mapping precision with PPPM’s detailed agricultural classifications, this study uncovers the spatiotemporal interplay between urban expansion and agricultural persistence, directly linking these dynamics to CH<sub>4</sub> emissions. The findings establish a robust framework for assessing the environmental consequences of land-use transitions, offering insights into how such changes drive regional CH<sub>4</sub> emissions. This research demonstrates the efficacy of combining advanced remote sensing methodologies with machine learning applications, underscoring their potential to address complex challenges in environmental monitoring and inform sustainable land-use strategies.

### Auxiliary Data

To complement its remote sensing and machine learning methodologies, this study incorporates auxiliary datasets that provide historical, demographic, and environmental context for CH<sub>4</sub> emissions. These supplementary resources allow for the analysis of regional drivers of CH<sub>4</sub> emissions, bolstering the study’s spatiotemporal framework.

Historical CH<sub>4</sub> emission inventories, segmented into contributions from rice paddies and urban sources, are sourced from the Global Methane Initiative (GMI), an Environmental Protection Agency (EPA)-led project. Spanning 1990–2050 and expressed in million metric tons of CO₂-equivalent (MMTCO₂e), these inventories establish a long-term baseline for evaluating emissions trends and shifts over time.

Urban CH<sub>4</sub> emissions are analyzed through demographic and energy consumption metrics obtained from the National Bureau of Statistics of China. Population statistics (per 10,000 persons) and natural gas consumption data provide key indicators for urban emissions, while rice paddy-related emissions are contextualized using sown area statistics (per 1,000 hectares). These datasets segment emissions across urban and agricultural domains, facilitating analysis of their respective contributions.

Annual provincial-level temperature data, acquired from the Climate Knowledge Portal (World Bank), further inform the study by addressing seasonal patterns in paddied rice cultivation. This climatological data provides insights into the environmental variables influencing emissions, such as flooding periods that drive anaerobic conditions in rice paddies.

By integrating publicly available datasets, this study establishes a comprehensive analytical framework that bridges historical, environmental, and land-use dimensions. This holistic approach enhances the accuracy of CH<sub>4</sub> modeling, providing a more contextually grounded perspective of the ebb-and-flow of land-use transitions and their impact on GHG emissions.

### Intellectual Merits and Broader Implications

This study operates at the intersection of environmental monitoring and predictive modeling, offering a novel spatiotemporal framework to examine the interconnections between urban expansion, rice paddy shifts, and atmospheric CH<sub>4</sub> concentrations within the YRD. By quantifying Urban-Methane transfers across China’s most densely populated and agriculturally significant provinces, this research deepens understanding of regional CH<sub>4</sub> emissions and their cascading environmental impacts. Through the integration of a CNN to address temporal data gaps, the study advances knowledge of historical CH<sub>4</sub> dynamics and informs strategies for sustainable land management, emissions mitigation, and climate resilience at both regional and global scales.

---

## Background

![Study Area - Yangtze River Delta (YRD)](/assets/Case_Study.png)

**<p align="center">Figure 1: Study Area - Yangtze River Delta (YRD)</p>**  
This map delineates the geographical scope of the study, highlighting the YRD’s provincial regions: Anhui, Zhejiang, Jiangsu, and Shanghai. The provincial boundaries, outlined in red, emphasize the region's spatial heterogeneity and provide a clear perspective on its scale in relation to urbanization and agricultural productivity. The inset situates the YRD within the broader context of China, underscoring its regional and global significance.

### Population Growth and China’s Land-Use Transformations

China, home to an estimated 1.44 billion people, constitutes approximately 18.47% of the global population (Worldometer, 2021), making it the world’s most populous nation. Rapid urbanization underscores China’s economic and social development, often marked by the conversion of agricultural land to urban areas. This study investigates these land-use transformations by analyzing the interplay between urban expansion and rice paddy cultivation, focusing on three temporal milestones: 2000, 2010, and 2018. Assessing spatiotemporal dynamics across this nexus, the research sheds light on how population growth and land-use changes influence CH<sub>4</sub> emissions and regional environmental monitoring.

### From Rivers to Riches: An Anthology of the Economic and Environmental Legacies of the YRD

The YRD owes its economic dominance to its unique environmental and geographic attributes. Centered around the Yangtze River – the largest river in China and the third largest globally, spanning 1.8 million km² (Zhu et al., 2020) – the region has historically utilized its vast river networks to foster trade, agriculture, and industrial growth. Encompassing 27 cities over an area of 225,065 km² and housing 163 million people (EY Greater China, 2020), the YRD generates nearly 24% of China’s GDP, representing a fusion of natural resource abundance and economic ingenuity.

Historically, YRD cities capitalized on their riverine infrastructure to establish specialized industries. Yangzhou dominated the salt trade; Wuxi contributed one-fourth of China’s rice production; Suzhou and Hangzhou thrived as textile hubs; and Ningbo and Yin served as pivotal trading ports (Gu et al., 2011). These industries leveraged the region’s interconnected waterways for seamless transportation and market integration. This synergistic relationship between natural resources and industry laid the foundation for the YRD’s evolution into an economic powerhouse.

### Shanghai: The Engine of Global Urbanization and Economic Evolution

Shanghai’s ascension to a global hub epitomizes the YRD’s urban and economic transformation. Strategically located at the Yangtze River estuary, Shanghai’s rise was catalyzed by key treaties, including the 1842 Nanjing Treaty and the 1843 Treaty of Humen, which opened its ports to international trade (Gu et al., 2011). These agreements spurred migration, foreign investment, and the establishment of international factories, cementing Shanghai’s role as China’s largest export hub by the late 19th century. The city’s historical trajectory not only highlights its role in shaping the urban and economic landscapes of the YRD, but also underscores its enduring influence in driving global trade and urbanization trends.

### The YRD: Agricultural Powerhouse and Biogenic CH<sub>4</sub> Contributor

The YRD’s marine monsoon subtropical climate, defined by hot, humid summers and cool, dry winters, supports remarkable agricultural productivity. Contributing 40% of China’s total agricultural output, the region owes much of its success to rice cultivation – which accounts for 70% of this yield (Li et al., 2021). This productivity comes with significant environmental tradeoffs: flooded rice paddy fields are among the largest contributors to atmospheric CH<sub>4</sub> emissions (Y. Zhang et al., 2011). 

Rising global temperatures are projected to amplify rice fertilization rates, boosting yields while exacerbating CH<sub>4</sub> emissions through heightened microbial activity in flooded fields (G. Zhang et al., 2020). This dual challenge positions the YRD as both a unique case study in balancing agricultural productivity with climate mitigation and a global exemplar of the complexities inherent in achieving sustainable agricultural practices in the face of escalating environmental pressures.

### Rice Cultivation: Cornerstone of Agriculture, Catalyst of Emissions

Rice paddies are integral to China’s agricultural landscape, spanning nearly 30 million hectares (Jiang et al., 2018) and accounting for a substantial portion of global CH<sub>4</sub> emissions. As one of the world’s largest biogenic sources of CH<sub>4</sub>, rice cultivation contributes approximately 25–36% of global agricultural CH<sub>4</sub> emissions (G. Zhang et al., 2020). These emissions stem primarily from the anaerobic decomposition of organic matter in flooded fields – a technique critical to rice production but inherently conducive to CH<sub>4</sub> release. This positions rice paddies at the intersection of two pressing challenges: sustaining agricultural yields to meet global food export demands while mitigating their considerable environmental impact. 

### From CO₂ Reduction to CH<sub>4</sub> Emission: The NGV Paradox in Urban-Methane Dynamics

China’s nationwide adoption of Natural Gas Vehicles (NGVs) represents a key component of its strategy to minimize GHG emissions and transition toward sustainable transportation. NGVs emit significantly less CO₂ than traditional fossil fuel vehicles, making them a cleaner alternative; however, retrofitting challenges (particularly faulty tailpipes) have led to unintended consequences, disproportionately contributing to urban CH<sub>4</sub> emissions.

As the world’s largest manufacturer of NGVs, China faces a duality of maximizing the environmental benefits of NGVs while addressing the retrofitting defects exacerbating CH<sub>4</sub> emissions. This study investigates urban CH<sub>4</sub> concentrations in the YRD, which are likely amplified by the rapid increase in NGV retrofitting. By analyzing XCH<sub>4</sub> as an indicator, this research offers a perspective into the atmospheric CH<sub>4</sub> footprint of urban growth and the transition to NGVs, highlighting the necessity for targeted mitigation strategies in densely populated urban regions.

---

## Objectives and Hypotheses

### Objectives

This study aims to address historical knowledge gaps in the spatiotemporal dynamics of urbanization, agricultural practices, and CH<sub>4</sub> emissions along the YRD. Its objectives are as follows:

- **Mapping Urban Growth Dynamics:** Quantify and characterize the spatiotemporal evolution of urban boundaries across the YRD over two decades (2000, 2010, 2018) by leveraging Landsat imagery composites and Global Artificial Impervious Area (GAIA) data. This analysis provides insight into the patterns and drivers of rapid urban growth in one of the world’s most densely populated regions.
- **Mapping Rice Cultivation Extents:** Assess changes in rice paddy extents across the YRD during the same time period (2000, 2010, 2018) using the Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm applied to Landsat imagery. Understanding these shifts is crucial for contextualizing the agricultural contributions to CH<sub>4</sub> emissions.
- **Spatial Analysis of CH<sub>4</sub> Hotspots:** Identify statistically significant clusters of atmospheric CH<sub>4</sub> concentrations for 2018 through spatial autocorrelation methods, including hotspot detection. These clusters reveal key areas where land-use interactions and emissions intensify, offering a spatially explicit perspective on regional CH<sub>4</sub> dynamics.
- **Reconstructing Historical CH<sub>4</sub> Emissions:** Develop a DeepLabv3+ Convolutional Neural Network (CNN) to reconstruct historical CH<sub>4</sub> emission distributions (2000, 2010) based on urban boundaries and paddied rice extents recorded during those years. This modeling approach bridges temporal data gaps, enabling a historical understanding of CH<sub>4</sub> dynamics.

### Hypotheses

The study proposes two hypotheses to test the interplay between urbanization, agriculture, and atmospheric CH<sub>4</sub> emissions:

#### Hypothesis 1  
CH<sub>4</sub> emissions from rice paddies are expected to be lower than previously recorded levels. This hypothesis posits that continued urban expansion has led to a reduction in agricultural land, including rice fields, resulting in decreased biogenic CH<sub>4</sub> emissions. Trends in atmospheric CH<sub>4</sub> concentrations correlate with the proportion of agricultural land converted to urban development, underscoring the importance of accurately characterizing urbanization rates along the YRD.

#### Hypothesis 2  
Urban-related CH<sub>4</sub> emissions are expected to surpass historical levels, driven by continued population growth, exponential NGV adoption, and persistent infrastructure deficiencies (retrofitting). Faulty retrofitted NGVs are anticipated to emerge as a dominant urban CH<sub>4</sub> source, reflecting the environmental trade-offs of rapid urbanization and increasing transportation and energy demands in the region.

---

## Methodology

This study employs a multi-method approach, integrating remote sensing techniques, supervised classification algorithms, and deep learning methods to address its core objectives:

- **Urban Growth Analysis:** Urban boundaries are delineated for 2000, 2010, and 2018 using high-resolution Landsat imagery combined with the GAIA dataset. This framework detects impervious surface features, such as roads, rooftops, and sidewalks, which serve as key indicators of human settlement and urban expansion.
- **Rice Cultivation Mapping:**  PPPM algorithm, applied to Landsat imagery, identifies rice paddy distributions. The method incorporates phenological signatures, such as transplanting and harvesting cycles, along with conditional thresholds like elevation and cropping calendars, to accurately isolate rice fields.
- **Forecasting Historical CH<sub>4</sub> Emissions:** A CNN built on DeepLabv3+ architecture estimates historical CH<sub>4</sub> emissions for 2000 and 2010. The model leverages spatial relationships observed in 2018 between urban boundaries, rice paddy extents, and XCH<sub>4</sub> data to address gaps in emissions records and facilitate a retrospective analysis of CH<sub>4</sub> dynamics.

### Decoding Urban Growth: Spatiotemporal Trends in the YRD (2000, 2010, 2018)

Urbanization is a defining feature of land-use transformation in the YRD, a landscape characterized by rapid population growth and expanding urban landscapes. Projections estimate an additional 2.5 billion individuals will populate urban areas globally in the coming decades (Seto et al., 2011), driving outward urban land expansion at the cost of rural acreage. This process has far-reaching environmental consequences, including soil degradation (Yan et al., 2015) and air pollution (Bereitschaft and Debbage, 2013; Zhu et al., 2020). Understanding the spatiotemporal dynamics of urban development in the YRD requires high-resolution datasets that balance spatial detail (30 meters) with temporal granularity (annual and decadal trends) (Ban et al., 2015; Chen et al., 2016).

#### The Complexity of Monitoring Urban Transformations
Previous large-scale monitoring efforts often struggled to capture both spatial and temporal dynamics at high-resolution. Studies relying on coarse spatial datasets, such as the 500-meter Moderate Resolution Imaging Spectroradiometer (MODIS) product (Friedl et al., 2010), provide insufficient detail for urban growth analysis. Similarly, temporal inconsistencies arise in global urban products like the five-year intervals of Liu et al. (2017) or the 10-year GlobeLand30 classifications (Chen et al., 2016). These limitations hinder accurate assessments of urban land conversion rates and extents, particularly in rapidly evolving regions like the YRD.

#### GAIA: A High-Resolution Approach to Urban Expansion Analysis
The GAIA dataset, introduced by Gong et al. (2019), addresses these challenges by leveraging the full 30-meter resolution Landsat archive (1985–2018) on the Google Earth Engine (GEE) platform. The GAIA dataset automates the mapping of artificial impervious areas – pavements, roads, sidewalks, roofs – as indicators of urban boundaries. By bypassing the need for large training datasets, GAIA offers a cost-effective alternative for tracking urban expansion. Its reliance on spectral indices, such as the Normalized Difference Vegetation Index (NDVI), the Modified Normalized Difference Water Index (MNDWI), and shortwave infrared (SWIR) bands, enables robust classification of land cover changes over time.

Algorithms within the GAIA framework mask vegetated regions, water bodies, and bare lands to isolate artificial impervious surfaces. These methods identify urban boundaries with annual updates, leveraging Landsat Thematic Mapper (TM), Enhanced Thematic Mapper Plus (ETM+), and Operational Land Imager (OLI) imagery. For early years (pre-2000), when high-resolution satellite imagery was less available, urban cores were generalized using locally homogeneous pixels with impervious area coverage exceeding 50% (Gong et al., 2019). This approach ensures temporal consistency while maintaining spatial precision.

#### Advantages of GAIA in Urban Mapping

The GAIA dataset enables comprehensive mapping of the YRD’s urban growth by addressing key limitations of earlier approaches. Its advantages include:

- **Temporal Consistency:** Providing annual urban boundary updates over 34 years (1985–2018), GAIA captures both short-term urban fluctuations and long-term patterns necessary for cataloging rapid urbanization dynamics.
- **Spatial Precision:** Leveraging 30-meter resolution imagery, GAIA avoids the coarse granularity of earlier products, enabling detailed representations of urban expansion patterns critical for identifying urban-rural transitions.
- **Streamlined Automation:** Utilizing GEE and spectral indices, GAIA streamlines the traditionally resource-intensive process of manual training sample collection, enabling scalable analysis for large-scale urban growth studies (Yang et al., 2017).

#### Limitations and Considerations

While GAIA’s methodology marks a significant advance in urban mapping, certain limitations persist:

- **Early-Year Data Availability:** Limited availability of cloud-free Landsat imagery during earlier years (e.g., 1985) may reduce classification accuracy for these time points.
- **Spectral Mixing in Urban Areas:** Mixed spectral signatures within 30-meter pixels can complicate classification in spatially complex urban settings (Wang and Li, 2019).
- **Urban Permanence Assumption:** GAIA assumes permanence in urban classification – once an area is classified as urban, it remains so. This disregards processes like afforestation or land-use reversion from urban to rural.

Despite these limitations, GAIA proves well-suited for charting urban expansion rates along the YRD. Unlike arid or semi-arid landscapes, where spectral inconsistencies complicate impervious surface classification, the YRD’s humid climate and distinct urban features minimizes these challenges. GAIA provides a robust foundation, delivering high-resolution insights into the spatiotemporal dynamics of urbanization in one of the world’s fastest-developing regions.

#### Open Access and Reproducibility

The GAIA dataset is openly available at [http://data.ess.tsinghua.edu.cn](http://data.ess.tsinghua.edu.cn), ensuring transparency and reproducibility for future research.

### Mapping Rice Cultivation Dynamics Using the PPPM Algorithm (2000, 2010, 2018)

China’s agricultural economy is deeply rooted in its rice cultivation system, characterized by two dominant mixed-cropping practices: single-cropping rice (SCR) and double-cropping rice (DCR). Together, these practices represent the backbone of the nation’s agricultural exports. Capturing the spatial dynamics of rice paddies has historically relied on advanced remote sensing technologies, with phenological signatures (like transplanting and heading periods) indicating rice distributions. This study employs Zhu et al.’s (2021) PPPM algorithm to map rice paddy extents across the YRD over two decades (2000–2018). By combining SCR and DCR paddies, the algorithm integrates phenological signals extracted from Landsat TM, ETM+, and OLI imagery to quantify total rice acreage.

#### Optimizing Remote Sensing Techniques for Rice Mapping: Challenges and Innovations
Accurate mapping of rice paddies requires balancing high temporal frequency with detailed spatial resolution datasets. While MODIS data has been widely utilized for its frequent temporal coverage (Boschetti et al., 2014), its coarse 500-meter resolution restricts its capacity to capture the intricate spatial heterogeneity of rice systems. In contrast, Landsat’s 30-meter spatial resolution provides the granularity required to analyze rice paddy distributions, albeit at the cost of reduced temporal coverage (Dao et al., 2015; Xu et al., 2018).

Recent advancements in remote sensing, such as Sentinel-2A MSI data, combine high spatial and spectral resolution, offering superior crop classification capabilities (Löw et al., 2015; Marshall et al., 2015). However, Sentinel-2A’s temporal availability does not align with this study’s 30-year historical scope. Similarly, synthetic aperture radar (SAR) data provides the advantage of weather-independent imaging (Du et al., 2016; Zhang et al., 2018), but high-resolution SAR datasets for historical mapping of rice paddies are unavailable for this study region. 

The PPPM algorithm addresses these challenges by leveraging Landsat imagery enriched with phenological characteristics to deliver both spatial precision and temporal continuity. This combination is particularly effective for identifying the dynamic rice systems embedded within the YRD’s spatially heterogeneous agricultural landscapes (Dou et al., 2020; Hao et al., 2018; Li et al., 2021).

#### The PPPM Algorithm: Precision Mapping of Rice Cultivation
The PPPM algorithm employs a specialized approach to isolate rice paddies by detecting flooding signals unique to rice during transplanting phases. Three vegetation indices – Enhanced Vegetation Index (EVI), Normalized Difference Vegetation Index (NDVI), and Land Surface Water Index (LSWI) – are utilized to identify areas with high water content and active vegetation growth (Xiao et al., 2006). When paired with Landsat imagery, these indices enable accurate identification of rice paddies, delivering both precision and reliability in mapping agricultural landscapes with diverse cropping systems. To reduce the risk of misclassification with other water-intensive crops, the algorithm integrates phenological features that differentiate rice paddies based on the unique biophysical characteristics of rice cultivation cycles. This approach ensures accuracy even in regions characterized by complex, mixed cropping systems (Liu et al., 2020).

#### Agricultural Data Integration and Validation
Phenological data was sourced from the Ministry of Agriculture of China, providing agriculturally verified thresholds to define optimal observation windows for flooding and vegetative phases of rice systems. By aligning satellite observations with these timeframes, the PPPM algorithm ensures precise temporal targeting, enhancing the accuracy of rice paddy mapping. To validate the algorithm’s outputs, rice paddy extents derived from the PPPM algorithm were compared against historical agricultural statistics from the National Bureau of Statistics of China. These provincial-scale datasets (1999–2019) offer a reliable baseline for assessing algorithm performance, ensuring alignment with reported paddied rice acreage across Anhui, Zhejiang, Jiangsu, and Shanghai. This validation process underscores the consistency and reliability of the algorithm in capturing regional agricultural dynamics.

#### Limitations and Considerations for Phenological-Based Rice Mapping

While the PPPM algorithm advances rice mapping capabilities, certain limitations remain:

- **Flooding Signal Ambiguity:** Aquatic crops like duckweed exhibit flooding signals similar to those of rice during transplant phases, occasionally resulting in misclassifications (Zhu et al., 2021). Although incorporating additional phenological features mitigates this risk, minor overlaps persist in areas with complex cropping systems.
- **Phenological Data Dependency:** The algorithm’s performance heavily relies on the accuracy of phenological data, which varies across heterogeneous regions with overlapping cropping systems and mixed cultivation cycles. Inconsistencies in data quality or availability may influence mapping precision.

Despite these limitations, the PPPM algorithm provides a comprehensive perspective for understanding rice cultivation dynamics, proving particularly valuable in regions like the YRD, where land-use transitions intertwine agricultural and urban systems.

### Reconstructing Historical XCH<sub>4</sub> Emissions: DeepLabv3+ and the Encoder-Decoder Architecture of CNNs

#### Machine Learning Applications in Remote Sensing
The integration of machine learning techniques, particularly Convolutional Neural Networks (CNNs), with remotely sensed imagery has revolutionized environmental monitoring, enabling scalable, automated, and high-resolution analyses. CNNs are widely recognized for their ability to learn complex spatial and spectral patterns in labeled datasets (Krizhevsky et al., 2012; LeCun et al., 1989), with applications spanning land-use classification, object detection, and environmental forecasting (Cheng et al., 2016; Mahdianpari et al., 2018).

This study leverages the DeepLabv3+ architecture, a state-of-the-art semantic segmentation model tailored for extracting spatially explicit features from high-resolution imagery. Designed to enhance segmentation accuracy, the model employs an encoder-decoder framework, which captures multi-scale contextual information and reconstructs fine-grained spatial details. By training the model on 2018 data, where urban extents, rice paddy distributions, and XCH<sub>4</sub> emissions are simultaneously available, the model bridges temporal data gaps to reconstruct historical CH<sub>4</sub> emission patterns for 2000 and 2010. This approach facilitates a retrospective analysis, revealing how land-use transitions have influenced atmospheric CH<sub>4</sub> emissions over time.

![DeepLabv3+ Architecture for XCH<sub>4</sub> Emission Forecasting](/assets/DeepLabv3+.png)

**<p align="center">Figure 2: DeepLabv3+ Architecture for Historical XCH<sub>4</sub> Emission Forecasting</p>**
This figure depicts the encoder-decoder architecture of the DeepLabv3+ model applied to forecast historical XCH<sub>4</sub> emission boundaries. The model integrates urban boundaries, rice paddy extents, and a satellite basemap (YRD) as inputs. The encoder employs Atrous Spatial Pyramid Pooling (ASPP) to extract multi-scale contextual information using parallel convolutional layers with varying dilation rates. The decoder reconstructs high-resolution segmentation maps by fusing low-level and high-level features through skip connections, improving the output spatial resolution and granularity. The final segmentation map predicts XCH<sub>4</sub> emission boundaries, reflecting spatial patterns derived from urban and rice paddy distributions. This architecture exemplifies the model’s capability to learn complex spatial relationships and bridge temporal gaps in satellite data for enhanced environmental monitoring.

#### Theoretical Basis for Spatial Image Reconstruction
The encoder-decoder architecture of CNNs is grounded in principles of spatial dependency, famously articulated in Tobler’s First Law of Geography: “Everything is related to everything else, but near things are more related than distant things.” This inherent spatial interdependence allows CNNs to reconstruct missing or incomplete image patches by utilizing contextual information from neighboring or surrounding pixels, making them particularly effective for addressing data availability gaps (He et al., 2022). In this study, the encoder processes Landsat imagery (30m resolution) representing urban and rice paddy extents for 2000, 2010, and 2018, alongside S-5P imagery (7 km² resolution) containing XCH<sub>4</sub> data for 2018. The decoder reconstructs masked image regions, learning latent spatial patterns to predict historical XCH<sub>4</sub> emission boundaries. The scale and translation invariance of CNNs ensure seamless integration of these datasets despite their differing resolutions, enabling precise cross-temporal reconstructions of CH<sub>4</sub> dynamics along the YRD.

### DeepLabv3+ Architecture: Implementation and Evaluation

DeepLabv3+ was chosen for its robust capability in generating high-resolution segmentation maps by integrating multi-scale contextual features with fine-grained spatial details. The architecture implementation involves the following components:

- **Encoder Module:** The encoder leverages ResNet50 as its backbone network, pre-trained on ImageNet, to extract robust feature representations. Atrous convolutions with varying dilation rates in the ASPP module capture multi-scale contextual features, allowing the model to effectively discern spatial relationships across different resolutions. This multi-scale capability is crucial for handling the heterogeneity of urban and agricultural landscapes within the YRD.
- **Decoder Module with Skip Connections:** The decoder refines segmentation maps by combining high-level features from the ASPP module with low-level features from earlier encoder layers through skip connections. These connections restore spatial granularity by reintroducing fine details lost during feature extraction, improving the delineation of object boundaries and enhancing segmentation accuracy. This architecture ensures that the model captures both macro-level patterns and micro-level intricacies in emission distributions.
- **Output:** The final segmentation map assigns a class label to each pixel, reconstructing historical CH<sub>4</sub> emission boundaries with high spatial resolution. Integrating spatial relationships derived from urban boundaries, rice paddy extents, and a satellite basemap, the model captures how land-use transitions in the YRD have influenced CH<sub>4</sub> emissions over time.

### Training Process

The model is trained using 5,000 randomly cropped images from 2018 data spanning Anhui, Zhejiang, and Shanghai. Each crop includes four input layers: urban boundaries, rice paddy extents, XCH<sub>4</sub> emission boundaries, and a satellite basemap. This cropping approach ensures spatial diversity and incorporates a wide range of land-use patterns to improve the model’s robustness.

### Testing Process

The testing set consists of 1,000 randomly cropped images from Jiangsu, a region excluded from the training data to evaluate the model's generalization capability. This ensures the model can accurately predict XCH<sub>4</sub> emission patterns in unseen spatial contexts. The testing process assesses the model's ability to reconstruct emission boundaries while maintaining consistency across heterogeneous landscapes and land-use types.

### Evaluation and Performance

Following training, the model undergoes rigorous performance evaluation to validate its reliability in reconstructing historical CH<sub>4</sub> emissions. Metrics such as Mean Squared Error (MSE) measure the accuracy of predicted XCH<sub>4</sub> boundaries against ground truth data, while additional qualitative assessments examine the spatial coherence of emission reconstructions. This evaluation confirms the model’s ability to capture spatiotemporal dynamics, bridge temporal data gaps, and deliver actionable insights into CH<sub>4</sub> emission trajectories across the YRD.

### Forecasting Historical XCH<sub>4</sub> Emissions with DeepLabv3+

The DeepLabv3+ model addresses a critical challenge: predicting historical CH<sub>4</sub> emissions (2000, 2010) in the absence of S-5P data. By training on 2018 data, where XCH<sub>4</sub> boundaries align with urban and rice paddy extents, the model extrapolates these learned relationships to earlier years. Historical urban boundaries and rice paddy extents are utilized as spatial proxies, enabling the DeepLabv3+ model to reconstruct high-resolution XCH<sub>4</sub> emission maps for 2000 and 2010.

### Advantages of DeepLabv3+ for Predicting XCH<sub>4</sub> Emissions

- **Granularity and Resolution:** The integration of skip connections within the decoder allows for the recovery of fine-grained details. By merging low-level spatial features with high-level semantic insights, the model produces high-resolution segmentation maps, enabling detailed analysis of emission distributions.
- **Multi-Scale Contextual Understanding:** The ASPP module captures spatial patterns across varying scales, from localized emission sources to broader regional dynamics. By integrating these multi-scale insights, the model effectively segments complex and heterogeneous landscapes, including the intricately structured urban-agricultural mosaics characteristic of the YRD.
- **Robust Generalization:** Incorporating random masking during training forces the model to learn from incomplete datasets, reducing its reliance on specific input patterns. This training approach significantly improves the model's robustness and ensures that it can generalize predictions to unseen spatiotemporal scenarios.
- **Scalability:** DeepLabv3+ excels in processing large-scale datasets comprising diverse input features, including urban boundaries, rice paddy extents, and atmospheric CH<sub>4</sub> concentrations. Its computational efficiency allows it to analyze complex datasets without compromising accuracy, making it a versatile tool for regional studies like the YRD and scalable for broader applications in global environmental monitoring and spatiotemporal analysis.

### Limitations and Considerations for DeepLabv3+

- **Temporal Dependence:** The model relies exclusively on 2018 as the training year, introducing potential biases tied to the unique spatiotemporal conditions of that period. While the use of 2018 data provides a baseline for training, the model’s ability to generalize predictions to historical or future periods may be constrained by the specific characteristics of that year, such as land-use patterns and meteorological conditions.
- **Resolution Disparities:** The integration of Landsat imagery (30m resolution) and Sentinel-5P data (7 km² resolution) presents challenges in reconciling disparate spatial scales. Although the CNN’s scale-invariance capabilities mitigate this issue, the inherent resolution gap may affect the granularity of reconstructed outputs, particularly for fine-scale emission hotspots or fragmented landscapes.
- **Data Representation:** Spectral variability and complexities in masking heterogeneous regions pose additional challenges for data consistency. Factors such as mixed spectral signatures in densely populated areas or overlapping land-use classes can introduce noise into the model’s predictions, potentially reducing the reliability of reconstructed CH<sub>4</sub> emission boundaries.

By leveraging the encoder-decoder architecture of DeepLabv3+, this study reconstructs historical CH<sub>4</sub> emissions for 2000 and 2010, using urban boundaries and rice paddy extents as proxies. The integration of high-resolution Landsat imagery with advanced semantic segmentation techniques underscores the transformative potential of deep learning in addressing data gaps and enabling retrospective analyses. This approach not only advances our understanding of the interplay between land-use transitions and atmospheric CH<sub>4</sub> dynamics but also establishes a scalable, replicable framework for tackling complex spatiotemporal challenges in environmental monitoring.

---

# Results

### YRD Urban Mappings (2000, 2010, 2018): GAIA Dataset and Landsat Composites

![Urban Boundaries in the YRD (2000)](/assets/Urb_2000.png)

**<p align="center">Figure 3: Urban Boundaries in the YRD (2000)</p>**
This map illustrates the YRD’s urban extents for the year 2000. Urban boundaries are delineated using GAIA data, derived from high-resolution Landsat imagery. The green-shaded areas represent artificial impervious surfaces, such as roads, buildings, and industrial zones, mapped within the four key provinces. Provincial boundaries are outlined in black for spatial reference. This visualization provides a foundational perspective on the spatial distribution of urbanized areas, capturing the baseline for subsequent analyses of urban expansion and its environmental implications.

![Urban Boundaries in the YRD (2010)](/assets/Urb_2010.png)

**<p align="center">Figure 4: Urban Boundaries in the YRD (2010)</p>**
This map depicts the urban extents within the YRD for the year 2010, derived from GAIA data processed using Landsat imagery. Urban areas, shown in pink, highlight the expansion of impervious surfaces – likely associated with industrial development and transportation infrastructure – across the four provinces. The visible increase in urban boundaries compared to 2000 underscores the rapid urbanization occurring over the decade. Provincial boundaries are delineated for regional context. This visualization demonstrates the accelerated growth of urban centers, particularly around Jiangsu and Shanghai, offering insights into land-use dynamics.

![Urban Boundaries in the YRD (2018)](/assets/Urb_2018.png)

**<p align="center">Figure 5: Urban Boundaries in the YRD (2018)</p>**
This map illustrates the urban extents within the YRD for the year 2018, derived from GAIA data processed using Landsat imagery. Urban areas, shown in purple, highlight the continued expansion of impervious surfaces across Anhui, Zhejiang, Jiangsu, and Shanghai. The urban footprint demonstrates continued growth across all provinces, with Shanghai exhibiting dense, concentrated development. Provincial boundaries provide a spatial context for the distribution of urbanized regions.

![Urban Expansion Trends Across the YRD (2000–2018)](/assets/Urb_2000to2018.png)

**<p align="center">Figure 6: Urban Expansion Trends Across the YRD (2000–2018)</p>**
This map visualizes the total urban expansion within the YRD from 2000 to 2018, as derived from GAIA data processed using Landsat imagery. Urban boundaries for the years 2000, 2010, and 2018 are represented in green, pink, and purple, respectively, illustrating the progressive growth of impervious surfaces over nearly two decades. The overlapping urban extents highlight areas of consistent expansion, with notable growth observed in Jiangsu and Shanghai, as well as the emergence of new urban clusters in Zhejiang and Anhui. Provincial boundaries provide a geographic frame of reference for the spatial distribution of these changes. This visualization underscores the rapid rate of urbanization across the YRD, offering a valuable lens to study its implications for land-use transformations and regional planning.

#### Provincial Urban Extent Mappings (2000, 2010, 2018): GAIA Dataset and Landsat Composites

![Urban Boundaries by Province (2000)](/assets/Prov_2000.png)

**<p align="center">Figure 7: Urban Boundaries by Province (2000)</p>**
This map presents the provincial-scale urban extents within the YRD for the year 2000, as derived from the GAIA dataset using Landsat imagery. Urban boundaries are categorized by province: Anhui, Jiangsu, Shanghai, and Zhejiang, with distinct colors representing each region. The visualization highlights Jiangsu’s dominant urban footprint during this period, with substantial contributions from Shanghai. Smaller, yet identifiable, urban centers are evident in Zhejiang and Anhui, reflecting early-stage urbanization in these provinces. Provincial boundaries provide geographic context, facilitating a comparative analysis of urban development patterns across the YRD. This map serves as a baseline for understanding subsequent urban growth over the next two decades and its implications for land-use transformations.

![Urban Boundaries by Province (2010)](/assets/Prov_2010.png)

**<p align="center">Figure 8: Urban Boundaries by Province (2010)</p>**
This map displays the urban extents for each province within the YRD in 2010, derived from the GAIA dataset and Landsat composites. Urban boundaries are distinguished by province, with unique color coding for clarity. Jiangsu exhibits the largest urban footprint, underscoring its rapid development during the first decade of the 21st century. Significant urban expansion is also observed in Shanghai and Zhejiang, while Anhui’s growth reflects a more moderate trend. Provincial boundaries are provided for geographic context.

![Urban Boundaries by Province (2018)](/assets/Prov_2018.png)

**<p align="center">Figure 9: Urban Boundaries by Province (2018)</p>**
This map illustrates the provincial urban extents within the YRD for the year 2018, based on GAIA-derived data processed from Landsat imagery. Urban areas are color-coded by province, providing clear distinctions in land-use patterns. Jiangsu continues to exhibit the largest urban footprint, reflecting its sustained dominance in regional development. Urban growth in Shanghai shows significant consolidation, while Zhejiang displays notable expansion, particularly along its coastal regions. Anhui demonstrates more dispersed urbanization compared to its neighboring provinces. Provincial boundaries are included for geographic clarity, offering insights into the spatial heterogeneity of urbanization trends as they culminate in this final temporal milestone of the study. This visualization highlights the advanced urban growth along the YRD.

### Paddied Rice Extent Mappings (2000, 2010, 2018): PPPM Algorithm and Landsat Composites

![Paddied Rice Distribution in the YRD (2000)](/assets/Rice_2000.png)

**<p align="center">Figure 10: Paddied Rice Distribution in the YRD (2000)</p>**
This map illustrates the spatial distribution of paddied rice extents in the YRD for the year 2000. Using Landsat imagery processed through the Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm, the visualization captures agricultural landscapes characterized by water-intensive rice cultivation practices. Paddied rice fields are delineated in green, reflecting the region's reliance on agricultural productivity, particularly in Anhui and Jiangsu provinces. Provincial boundaries are included to provide a regional frame of reference. This visualization offers insights into the spatial heterogeneity of rice cultivation, serving as a baseline for assessing future trends and their environmental implications.

![Paddied Rice Distribution in the YRD (2010)](/assets/Rice_2010.png)

**<p align="center">Figure 11: Paddied Rice Distribution in the YRD (2010)</p>**
This map illustrates the paddied rice extents across the YRD provinces for the year 2010. Derived from Landsat imagery and processed using the PPPM algorithm, the highlighted areas represent the spatial distribution of rice fields actively engaged in agricultural production during this period. The classification integrates key phenological stages, such as transplanting and heading, with satellite-derived vegetation indices to isolate rice paddies from other land cover types. The provincial boundaries are overlaid to provide a regional context, emphasizing the relative concentration of rice paddies in Anhui and Jiangsu. This visualization offers insights into agricultural trends within the YRD, reflecting its role as an agricultural hub and its evolving land-use dynamics.

![Paddied Rice Distribution in the YRD (2018)](/assets/Rice_2018.png)

**<p align="center">Figure 12: Paddied Rice Distribution in the YRD (2018)</p>**
This map illustrates the distribution of paddied rice fields across the YRD in 2018, as delineated by the PPPM algorithm applied to Landsat imagery. The paddied rice extents, shown in green, reveal a marked reduction compared to earlier decades, particularly in Shanghai and Zhejiang, aligning with trends in urban expansion. Despite this decline, Jiangsu and Anhui remain dominant in agricultural productivity, showcasing substantial concentrations of paddied rice fields. Provincial boundaries are included for context, emphasizing the spatial disparities in agricultural persistence across the region.

### Overlaying Urban Extents With Paddied Rice Extents: Landsat Composites Coupled With GAIA Dataset and PPPM Algorithm (2000, 2010, 2018)

![Integrated Mapping of Urban Boundaries and Rice Fields in the YRD (2000)](/assets/Urb_Rice_2000.png)

**<p align="center">Figure 13: Integrated Mapping of Urban Boundaries and Rice Fields in the YRD (2000)</p>**
This map overlays urban boundaries and paddied rice extents across the YRD for the year 2000, providing a holistic view of land-use distribution within the region. Urban boundaries, delineated in pink, highlight areas of impervious surfaces, while paddied rice extents, shown in green, emphasize agricultural land. The four provinces – Anhui, Jiangsu, Zhejiang, and Shanghai – are outlined to provide spatial context. This visualization underscores the coexistence of urban and agricultural systems within the YRD at the beginning of the study period, illustrating a baseline for evaluating subsequent changes in land-use dynamics and their implications for regional CH<sub>4</sub> emissions.

![Integrated Mapping of Urban Boundaries and Rice Fields in the YRD (2010)](/assets/Urb_Rice_2010.png)

**<p align="center">Figure 14: Integrated Mapping of Urban Boundaries and Rice Fields in the YRD (2010)</p>**
This map overlays urban boundaries with paddied rice extents within the YRD for the year 2010. Urban areas, delineated in pink, illustrate the continued expansion of impervious surfaces, while paddied rice extents, marked in green, highlight key agricultural zones across the four provinces. The combination of these datasets underscores the spatial juxtaposition of rapid urban growth with agricultural persistence, revealing zones of potential land-use conflict.

![Integrated Mapping of Urban Boundaries and Rice Fields in the YRD (2018)](/assets/Urb_Rice_2018.png)

**<p align="center">Figure 15: Integrated Mapping of Urban Boundaries and Rice Fields in the YRD (2018)</p>**
This map overlays urban boundaries and paddied rice extents within the YRD for 2018, showcasing the intricate spatial relationships between urbanization and agricultural activity in the region. Urban boundaries are outlined in a pink, while paddied rice extents are marked in green, emphasizing their co-occurrence and overlap. The visualization highlights the significant urban expansion and the contraction of paddied rice extents in proximity to urban cores, particularly in Shanghai and Jiangsu provinces. The provincial boundaries provide a contextual framework for understanding regional disparities. By integrating these datasets, the map captures the dual forces of urban growth and agricultural persistence, offering insights into land-use dynamics and their implications for projected CH<sub>4</sub> emissions.

### Raw XCH<sub>4</sub> Emission Extents: S5-P TROPOMI Measurements (2018)

![Spatial Distribution of XCH<sub>4</sub> Emissions Across the YRD (2018)](/assets/XCH4_2018.png)

**<p align="center">Figure 16: Spatial Distribution of XCH<sub>4</sub> Emissions Across the YRD (2018)</p>**
This map depicts raw XCH<sub>4</sub> emissions across the YRD for 2018, derived from the Sentinel-5 Precursor’s (S-5P) TROPOspheric Monitoring Instrument (TROPOMI). Emission intensities are represented on a gradient scale, with darker tones signifying higher CH<sub>4</sub> concentrations.  The dataset's spatial resolution of 7 km² enables the identification of CH<sub>4</sub> hotspots and spatial variability across the four provinces. Noticeable clusters of elevated XCH<sub>4</sub> concentrations align with densely urbanized areas such as Shanghai and significant paddied rice regions in northern Anhui and Jiangsu. These spatial patterns provide foundational insights into the interplay between urbanization, agricultural activity, and atmospheric CH<sub>4</sub> emissions, forming a basis for emission monitoring.

![Hotspot Analysis of XCH<sub>4</sub> Emissions Using Spatial Autocorrelation (2018)](/assets/XCH4_2018_Hotspot.png)

**<p align="center">Figure 17: Hotspot Analysis of XCH<sub>4</sub> Emissions Using Spatial Autocorrelation (2018)</p>**
This map presents the results of a hotspot analysis on XCH<sub>4</sub> emissions across the YRD for 2018, derived from Sentinel-5 Precursor’s (S-5P) TROPOspheric Monitoring Instrument (TROPOMI). Using the Getis-Ord Gi* statistic, the analysis identifies statistically significant clusters of high (hotspots) and low (cold spots) XCH<sub>4</sub> values. Hotspots are concentrated in northern Anhui, Jiangsu, and Zhejiang – areas dominated by extensive paddied rice cultivation – and in urban centers like Shanghai. Cold spots, characterized by lower CH<sub>4</sub> emissions, are found in regions with less intensive agricultural or urban activity. This spatial analysis underscores the strong link between elevated XCH<sub>4</sub> concentrations and anthropogenic sources, including emissions from flooded rice paddies and urban activities, such as the proliferation of NGVs. The visualization offers a detailed, spatially explicit understanding of CH<sub>4</sub> distribution, highlighting key sources and sinks.

### Accuracy Assessment: Remotely Sensed Estimates (GAIA, PPPM) vs. Recorded Agricultural Statistics

![Accuracy Assessment: Bar Chart of Algorithms vs Recorded Statistics](/assets/Provincial-Stats.png)

**<p align="center">Figure 18: Comparative Analysis of Remotely Sensed Data and Recorded Agricultural Statistics Across YRD Provinces (2000–2018)</p>**
This figure provides a comparative analysis of urban extents and paddied rice distributions derived from remotely sensed datasets (GAIA for urban areas and PPPM for rice extents) against China’s official agricultural statistics for the YRD provinces: Shanghai, Zhejiang, Anhui, and Jiangsu. The temporal scope spans three key years: 2000, 2010, and 2018.

For rice cultivation shifts, notable discrepancies emerge in Shanghai and Zhejiang, where the PPPM algorithm underestimates rice distributions. These differences are likely attributed to Shanghai’s high urbanization levels and Zhejiang’s regional complexities, such as mixed-use landscapes and diverse cropping patterns. Anhui and Jiangsu exhibit closer alignment between PPPM-derived rice extents and official statistics, demonstrating the algorithm’s robustness in agriculturally dominated provinces.

In terms of urban areas, GAIA-derived extents consistently show substantial growth across all provinces, particularly in Jiangsu and Shanghai. Between 2000 and 2018, urban areas in Jiangsu expanded more than sixfold, while Shanghai experienced nearly a fivefold increase. These trends underscore the rapid urbanization and infrastructure development driving land-use changes in the region.

This comparative analysis highlights both the strengths and limitations of remote sensing techniques. While these algorithms effectively capture large-scale trends in urban and agricultural land use, they face challenges in highly urbanized or heterogeneous regions. The visualization underscores the dynamic interplay between human development and agricultural land conversion, offering insights for sustainable land-use management and CH<sub>4</sub> emission mitigation strategies in the YRD.

### Forecasting Historical XCH<sub>4</sub> Emissions (2000, 2010) Based on Recorded Urban Extents and Paddied Rice Extents

![XCH<sub>4</sub> Predicted (2000)](/assets/XCH_4_Predicted_2000.png)

**<p align="center">Figure 9.1: XCH<sub>4</sub> Predicted (2000)</p>**

![XCH<sub>4</sub> Predicted (2010)](/assets/XCH_4_Predicted_2010.png)

**<p align="center">Figure 9.2: XCH<sub>4</sub> Predicted (2010)</p>**

---

## Discussion

### Accuracy Assessment: Remotely Sensed Estimates (GAIA, PPPM) vs. Recorded Agricultural Statistics

| Province       | Year | Urban Extent (GAIA) | Paddied Rice (PPPM) | Sown Area of Rice |
|----------------|------|---------------------|---------------------|-------------------|
| **Shanghai**   | 2000 | 1,211               | 1,123               | 1,130             |
| **Zhejiang**   | 2000 | 1,752               | 5,983               | 10,290            |
| **Anhui**      | 2000 | 2,326               | 19,651              | 21,490            |
| **Jiangsu**    | 2000 | 3,008               | 15,505              | 22,090            |
| **Shanghai**   | 2010 | 3,310               | 577                 | 1,210             |
| **Zhejiang**   | 2010 | 6,731               | 6,028               | 8,220             |
| **Anhui**      | 2010 | 4,748               | 22,977              | 23,390            |
| **Jiangsu**    | 2010 | 10,042              | 18,825              | 22,240            |
| **Shanghai**   | 2018 | 5,121               | 536                 | 1,040             |
| **Zhejiang**   | 2018 | 14,957              | 4,463               | 6,510             |
| **Anhui**      | 2018 | 10,217              | 17,430              | 25,450            |
| **Jiangsu**    | 2018 | 19,430              | 16,038              | 22,150            |

**Table 1: Provincial Comparisons of Urban Extent, Paddied Rice, and Sown Area of Rice (2000-2018) in km²</p>**

### Urban Expansion Analysis

The urban growth trajectory across the YRD over nearly two decades highlights rapid and unprecedented land-use changes. In 2000, artificial impervious areas totaled 8,297 km², with the majority concentrated in Jiangsu (3,008 km²), Anhui (2,326 km²), Zhejiang (1,752 km²), and Shanghai (1,211 km²). By 2010, these extents nearly tripled to 24,830 km², driven by dramatic increases in Jiangsu (10,042 km²) and Zhejiang (6,731 km²). Shanghai and Anhui followed with 3,310 km² and 4,748 km², respectively.

By 2018, artificial impervious areas had nearly doubled again, reaching a total of 49,725 km². Jiangsu retained the largest share at 19,430 km², followed by Zhejiang (14,957 km²), Anhui (10,217 km²), and Shanghai (5,121 km²). The cumulative expansion from 2000 to 2018 amounted to an estimated 41,428 km², underscoring the YRD’s position as a global epicenter of urbanization. While these findings provide a quantitative narrative of urban expansion, they must be contextualized within the unique characteristics of each province. For instance, Jiangsu’s substantial urban growth is consistent with its economic development, bolstered by industrial zones and transportation infrastructure. Meanwhile, Shanghai’s expansion, although smaller in absolute terms, represents a near fivefold increase, indicative of its status as a densely urbanized global hub.

This analysis demonstrates the strengths of GAIA-derived urban extents in capturing overarching trends but also highlights the importance of considering provincial scales. Relying solely on impervious area growth may obscure nuanced dynamics, such as land-use policies or urban renewal processes, which merit further investigation.

### PPPM-Derived Paddied Rice vs. Sown Area of Rice Statistics

In contrast, the PPPM algorithm underestimates rice extents in Shanghai and Zhejiang. While PPPM-derived estimates and recorded statistics were nearly identical in 2000 (1,123 km² vs. 1,130 km²), the 2010 and 2018 estimates diverge, with the PPPM algorithm capturing approximately half of the recorded sown area. Shanghai underestimations may stem from the province’s small geographic area and high urban density, while Zhejiang’s errors may result from the province’s mixed-use landscapes and agricultural-urban overlap. Despite these limitations in spectral classification, the alignment between satellite-derived estimates and recorded statistics demonstrates the algorithm’s utility for large-scale assessments. The PPPM algorithm demonstrates significant utility in capturing broad-scale trends. Its accuracy in Anhui and Jiangsu reinforces its application for monitoring agricultural systems, while its challenges in urbanized provinces highlight areas for refinement. Integrating additional datasets, like high-resolution SAR imagery, might enhance the model’s ability to delineate agricultural extents across complex environments.

### Spatial Assessment of XCH<sub>4</sub> Emission Concentrations
The spatial analysis of XCH<sub>4</sub> concentrations derived from S-5P TROPOMI data reveals statistically significant clustering, as evidenced by a Moran’s Index of 0.46 and a z-score of 276.31. These metrics confirm a less than 1% likelihood of random spatial patterns, underscoring the structured interplay of emission sources. Hotspots of high XCH<sub>4</sub> concentrations are concentrated in agriculturally intensive areas – notably paddied rice fields in northern Anhui, Jiangsu, and northeastern Zhejiang. Urban hotspots, such as central Shanghai and southwestern Zhejiang, further highlight the contribution of urban emissions, potentially linked to NGVs and industrial activities.

Clustering patterns emphasize the dual role of agriculture and urbanization in shaping regional CH<sub>4</sub> emissions. The alignment of hotspot regions with areas of intensive land-use activity corroborates the hypothesis of anthropogenic drivers behind emission patterns. By establishing these spatial relationships, the study provides potential insights for emission mitigation strategies and supports the development of region-specific policies along the YRD.

### Merging Remote Sensing and Machine Learning
Using the DeepLabv3+ architecture, this study forecasts historical XCH<sub>4</sub> emission boundaries for 2000 and 2010. By inputting urban and paddied rice boundaries from those years, the model generates segmentation maps to predict CH<sub>4</sub> emissions. Although 2018 data serves as the sole reference for training, the model demonstrates strong potential for reconstructing historical CH<sub>4</sub> patterns, paving the way for deeper considerations into the region’s emission trends. The predicted XCH<sub>4</sub> emission maps align with observed urban and agricultural dynamics, offering valuable context for interpreting S-5P’s 2018 data. This forecasting approach underscores the potential for integrating satellite imagery with machine learning to address temporal data gaps.

This study exemplifies the transformative potential of merging remote sensing with machine learning frameworks. The successful integration of high-resolution satellite imagery and advanced algorithms demonstrates the viability of autonomous environmental monitoring at regional scales. As open-source data and computational resources continue to expand, future research will likely achieve real-time observations and unprecedented levels of detail. These advancements hold immense promise for climate modeling, emission mitigation strategies, and sustainable land-use planning.

### Potential Limitations and Future Implications

While this study advances the understanding of CH<sub>4</sub> emissions along the YRD, a few limitations warrant discussion:

- **Data Availability:** Temporal gaps in satellite data, particularly the absence of pre-2018 XCH<sub>4</sub> observations, limit direct validation of historical predictions.
- **Emission Representation:** China’s agricultural statistics omit contributions from NGV-emitted CH<sub>4</sub>, which may result in underreported national emissions.
- **Consistency Assumptions:** The model assumes static relationships between land use and CH<sub>4</sub> emissions over time, which may not fully account for evolving emission dynamics.

Future work could integrate additional data sources, such as provincial CH<sub>4</sub> inventories or high-resolution SAR data, to refine predictions and validate historical trends. Enhancements in model architecture, including advanced feature engineering and multi-sensor data fusion, could further improve segmentation accuracy and computational efficiency.

---
## Open-Source Code Availability

The GEE links and the Google Colab Notebook containing the CNN model can be accessed below:

- **GAIA:** [Link to GAIA on Google Earth Engine](https://code.earthengine.google.com/7f2eb1d430833ff194bd4ccd7e724b39)
- **PPPM:** [Link to PPPM on Google Earth Engine](https://code.earthengine.google.com/a850b64d8fe124e6d2fc4c7ac599a09a)
- **Google Colab Jupyter Notebook (DeepLabv3+ Architecture):** [Colab Notebook Link](https://colab.research.google.com/drive/1HTWfWMo0rU8-jP6z2rowWxtN6Jt4CJPp?usp=sharing)

---

## References
Aitken, Kyle, et al. “Understanding How Encoder-Decoder Architectures Attend.” Advances in Neural Information Processing Systems, edited by M. Ranzato et al., vol. 34, Curran Associates, Inc., 2021, pp. 22184–95, https://proceedings.neurips.cc/paper/2021/file/ba3c736667394d5082f86f28aef38107- Paper.pdf.
Asilo, Sonia, et al. “Complementarity of Two Rice Mapping Approaches: Characterizing Strata Mapped by Hypertemporal MODIS and Rice Paddy Identification Using Multitemporal SAR.” Remote Sensing, vol. 6, no. 12, Dec. 2014, pp. 12789–814. DOI.org (Crossref), https://doi.org/10.3390/rs61212789.				
Ball, John E., et al. “Comprehensive Survey of Deep Learning in Remote Sensing: Theories, Tools, and Challenges for the Community.” Journal of Applied Remote Sensing, vol. 11, no. 04, Sept. 2017, p. 1. DOI.org (Crossref), https://doi.org/10.1117/1.JRS.11.042609.				
Ban, Yifang, et al. “Global Land Cover Mapping Using Earth Observation Satellite Data: Recent Progresses and Challenges.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 103, May 2015, pp. 1–6. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2015.01.001.
Bereitschaft, Bradley, and Keith Debbage. “Urban Form, Air Pollution, and CO 2 Emissions in Large U.S. Metropolitan Areas.” The Professional Geographer, vol. 65, no. 4, Nov. 2013, pp. 612–35. DOI.org (Crossref), https://doi.org/10.1080/00330124.2013.799991.				
Bloom, A. Anthony, et al. “Large-Scale Controls of Methanogenesis Inferred from Methane and Gravity Spaceborne Data.” Science, vol. 327, no. 5963, Jan. 2010, pp. 322–25. DOI.org (Crossref), https://doi.org/10.1126/science.1175176.
Boschetti, Mirco, et al. “Comparative Analysis of Normalised Difference Spectral Indices Derived from MODIS for Detecting Surface Water in Flooded Rice Cropping Systems.” PLoS ONE, edited by Guy J.-P. Schumann, vol. 9, no. 2, Feb. 2014, p. e88741. DOI.org (Crossref), https://doi.org/10.1371/journal.pone.0088741.
Chen, XueHong, et al. “Global Mapping of Artificial Surfaces at 30-m Resolution.” Science China Earth Sciences, vol. 59, no. 12, Dec. 2016, pp. 2295–306. DOI.org (Crossref), https://doi.org/10.1007/s11430-016-5291-y.
Cheng, G. et al. “Learning rotation-invariant convolutional neural networks for object detection in VHR optical remote sensing images.” IEEE Trans. Geosci. Remote Sens. 2016, 54, 7405–7415. (Crossref), https://ieeexplore.ieee.org/document/7560644.			
China Banking News. “Yangtze River Delta’s GDP Reached USD 3.35 Trillion in 2019, Accounts for Nearly Quarter of National Total.” China Banking News, Jun. 2020. (Crossref), https://www.chinabankingnews.com/2020/06/07/yangtze-river-deltas-gdp-reached-3-35-trillion-yuan-in-2019-accounts-for-nearly-quarter-of-national-total/.		
Da Pan, et al. “Methane Emissions from Natural Gas Vehicles in China.” Nature Communications, vol. 11, no. 1, Dec. 2020, p. 4588. DOI.org (Crossref), https://doi.org/10.1038/s41467-020-18141-0.				
Dao, Phuong, and Yuei-An Liou. “Object-Based Flood Mapping and Affected Rice Field Estimation with Landsat 8 OLI and MODIS Data.” Remote Sensing, vol. 7, no. 5, Apr. 2015, pp. 5077–97. DOI.org (Crossref), https://doi.org/10.3390/rs70505077.				
Dong, Jinwei, et al. “Tracking the Dynamics of Paddy Rice Planting Area in 1986–2010 through Time Series Landsat Images and Phenology-Based Algorithms.” Remote Sensing of Environment, vol. 160, Apr. 2015, pp. 99–113. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2015.01.004.			
Dosovitskiy, Alexey, et al. An Image Is Worth 16x16 Words: Transformers for Image Recognition at Scale. arXiv:2010.11929, arXiv, 3 June 2021. arXiv.org, http://arxiv.org/abs/2010.11929.					
Dou, Yujie, et al. “Mapping High Temperature Damaged Area of Paddy Rice along the Yangtze River Using Moderate Resolution Imaging Spectroradiometer Data.” International Journal of Remote Sensing, vol. 41, no. 2, Jan. 2020, pp. 471–86. DOI.org (Crossref), https://doi.org/10.1080/01431161.2019.1643936.				
Du, Lin, et al. “Estimation of Rice Leaf Nitrogen Contents Based on Hyperspectral LIDAR.” International Journal of Applied Earth Observation and Geoinformation, vol. 44, Feb. 2016, pp. 136–43. DOI.org (Crossref ), https://doi.org/10.1016/j.jag.2015.08.008.					
Esam, Othman, et al. “Using convolutional features and a sparse autoencoder for land-use scene classification.” International Journal of Remote Sensing, 2016, 37:10, 2149 2167, DOI.org (Crossref): 10.1080/01431161.2016.1171928.
EY Greater China. “How is the Yangtze River Delta driving China’s economic development?” EY, Apr. 2020. (Crossref), https://www.ey.com/en-cn/china-opportunities/how-is- yangtze-river-delta-driving-china-economic-development.
Feichtenhofer, Christoph, et al. Masked Autoencoders As Spatiotemporal Learners. arXiv:2205.09113, arXiv, 21 Oct. 2022. arXiv.org, http://arxiv.org/abs/2205.09113.		
Frankenberg, C. et al. “Assessing methane emissions from global space-borne observations.” Science, 308, 1010–1014, 2005.
Friedl, Mark A., et al. “MODIS Collection 5 Global Land Cover: Algorithm Refinements and Characterization of New Datasets.” Remote Sensing of Environment, vol. 114, no. 1, Jan. 2010, pp. 168–82. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2009.08.016.				
Goldblatt, Ran, et al. “Detecting the Boundaries of Urban Areas in India: A Dataset for Pixel-Based Image Classification in Google Earth Engine.” Remote Sensing, vol. 8, no. 8, Aug. 2016, p. 634. DOI.org (Crossref), https://doi.org/10.3390/rs8080634.
Gong, Peng, et al. “Annual Maps of Global Artificial Impervious Area (GAIA) between 1985 and 2018.” Remote Sensing of Environment, vol. 236, Jan. 2020, p. 111510. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2019.111510.
Gu, Chaolin, et al. “Climate Change and Urbanization in the Yangtze River Delta.” Habitat International, vol. 35, no. 4, Oct. 2011, pp. 544–52. DOI.org (Crossref), https://doi.org/10.1016/j.habitatint.2011.03.002.
Gumma, Murali Krishna. “Mapping Rice Areas of South Asia Using MODIS Multitemporal Data.” Journal of Applied Remote Sensing, vol. 5, no. 1, Jan. 2011, p. 053547. DOI.org (Crossref), https://doi.org/10.1117/1.3619838.
Hao, Pengyu, et al. “Annual Cropland Mapping Using Reference Landsat Time Series—A Case Study in Central Asia.” Remote Sensing, vol. 10, no. 12, Dec. 2018, p. 2057. DOI.org (Crossref), https://doi.org/10.3390/rs10122057.	
Hayashida, S., et al. “Methane Concentrations over Monsoon Asia as Observed by SCIAMACHY: Signals of Methane Emission from Rice Cultivation.” Remote Sensing of Environment, vol. 139, Dec. 2013, pp. 246–56. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2013.08.008.				
He, Kaiming, et al. “Masked Autoencoders Are Scalable Vision Learners.” 2022 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), IEEE, 2022, pp. 15979–88. DOI.org (Crossref), https://doi.org/10.1109/CVPR52688.2022.01553.	
Hu, Fan, et al. “Transferring Deep Convolutional Neural Networks for the Scene Classification of High-Resolution Remote Sensing Imagery.” Remote Sensing, vol. 7, no. 11, Nov. 2015, pp. 14680–707. DOI.org (Crossref), https://doi.org/10.3390/rs71114680.					
Hu, Ning, et al. “Large Methane Emissions from Natural Gas Vehicles in Chinese Cities.” Atmospheric Environment, vol. 187, Aug. 2018, pp. 374–80. DOI.org (Crossref), https://doi.org/10.1016/j.atmosenv.2018.06.007.
Jiang, et al., “The effect of rice plant traits on methane emissions from paddy fields: A review.” Chinese Journal of Eco-Agriculture, vol 26, 2018, pp. 175-181. DOI.org (Crossref), https://doi.org/10.13930/j.cnki.cjea.171155.
Kontgis, Caitlin, et al. “Mapping Rice Paddy Extent and Intensification in the Vietnamese Mekong River Delta with Dense Time Stacks of Landsat Data.” Remote Sensing of Environment, vol. 169, Nov. 2015, pp. 255–69. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2015.08.004.					
Krizhevsky, Alex, et al. “ImageNet Classification with Deep Convolutional Neural Networks.” Advances in Neural Information Processing Systems, edited by F. Pereira et al., vol. 25, Curran Associates, Inc., 2012, https://proceedings.neurips.cc/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b- Paper.pdf.		
LeCun, Y., et al. “Backpropagation Applied to Handwritten Zip Code Recognition.” Neural Computation, vol. 1, no. 4, Dec. 1989, pp. 541–51, https://doi.org/10.1162/neco.1989.1.4.541.					
Li, Shuang, et al. “Understanding Urban Growth in Beijing-Tianjin-Hebei Region over the Past 100 Years Using Old Maps and Landsat Data.” Remote Sensing, vol. 13, no. 16, Aug. 2021, p. 3264. DOI.org (Crossref), https://doi.org/10.3390/rs13163264.	
Li, Wenjing, et al. “Climate Change Perceptions and the Adoption of Low-Carbon Agricultural Technologies: Evidence from Rice Production Systems in the Yangtze River Basin.” Science of The Total Environment, vol. 759, Mar. 2021, p. 143554. DOI.org (Crossref), https://doi.org/10.1016/j.scitotenv.2020.143554.					
Liu, Dandan, et al. “Annual Large-Scale Urban Land Mapping Based on Landsat Time Series in Google Earth Engine and OpenStreetMap Data: A Case Study in the Middle Yangtze River Basin.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 159, Jan. 2020, pp. 337–51. DOI.org (Crossref ), https://doi.org/10.1016/j.isprsjprs.2019.11.021.	
Liu, Dandan, and Nengcheng Chen. “Satellite Monitoring of Urban Land Change in the Middle Yangtze River Basin Urban Agglomeration, China between 2000 and 2016.” Remote Sensing, vol. 9, no. 11, Oct. 2017, p. 1086. DOI.org (Crossref), https://doi.org/10.3390/rs9111086.				
Liu, Mengyao, et al. “A New Divergence Method to Quantify Methane Emissions Using Observations of Sentinel-5P TROPOMI.” Geophysical Research Letters, vol. 48, no. 18, Sept. 2021. DOI.org (Crossref), https://doi.org/10.1029/2021GL094151.	
Liu, Xiaoping, et al. “High-Resolution Multi-Temporal Mapping of Global Urban Land Using Landsat Images Based on the Google Earth Engine Platform.” Remote Sensing of Environment, vol. 209, May 2018, pp. 227–39. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2018.02.055.
Lo ̈w, Fabian, et al. “Decision Fusion and Non-Parametric Classifiers for Land Use Mapping Using Multi-Temporal RapidEye Data.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 108, Oct. 2015, pp. 191–204. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2015.07.001.					
Luus, F.P.S, et al. “Multiview deeplearning for land-use classification.” IEEE Geosci. Remote Sens. Lett. 2015, 12, 2448–2452. (CrossRef ), https://ieeexplore.ieee.org/document/7307121.			
M. Boschetti, et al. “Multi-year monitoring of rice crop phenology through time series analysis of MODIS images.” International Journal of Remote Sensing, 2009, 30:18, 4643 4662, DOI.org (Crossref), 10.1080/01431160802632249.
Mahdianpari, Masoud, et al. “Very Deep Convolutional Neural Networks for Complex Land Cover Mapping Using Multispectral Remote Sensing Imagery.” Remote Sensing, vol. 10, no. 7, July 2018, p. 1119. DOI.org (Crossref), https://doi.org/10.3390/rs10071119.
Mariotto, Isabella, et al. “Hyperspectral versus Multispectral Crop-Productivity Modeling and Type Discrimination for the HyspIRI Mission.” Remote Sensing of Environment, vol. 139, Dec. 2013, pp. 291–305. DOI.org (Crossref ), https://doi.org/10.1016/j.rse.2013.08.002.	
Marmanis, D.; Datcu, M.; Esch, T.; Stilla, U. Deep learning earth observation classification using imageNet pretrained networks. IEEE Geosci. Remote Sens. 2016, 13, 105–109. (CrossRef), https://ieeexplore.ieee.org/document/7342907.	
Marshall, Michael, and Prasad Thenkabail. “Advantage of Hyperspectral EO-1 Hyperion over Multispectral IKONOS, GeoEye-1, WorldView-2, Landsat ETM+, and MODIS Vegetation Indices in Crop Biomass Estimation.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 108, Oct. 2015, pp. 205–18. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2015.08.001.
National Bureau of Statistics of China. ”Acreage of Sown or Harvested Land of Farm Crops in China from 1980 to 2021 (in Million Hectares).” Statista, Statista Inc., 7 Jul 2022, https://www.statista.com/statistics/275574/acreage-of-sown-or-harvested-land-of- farm-crops-in-china/.
Park, Seonyoung, et al. “Classification and Mapping of Paddy Rice by Combining Landsat and SAR Time Series Data.” Remote Sensing, vol. 10, no. 3, Mar. 2018, p. 447. DOI.org (Crossref), https://doi.org/10.3390/rs10030447.
Peng, Dailiang, et al. “Detection and Estimation of Mixed Paddy Rice Cropping Patterns with MODIS Data.” International Journal of Applied Earth Observation and Geoinformation, vol. 13, no. 1, Feb. 2011, pp. 13–23. DOI.org (Crossref), https://doi.org/10.1016/j.jag.2010.06.001.
Peng, Shushi, et al. “Inventory of Anthropogenic Methane Emissions in Mainland China from 1980 to 2010.” Atmospheric Chemistry and Physics, vol. 16, no. 22, Nov. 2016, pp. 14545–62. DOI.org (Crossref), https://doi.org/10.5194/acp-16-14545-2016.	
Pittman, Kyle, et al. “Estimating Global Cropland Extent with Multi-Year MODIS Data.” Remote Sensing, vol. 2, no. 7, July 2010, pp. 1844–63. DOI.org (Crossref), https://doi.org/10.3390/rs2071844.
Qin Y, et al. “Mapping paddy rice planting area in cold temperate climate region through analysis of time series Landsat 8 (OLI), Landsat 7 (ETM+) and MODIS imagery.” ISPRS Journal Photogrammetry and Remote Sensing, 2015 Jul;105:220-233. DOI.org (Crossref), https://pubmed.ncbi.nlm.nih.gov/27695195.	
Seto, Karen C., et al. “A Meta-Analysis of Global Urban Land Expansion.” PLoS ONE, edited by Juan A. An ̃el, vol. 6, no. 8, Aug. 2011, p. e23777. DOI.org (Crossref), https://doi.org/10.1371/journal.pone.0023777.
Son, Nguyen-Thanh, et al. “A Phenology-Based Classification of Time-Series MODIS Data for Rice Crop Monitoring in Mekong Delta, Vietnam.” Remote Sensing, vol. 6, no. 1, Dec. 2013, pp. 135–56. DOI.org (Crossref), https://doi.org/10.3390/rs6010135.
Song, Hongqing, et al. “Energy Consumption and Greenhouse Gas Emissions of Diesel/LNG Heavy-Duty Vehicle Fleets in China Based on a Bottom-up Model Analysis.” Energy, vol. 140, Dec. 2017, pp. 966–78. DOI.org (Crossref), https://doi.org/10.1016/j.energy.2017.09.011.
Thenkabail, P.S. “Mapping rice areas of South Asia using MODIS multitemporal data.” J. Appl. Remote Sens. 2011, 5, 863–871.
Wardlow, Brian D., and Stephen L. Egbert. “Large-Area Crop Mapping Using Time- Series MODIS 250 m NDVI Data: An Assessment for the U.S. Central Great Plains.” Remote Sensing of Environment, vol. 112, no. 3, Mar. 2008, pp. 1096–116. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2007.07.019.			
Worldometer. China Statistics. https://www.worldometers.info/world-population/china-population/ (2021).
Xiao, Xiangming, Stephen Boles, Steve Frolking, et al. “Mapping Paddy Rice Agriculture in South and Southeast Asia Using Multi-Temporal MODIS Images.” Remote Sensing of Environment, vol. 100, no. 1, Jan. 2006, pp. 95–113. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2005.10.004.
Xiao, Xiangming, Stephen Boles, Jiyuan Liu, et al. “Mapping Paddy Rice Agriculture in Southern China Using Multi-Temporal MODIS Images.” Remote Sensing of Environment, vol. 95, no. 4, Apr. 2005, pp. 480–92. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2004.12.009.	
Xu, Xinjie, et al. “Evaluation of One-Class Support Vector Classification for Mapping the Paddy Rice Planting Area in Jiangsu Province of China from Landsat 8 OLI Imagery.” Remote Sensing, vol. 10, no. 4, Apr. 2018, p. 546. DOI.org (Crossref), https://doi.org/10.3390/rs10040546.	
Yan, Yan, et al. “Impacts of Impervious Surface Expansion on Soil Organic Carbon – a Spatially Explicit Study.” Scientific Reports, vol. 5, no. 1, Dec. 2015, p. 17905. DOI.org (Crossref), https://doi.org/10.1038/srep17905.	
Yang, Di, et al. “Open Land-Use Map: A Regional Land-Use Mapping Strategy for Incorporating OpenStreetMap with Earth Observations.” Geo-Spatial Information Science, vol. 20, no. 3, July 2017, pp. 269–81. DOI.org (Crossref), https://doi.org/10.1080/10095020.2017.1371385.		
Zhang, Ce, Xin Pan, et al. “A Hybrid MLP-CNN Classifier for Very Fine Resolution Remotely Sensed Image Classification.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 140, June 2018, pp. 133–44. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2017.07.014.
Zhang, Geli, Xiangming Xiao, et al. “Fingerprint of Rice Paddies in Spatial–Temporal Dynamics of Atmospheric Methane Concentration in Monsoon Asia.” Nature Communications, vol. 11, no. 1, Dec. 2020, p. 554. DOI.org (Crossref), https://doi.org/10.1038/s41467-019-14155-5.
Zhang, Jiaxing, et al. “The Spatial and Temporal Distribution Patterns of XCH<sub>4</sub> in China: New Observations from TROPOMI.” Atmosphere, vol. 13, no. 2, Jan. 2022, p. 177. DOI.org (Crossref), https://doi.org/10.3390/atmos13020177.			
Zhang, Meng, Hui Lin, et al. “Mapping Paddy Rice Using a Convolutional Neural Network (CNN) with Landsat 8 Datasets in the Dongting Lake Area, China.” Remote Sensing, vol. 10, no. 11, Nov. 2018, p. 1840. DOI.org (Crossref), https://doi.org/10.3390/rs10111840.
Zhang, Xiaoyang, et al. “Monitoring Vegetation Phenology Using MODIS.” Remote Sensing of Environment, vol. 84, no. 3, Mar. 2003, pp. 471–75. DOI.org (Crossref), https://doi.org/10.1016/S0034-4257(02)00135-9.
Zhang, Xin, Bingfang Wu, et al. “Mapping Up-to-Date Paddy Rice Extent at 10 M Resolution in China through the Integration of Optical and Synthetic Aperture Radar Images.” Remote Sensing, vol. 10, no. 8, July 2018, p. 1200. DOI.org (Crossref), https://doi.org/10.3390/rs10081200.
Zhang, Y., et al. “Quantifying Methane Emissions from Rice Paddies in Northeast China by Integrating Remote Sensing Mapping with a Biogeochemical Model.” Biogeosciences, vol. 8, no. 5, May 2011, pp. 1225–35. DOI.org (Crossref), https://doi.org/10.5194/bg-8-1225-2011.	
Zhang, Yuan, et al. “Characterizing Spatiotemporal Dynamics of Methane Emissions from Rice Paddies in Northeast China from 1990 to 2010.” PLoS ONE, edited by Julian Clifton, vol. 7, no. 1, Jan. 2012, p. e29156. DOI.org (Crossref), https://doi.org/10.1371/journal.pone.0029156.	
Zhou, Feng, et al. “A New High-Resolution N2O Emission Inventory for China in 2008.” Environmental Science Technology, vol. 48, no. 15, Aug. 2014, pp. 8538–47. DOI.org (Crossref), https://doi.org/10.1021/es5018027.
Zhou, Yuting, et al. “Mapping Paddy Rice Planting Area in Rice-Wetland Coexistent Areas through Analysis of Landsat 8 OLI and MODIS Images.” International Journal of Applied Earth Observation and Geoinformation, vol. 46, Apr. 2016, pp. 1–12. DOI.org (Crossref), https://doi.org/10.1016/j.jag.2015.11.001.
Zhu, Lihong, et al. “Detection of Paddy Rice Cropping Systems in Southern China with Time Series Landsat Images and Phenology-Based Algorithms.” GIScience Remote Sensing, vol. 58, no. 5, July 2021, pp. 733–55. DOI.org (Crossref), https://doi.org/10.1080/15481603.2021.1943214.
Zhu, Min, et al. “Population and Economic Projections in the Yangtze River Basin Based on Shared Socioeconomic Pathways.” Sustainability, vol. 12, no. 10, May 2020, p. 4202. DOI.org (Crossref), https://doi.org/10.3390/su12104202.
