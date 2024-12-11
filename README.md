# Urban-Methane Transfers (2000 - 2018): A Convolutional Neural Network (CNN) Approach at Forecasting Historical XCH<sub>4</sub> Emissions through Urban Boundaries and Paddied Rice Extents Along China's YRD

## Overview
This repository presents the findings and methodologies from a comprehensive study integrating remote sensing and machine learning to understand atmospheric CH<sub>4</sub> emissions in China's Yangtze River Delta (YRD). The project bridges gaps in historical data using Convolutional Neural Networks (CNNs) to reconstruct emission distributions, providing insights into the interplay between urban expansion, rice cultivation, and greenhouse gas (GHG) emissions.

## Table of Contents

- **Abstract**
- **Introduction**
- **Objectives and Hypotheses**
- **Methodology**
  - **Urban Expansion Analysis:** Utilizing GAIA data to map urban growth in the YRD.
  - **Paddied Rice Extent Mapping:** Applying the PPPM algorithm for agricultural monitoring.
  - **Historical XCH<sub>4</sub> Emission Reconstruction:** Using DeepLabv3+ for spatiotemporal methane analysis.
- **Results**
  - **Urbanization Trends:** Quantifying urban growth across the YRD.
  - **Agricultural Land Dynamics:** Mapping and characterizing changes in paddied rice extents.
  - **Integrated Land-Use Analysis:** Assessing urban-agricultural tradeoffs and implications.
  - **XCH<sub>4</sub> Emission Patterns:** Spatial trends and historical reconstructions of methane (CH<sub>4</sub>) hotspots.
- **Discussion**
  - **Urban and Agricultural Dynamics:** Key drivers, trends, and implications of land-use changes.
  - **Methane Emission Insights:** Linking urbanization, agriculture, and atmospheric CH<sub>4</sub>.
  - **Limitations and Future Directions:** Methodological challenges and recommendations for advancement.
- **Conclusion**
- **Code and Data Availability**
- **References**

---

## Abstract

This study integrates remote sensing and machine learning to unravel the interplay between urban expansion, agriculture, and atmospheric methane (CH<sub>4</sub>) emissions in China’s Yangtze River Delta (YRD). As a global epicenter of dense urbanization and agricultural productivity, the YRD provides a unique lens to examine how land-use changes influence greenhouse gas (GHG) emissions. Using Landsat imagery processed through the Global Artificial Impervious Area (GAIA) and Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithms, the study maps urban boundaries and paddied rice extents with high accuracy, validated against provincial agricultural statistics.

To quantify atmospheric impacts, the analysis incorporates CH<sub>4</sub> emission data derived from the Sentinel-5 Precursor’s (S-5P) TROPOspheric Monitoring Instrument (TROPOMI). Bridging a key temporal gap – Landsat imagery spanning 2000-2018 and S-5P data limited to post-2017 – the study employs a Convolutional Neural Network (CNN) based on the DeepLabv3+ architecture. Selected for its semantic segmentation capabilities, the CNN uses 2018 data to predict historical CH<sub>4</sub> distributions for 2000 and 2010, leveraging recorded urban and paddied rice extents.

This integration of satellite imagery, machine learning algorithms, and deep learning applications addresses critical gaps in understanding land-use change dynamics. By illuminating spatial and temporal CH<sub>4</sub> emission trends, the study offers insights into the YRD’s evolving role in global CH<sub>4</sub> cycles.

---

## Project Summary

This project investigates land-use transformations in China’s YRD, a region characterized by dense urban centers and agricultural productivity. As one of China’s most critical agricultural landscapes, the YRD exemplifies the environmental tradeoffs between rapid urbanization and agricultural persistence. Spanning four provinces – Anhui, Zhejiang, Jiangsu, and Shanghai – this study captures nearly two decades of change (2000, 2010, and 2018), offering a comprehensive view of how urban growth reshapes agricultural systems. By linking these transformations to CH<sub>4</sub> emissions, the study provides a unique lens into the environmental consequences of land-use change.

To monitor these shifts, the study employs supervised machine learning algorithms applied to Landsat imagery (Landsat 5, 7, and 8) for the automated classification of urban boundaries and paddied rice extents. These high-resolution (30-meter) classifications reveal granular trends in land use, highlighting the interdependence of urbanization and agriculture. While prior research has extensively documented these dynamics, this study introduces an atmospheric dimension: spatiotemporal distributions of CH<sub>4</sub> emissions.

To quantify spatiotemporal distributions of CH<sub>4</sub> concentrations, this study employs column-averaged dry air mixing ratio of methane (XCH<sub>4</sub>) data from the TROPOspheric Monitoring Instrument (TROPOMI) onboard the Sentinel-5 Precursor (S5-P) satellite. With a spatial resolution of 7 km², the TROPOMI dataset is particularly suited for identifying CH<sub>4</sub> sources and sinks across heterogeneous landscapes throughout the YRD, offering valuable insights into regional emission patterns (Zhang et al., 2023). However, the late-2017 launch of S-5P confines CH<sub>4</sub> data availability to 2018, necessitating innovative solutions to address temporal gaps.

By integrating high-resolution land-use classifications with atmospheric CH<sub>4</sub> analysis, this study presents a novel framework for understanding the interconnected impacts of urbanization, agriculture, and climate-relevant emissions. These findings offer valuable insights into the YRD’s evolving role in global CH<sub>4</sub> dynamics, underscoring the need for sustainable land-use planning and emission mitigation strategies.

### Atmospheric CH<sub>4</sub> Investigations: Paddied Rice and the Rise of NGVs

Agriculture and urbanization are pivotal drivers of atmospheric CH<sub>4</sub> emissions, with biogenic and anthropogenic sources intricately interwoven along the YRD. Among these, rice paddies persist as significant contributors. As China’s keystone agricultural export, paddied rice depends on water-intensive cultivation methods such as flooding, which create anaerobic conditions conducive to CH<sub>4</sub> production (G. Zhang et al., 2020). Within the YRD, these emissions are further compounded by an urban-linked source: Natural Gas Vehicles (NGVs). Over the past two decades, NGV production in China has surged dramatically – from 6,000 vehicles in 2000 to 6 million by 2017 (Da Pan et al., 2020). While NGVs offer a cleaner alternative to traditional fossil fuels, retrofitted vehicles often suffer from faulty tailpipes, releasing an estimated 196 kg of CH<sub>4</sub> per vehicle annually (Hu et al., 2018).

This study leverages NGVs as a proxy for urbanization, analyzing their fleet-wide contributions to atmospheric CH<sub>4</sub> concentrations. Together, rice paddies and NGVs underscore the intertwined nature of agricultural and urban systems in shaping regional CH<sub>4</sub> emissions. By quantifying these sources within the spatial and temporal context of the YRD, the study highlights the dual pressures of feeding a growing population and sustaining urban expansion.

Moreover, this interdisciplinary approach sheds light on the broader implications of land-use transitions. Understanding the combined impact of paddied rice cultivation and NGV emissions not only provides a regional perspective on CH<sub>4</sub> dynamics but also underscores the need for targeted mitigation strategies. These findings contribute to global discussions on reducing GHG emissions and highlight the YRD’s role in informing sustainable development policies.

### XCH<sub>4</sub> Emissions: TROPOspheric Monitoring Instrument (TROPOMI)

CH<sub>4</sub> is a potent GHG, with a global warming potential 25-30 times greater than carbon dioxide (CO<sub>2</sub>) over a 100-year period (Y. Zhang et al., 2011). To analyze the spatial distribution of XCH<sub>4</sub> emissions, this study applies advanced statistical techniques. The Getis-Ord Gi* statistic identifies significant clusters of high or low XCH<sub>4</sub> concentrations, while Global Moran’s I quantifies spatial autocorrelation, assessing the relationship between emission values and their geographic locations. These methods help distinguish meaningful patterns from randomness, enabling the identification of statistically significant hot spots and clusters. Together, these analyses provide a spatially explicit understanding of CH<sub>4</sub> emissions along the YRD.

The temporal scope of XCH<sub>4</sub> observations is limited to 2018 due to the S-5P satellite’s launch timeline. This study addresses this constraint by aligning XCH<sub>4</sub> visualizations with previously mapped urban and paddied rice extents, creating a consistent provincial-scale framework for examining CH<sub>4</sub> emissions. The resulting spatial overlays reveal the interconnected impacts of land-use changes and atmospheric CH<sub>4</sub> concentrations, bridging the study’s land-use and atmospheric dimensions.

By integrating TROPOMI’s XCH<sub>4</sub> data with detailed land-use classifications, this analysis advances our understanding of the YRD’s role in regional and global CH<sub>4</sub> cycles. It highlights the value of combining remote sensing and statistical analyses to uncover emission dynamics.

### Machine Learning Applications: Encoder-Decoder Architecture of CNNs

To address temporal gaps in satellite-derived CH<sub>4</sub> observations, this study employs a Convolutional Neural Network (CNN) built on the DeepLabv3+ architecture, a cutting-edge model designed for semantic segmentation tasks. The encoder-decoder architecture of the CNN is particularly well-suited to this study’s objectives, as it integrates multi-scale contextual information from input data while recovering fine-grained details through skip connections in the decoder module. Key innovations, such as atrous convolution with spatial pyramid pooling (ASPP), enhance the model’s ability to segment complex spatial patterns, making it ideal for heterogeneous land-use data (Long et al., 2015).

The CNN is trained and validated using 2018 data, where urban and paddied rice extents derived from Landsat imagery are aligned with XCH<sub>4</sub> emission distributions captured by the S-5P satellite. By learning the spatial relationships between urban expansion, agricultural activity, and CH<sub>4</sub> emissions, the model extrapolates these patterns to predict historical XCH<sub>4</sub> distributions for 2000 and 2010, addressing the absence of direct CH<sub>4</sub> data for these years. This approach not only compensates for temporal gaps in satellite observations but also captures the interplay of land-use transitions and atmospheric emissions at a regional scale.

The model training process involves constructing a dataset of Landsat-derived urban and paddied rice maps for 2018, paired with XCH<sub>4</sub> data at a resolution of 7 km². The encoder extracts multi-scale features from these inputs, while the decoder refines segmentation maps to delineate CH<sub>4</sub> emission boundaries. The integration of ASPP enhances the model’s sensitivity to spatial variations, while skip connections enable the recovery of high-resolution details, such as object boundaries.

Ultimately, the CNN outputs high-resolution segmentation maps of historical XCH<sub>4</sub> concentrations, offering a framework for reconstructing CH<sub>4</sub> emission trajectories over time. This methodological advancement not only provides insights into the spatiotemporal dynamics of CH<sub>4</sub> emissions along the YRD but also establishes a replicable approach for addressing data limitations in environmental monitoring. By bridging satellite observations and machine learning, this study exemplifies the potential of integrating emerging technologies to inform sustainable land-use practices and GHG mitigation strategies.

### Novelty of Study

This study bridges the traditionally separate analyses of urbanization and agriculture by linking urban expansion with paddied rice distributions to estimate atmospheric CH<sub>4</sub> emissions within the YRD. This integrated framework offers a perspective on the combined impacts of these opposing land-use dynamics, addressing a gap in understanding the spatiotemporal drivers of GHG emissions. To the best of our knowledge, this represents one of the first large-scale attempts to quantify the collective influence of urbanization and agriculture on CH<sub>4</sub> cycles, leveraging the synergy of remote sensing and machine learning to uncover their intertwined spatiotemporal dynamics.

A key innovation lies in the implementation of an encoder-decoder architecture within a CNN to reconstruct historical XCH<sub>4</sub> emissions for 2000 and 2010. By utilizing urban and paddied rice extents as inputs, the model predicts CH<sub>4</sub> distributions for years lacking direct observations, offering a solution to the temporal limitations of satellite data. This approach demonstrates the versatility of machine learning in environmental monitoring, extending its applicability to address gaps in historical emissions data.

This work showcases the potential of data fusion techniques, combining diverse data structures and sources – including high-resolution Landsat imagery and S5-P TROPOMI data – through rigorous preprocessing and post-processing workflows. By synthesizing spatial, temporal, and atmospheric dimensions, the study provides a newfound lens into the interconnected impacts of land-use transitions and CH<sub>4</sub> emissions in the YRD. Beyond its technical contributions, this research highlights the importance of interdisciplinary approaches in addressing complex environmental challenges, laying the groundwork for future innovations.

### Related-Works and Contributions

This study builds upon two foundational methodologies: the Global Artificial Impervious Area (GAIA) mapping framework (Gong et al., 2019) and the Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm (Zhu et al., 2021). These seminal works provide the critical tools for accurately delineating urban extents and isolating paddied rice fields within the heterogeneous landscapes of the YRD.

The GAIA methodology serves as the cornerstone for mapping urban boundaries by detecting impervious surfaces across spatially complex environments with precision. Concurrently, the PPPM algorithm refines paddied rice mapping through its innovative use of phenological cycles and pixel-based analyses, enabling a granular understanding of mixed-cropping practices in agriculturally intensive regions.

By synthesizing these methodologies, this study advances their applications to probe the intricate relationship between urban expansion and agricultural persistence. This integrated approach not only illuminates regional CH<sub>4</sub> emissions with heightened clarity but also paves the way for broader explorations of land-use transitions and their environmental consequences.


### Auxiliary Data

To augment the remote sensing and machine learning methodologies, this study integrates auxiliary datasets that provide essential historical and environmental context for CH<sub>4</sub> emissions. These supplementary datasets enable a more comprehensive analysis of regional emissions and their driving factors.

Historical CH<sub>4</sub> emissions inventories, segmented into contributions from paddied rice and urban sources, are sourced from the Global Methane Initiative (GMI), an Environmental Protection Agency (EPA)-led project. Spanning 1990-2050 and expressed in million metric tons of CO<sub>2</sub>-equivalent (MMTCO<sub>2</sub>e), these inventories establish a baseline for tracking emissions trends over time.

Urban CH<sub>4</sub> emissions are assessed using population statistics (per 10,000 persons) and natural gas consumption proportions, both obtained from the National Bureau of Statistics of China. Paddied rice-related emissions are contextualized through data on the sown area of rice fields (per 1,000 hectares), also provided by the National Bureau of Statistics of China. These metrics ensure a nuanced understanding of emissions across urban and agricultural domains.

Additionally, annual provincial-level temperature data, acquired from the Climate Knowledge Portal (World Bank), inform the study’s consideration of seasonality in paddied rice flooding periods and their associated CH<sub>4</sub> releases. These climatological variables are crucial for contextualizing emissions within broader environmental patterns.

By integrating publicly accessible datasets, this study enhances its analysis with comprehensive historical and climatological dimensions, providing greater accuracy and a more contextually grounded understanding of the spatiotemporal drivers of CH<sub>4</sub> emissions.


### Intellectual Merits and Broader Implications

This study operates at the intersection of environmental monitoring and predictive modeling, presenting a novel spatiotemporal framework for analyzing the interconnections between urban expansion, paddied rice extents, and atmospheric CH<sub>4</sub> concentrations within the YRD. By quantifying the Urban-Methane transfers within China’s most densely populated and agriculturally productive provinces, this research deepens the understanding of regional CH<sub>4</sub> dynamics and their broader environmental implications.

By addressing the challenges of land-use transitions and their environmental repercussions, this work underscores the critical role of interdisciplinary approaches in tackling complex global issues, offering a pathway toward more effective environmental management and climate resilience.

---

## Background

![Study Area - Yangtze River Delta (YRD)](/assets/Case_Study.png)

**<p align="center">Figure 1: Study Area - Yangtze River Delta (YRD)</p>**  
This map illustrates the geographical scope of the study, encompassing the four provincial regions of Anhui, Zhejiang, Jiangsu, and Shanghai within the YRD. The provincial boundaries are outlined in red, highlighting the spatial heterogeneity of the region. The inset map situates the YRD within China, emphasizing its strategic significance as a densely populated and agriculturally vital area. This area serves as the focal point for analyzing the interplay between urban expansion, paddied rice cultivation, and atmospheric CH<sub>4</sub> emissions.


### China’s Population and Land-Use Transformation

China, home to an estimated 1.44 billion people, constitutes approximately 18.47% of the global population (Worldometer, 2021), making it the world’s most populous nation. Rapid urbanization has become a cornerstone of China’s economic and social development, often marked by the conversion of agricultural land to urban areas.  

This study investigates these land-use transformations by analyzing the interplay between urban expansion and paddied rice cultivation, focusing on three temporal milestones: 2000, 2010, and 2018. The research examines spatial dynamics across four diverse provinces—Anhui, Zhejiang, Jiangsu, and Shanghai—collectively forming the YRD, an area renowned as both the most densely populated region in the world and a critical nexus of urban and agricultural activity.

### Anthology of the YRD: Economic and Environmental Foundations

The YRD owes its economic dominance to its unique environmental and geographic attributes. Centered around the Yangtze River—the largest river in China and the third largest globally, spanning 1.8 million km² (Zhu et al., 2020)—the region has historically utilized its vast river networks to foster trade, agriculture, and industrial growth.  

Encompassing 27 cities over an area of 225,065 km² and housing 163 million people (EY Greater China, 2020), the YRD generates nearly 24% of China’s GDP, representing a fusion of natural resource abundance and economic ingenuity. Historically, YRD cities capitalized on their riverine infrastructure to establish specialized industries. Yangzhou dominated the salt trade; Wuxi contributed one-fourth of China’s rice production; Suzhou and Hangzhou thrived as textile hubs; and Ningbo and Yin served as pivotal trading ports (Gu et al., 2011). These industries leveraged the region’s interconnected waterways for seamless transportation and market integration.  

This synergistic relationship between natural resources and industry laid the foundation for the YRD’s evolution into an economic powerhouse.

### Shanghai: Catalyst of Global Urbanization

Shanghai’s ascension to a global hub epitomizes the YRD’s urban and economic transformation. Strategically located at the Yangtze River estuary, Shanghai’s rise was catalyzed by key treaties, including the 1842 Nanjing Treaty and the 1843 Treaty of Humen, which opened its ports to international trade (Gu et al., 2011).  

These agreements spurred migration, foreign investment, and the establishment of international factories, cementing Shanghai’s role as China’s largest export hub by the late 19th century. The city’s historical trajectory underscores its pivotal role in shaping both the urban dynamics and economic landscape of the YRD.

### The YRD: Agricultural Epicenter of Paddied Rice

The YRD’s marine monsoon subtropical climate, characterized by hot, humid summers and cool, dry winters, enables exceptional agricultural productivity. The region contributes 40% of China’s total agricultural output, with rice cultivation accounting for 70% of this yield (Li et al., 2021).  

However, this agricultural productivity comes at an environmental cost. Flooded paddied rice fields are among the largest contributors to atmospheric CH<sub>4</sub> (Y. Zhang et al., 2011). As global temperatures rise, the fertilization rate of rice is expected to increase, further boosting yields while intensifying CH<sub>4</sub> emissions due to heightened microbial activity in flooded fields (G. Zhang et al., 2020).  

This duality positions the YRD as a critical case study for balancing food security with climate mitigation efforts, as it remains one of the largest global contributors to biogenic CH<sub>4</sub> emissions.

### Paddied Rice: Biogenic Methane Emitters

Rice paddies are a cornerstone of China’s agricultural landscape, spanning nearly 30 million hectares (Jiang et al., 2018) and accounting for a substantial portion of global CH<sub>4</sub> emissions.  

As one of the world’s largest biogenic sources of CH<sub>4</sub>, rice cultivation contributes approximately 25–36% of global agricultural CH<sub>4</sub> emissions (G. Zhang et al., 2020). These emissions stem primarily from the anaerobic decomposition of organic matter in flooded fields—a method critical to rice production but inherently conducive to CH<sub>4</sub> release.  

This positions rice paddies at the intersection of two pressing challenges: sustaining agricultural yields to meet food export demands while minimizing their significant environmental impact.

### Natural Gas Vehicles: Urban Methane Emissions and Retrofitting Challenges

China’s strategy to reduce GHG emissions includes a nationwide shift toward sustainable transportation through the adoption of NGVs. While NGVs emit significantly less CO<sub>2</sub> than traditional fossil fuel vehicles, retrofitting challenges have resulted in unintended consequences: faulty tailpipes on retrofitted NGVs are disproportionately contributing to urban CH<sub>4</sub> emissions.  

As the world’s largest manufacturer of NGVs, China faces a growing challenge in mitigating these emissions. By using XCH<sub>4</sub> as a proxy, this study contextualizes urbanization’s environmental footprint and emphasizes the critical need for targeted mitigation strategies in densely populated urban centers.

---

## Objectives and Hypotheses

### Objectives

This study aims to address gaps in understanding the spatiotemporal dynamics of urbanization, agriculture, and CH<sub>4</sub> emissions in the YRD by pursuing the following objectives:

- #### Urbanization Dynamics  
  Quantify and characterize the spatiotemporal evolution of urban boundaries across the YRD over two decades (2000, 2010, 2018) using Landsat imagery composites and Global Artificial Impervious Area (GAIA) data.

- #### Agricultural Dynamics  
  Quantify and characterize changes in paddied rice extents within the YRD over the same period (2000, 2010, 2018) by applying a Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm to Landsat imagery composites.

- #### Hotspot Clustering of XCH<sub>4</sub>  
  Identify statistically significant clusters of atmospheric CH<sub>4</sub> emissions (XCH<sub>4</sub>) within the YRD for 2018 using spatial autocorrelation analyses, including hotspot detection.

- #### Historical Projections of XCH<sub>4</sub>  
  Construct a DeepLabv3+ CNN to project historical XCH<sub>4</sub> emission distributions (2000, 2010) based on urban boundaries and paddied rice extents recorded during those years.

### Hypotheses

#### Hypothesis 1  
Atmospheric CH<sub>4</sub> emissions from paddied rice fields are expected to be lower than previously recorded levels. This hypothesis posits that continued urban expansion has led to a significant reduction in agricultural land, including paddied rice fields, resulting in decreased biogenic CH<sub>4</sub> emissions. Trends in atmospheric CH<sub>4</sub> concentrations might closely align with the proportion of agricultural land converted to urban development, underscoring the importance of accurately characterizing urbanization rates along the YRD.

#### Hypothesis 2  
Urban-related atmospheric CH<sub>4</sub> emissions are expected to exceed historical levels. Continued population growth across the YRD has driven an exponential increase in NGV production, a trend compounded by persistent infrastructure deficiencies, such as faulty retrofitting. These factors are anticipated to contribute to higher CH<sub>4</sub> emissions from urban centers, reflecting the region’s evolving transportation and energy demands.

---

## Methodology

This study employs a multi-method approach to address its three core objectives, integrating advanced remote sensing techniques, supervised classification algorithms, and deep learning methods:

- #### Mapping Urban Land Expansion
  Urban boundaries are mapped using Landsat imagery and Global Artificial Impervious Area (GAIA) data, focusing on the YRD’s urbanization dynamics over three temporal milestones: 2000, 2010, and 2018.

- #### Mapping Paddied Rice Distributions
  Paddied rice extents are identified using Landsat imagery and a Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm, which incorporates phenological characteristics and conditional thresholds (e.g., elevation, rice cultivation calendar).

- #### Modeling Historical XCH<sub>4</sub> Emissions
  A Convolutional Neural Network (CNN) built on the DeepLabv3+ architecture is used to predict historical spatial distributions of XCH<sub>4</sub> emissions for 2000 and 2010 based on urban and paddied rice extents.

### Quantifying and Characterizing Spatiotemporal Dynamics of Urbanization (2000, 2010, 2018) Using GAIA Data:

Urbanization is a defining feature of land-use transformation in the YRD, a landscape characterized by rapid population growth and expanding urban landscapes. Projections estimate an additional 2.5 billion individuals will populate urban areas globally in the coming decades (Seto et al., 2011), driving outward urban land expansion at the cost of rural acreage. This process has far-reaching environmental consequences, including soil degradation (Yan et al., 2015) and air pollution (Bereitschaft and Debbage, 2013; Zhu et al., 2020). Understanding the spatiotemporal dynamics of urban development in the YRD requires high-resolution datasets that balance spatial detail (30 meters) with temporal granularity (annual and decadal trends) (Ban et al., 2015; Chen et al., 2016).

#### Challenges in Urbanization Monitoring
Previous large-scale monitoring efforts often struggled to capture both spatial and temporal dynamics at high-resolution. Studies relying on coarse spatial datasets, such as the 500-meter Moderate Resolution Imaging Spectroradiometer (MODIS) product (Friedl et al., 2010), provide insufficient detail for urban growth analysis. Similarly, temporal inconsistencies arise in global urban products like the five-year intervals of Liu et al. (2017) or the 10-year GlobeLand30 classifications (Chen et al., 2016). These limitations hinder accurate assessments of urban land conversion rates and extents, particularly in rapidly evolving regions like the YRD.

#### GAIA Dataset and Methodology
The Global Artificial Impervious Area (GAIA) dataset, introduced by Gong et al. (2019), addresses these challenges by leveraging the full 30-meter resolution Landsat archive (1985–2018) on the Google Earth Engine (GEE) platform. The GAIA dataset automates the mapping of artificial impervious areas, including pavements, roads, sidewalks, and roofs, as proxies for urban boundaries. By bypassing the need for large training datasets, GAIA offers a cost-effective alternative for tracking urban expansion. Its reliance on spectral indices, such as the Normalized Difference Vegetation Index (NDVI), the Modified Normalized Difference Water Index (MNDWI), and shortwave infrared (SWIR) bands, enables robust classification of land cover changes over time.

Algorithms within the GAIA framework mask vegetated regions, water bodies, and bare lands to isolate artificial impervious surfaces. These methods identify urban boundaries with annual updates, leveraging Landsat Thematic Mapper (TM), Enhanced Thematic Mapper Plus (ETM+), and Operational Land Imager (OLI) imagery. For early years (pre-2000), when high-resolution satellite imagery was less available, urban cores were generalized using locally homogeneous pixels with impervious area coverage exceeding 50% (Gong et al., 2019). This approach ensures temporal consistency while maintaining spatial precision.

#### Advantages of GAIA in Urban Mapping

The GAIA dataset enables comprehensive mapping of the YRD’s urban growth by addressing key limitations of earlier approaches:

- #### Temporal Consistency
   GAIA provides annual urban boundary updates over 34 years (1985–2018), capturing both short-term trends and long-term patterns.

- #### Spatial Precision
  By utilizing 30-meter resolution imagery, GAIA ensures detailed representations of urban boundaries, avoiding the coarse spatial granularity of previous products.

- #### Streamlined Automation
  GAIA’s reliance on GEE and spectral indices reduces the time and resource intensity traditionally associated with training sample collection (Yang et al., 2017).

#### Limitations and Considerations

While GAIA’s methodology represents a significant advance, certain limitations persist:

- #### Early-Year Data Availability
  The availability of cloud-free Landsat images was limited in earlier years (e.g., 1985), potentially reducing classification accuracy for these time points.

- #### Spectral Mixing in Urban Areas
    Mixed spectral signatures within 30-meter pixels can complicate classification in spatially complex urban settings (Wang and Li, 2019).

- #### Urban Permanence Assumption
  GAIA assumes that once an area is classified as urban, it remains urban. This disregards processes like afforestation or land-use reversion from urban to rural, which may occur in certain contexts.

#### Relevance to the YRD

Despite these limitations, GAIA is highly suited to analyzing urban expansion in the YRD. Unlike arid or semi-arid regions where impervious area classifications can be challenging due to spectral inconsistencies, the YRD’s humid climate and well-defined urban structures minimize these concerns. The GAIA dataset provides a robust foundation for this study, offering high-resolution insights into urbanization trends across one of the world’s most rapidly developing regions.

#### Open Access and Reproducibility

The GAIA dataset is openly available at [http://data.ess.tsinghua.edu.cn](http://data.ess.tsinghua.edu.cn), ensuring transparency and reproducibility for future research.

### Quantifying and Characterizing Spatiotemporal Dynamics of Paddied Rice (2000, 2010, 2018) Using the PPPM Algorithm:

#### Rice Cultivation and Monitoring
China’s agricultural economy is deeply rooted in its rice cultivation system, characterized by two dominant mixed-cropping practices: single-cropping rice (SCR) and double-cropping rice (DCR). Together, these practices represent the backbone of the nation’s agricultural exports. Capturing the spatial dynamics of rice paddies has historically relied on advanced remote sensing technologies, with phenological signatures – like transplanting and heading periods – serving as crucial indicators of rice distribution.

This study employs Zhu et al.’s (2021) Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm to map paddied rice extents in the Yangtze River Delta (YRD) over two decades (2000–2018). By combining SCR and DCR paddies, the PPPM algorithm quantifies total paddied rice acreage and integrates phenological signals from Landsat TM, ETM+, and OLI imagery. These insights reveal nuanced patterns of agricultural persistence amidst urban expansion.

#### Advancements in Remote Sensing for Rice Mapping
Accurate mapping of paddied rice requires a balance between high temporal and spatial resolution datasets. While MODIS data has been widely employed for its temporal frequency (Boschetti et al., 2014), its coarse 500-meter resolution limits its capacity for detailed analyses of regional rice systems. By contrast, Landsat’s 30-meter spatial resolution provides more granular insights into paddied rice distributions, albeit with reduced temporal coverage (Dao et al., 2015; Xu et al., 2018).

Recent advances, such as Sentinel-2A MSI data, have combined high spatial and spectral resolution for superior crop classification (Löw et al., 2015; Marshall et al., 2015). However, Sentinel-2A’s availability does not align with this study’s 30-year temporal scope. Similarly, synthetic aperture radar (SAR) data offers the advantage of weather-independent imaging (Du et al., 2016; Zhang et al., 2018), but high-resolution SAR data for historical mappings of paddied rice is unavailable for the YRD.

The PPPM algorithm addresses these challenges by leveraging Landsat imagery, enriched with phenological characteristics, to deliver both spatial precision and temporal continuity. This combination is particularly effective for capturing rice systems in spatially heterogeneous regions, such as the intricately embedded agricultural landscapes of the YRD (Dou et al., 2020; Hao et al., 2018; Li et al., 2021).

#### The PPPM Algorithm: Methodology and Features
The PPPM algorithm isolates paddied rice systems by detecting flooding signals unique to rice during transplant phases. Three core vegetation indices – enhanced vegetation index (EVI), normalized difference vegetation index (NDVI), and land surface water index (LSWI) – are utilized to identify areas with high water content and vegetative activity (Xiao et al., 2006). Coupled with Landsat imagery, these indices provide a robust framework for rice mapping.

To minimize misclassification, particularly with aquatic crops like duckweed, the PPPM algorithm incorporates phenological features such as transplanting and heading periods (Zhu et al., 2021). These features enhance the algorithm’s capacity to distinguish rice paddies from other crops, leveraging the biophysical characteristics unique to rice cultivation (Liu et al., 2020).

#### Data Acquisition and Validation
Phenological data, including transplanting and heading dates, were obtained from the Ministry of Agriculture of China. These agriculturally verified thresholds define optimal observation windows for capturing flooding and vegetative phases of rice systems. The PPPM algorithm aligns satellite observations with these timeframes, ensuring accurate mapping of paddied rice extents.

Validation assessments were conducted by comparing paddied rice extents derived from the PPPM algorithm against historical agricultural statistics from the National Bureau of Statistics of China. These provincial-scale datasets (1999–2019) serve as a neutral baseline for evaluating the algorithm’s performance, ensuring consistency with reported paddied rice acreage across Anhui, Zhejiang, Jiangsu, and Shanghai.

#### Limitations and Considerations

While the PPPM algorithm advances rice mapping capabilities, certain limitations persist:

- #### Flooding Signal Ambiguity
  Similar flooding signals from aquatic crops, such as duckweed, may lead to minor misclassifications during transplant phases (Zhu et al., 2021). Incorporating additional phenological features reduces this risk but does not entirely eliminate it.

- #### Phenological Data Dependency
  The success of the algorithm heavily relies on the accuracy of phenological data, particularly for heterogeneous regions with overlapping cropping systems.


Despite these challenges, the PPPM algorithm offers a sophisticated approach to capturing rice dynamics, particularly in a region like the YRD, where agricultural and urban systems intersect. By integrating Landsat imagery with phenological characteristics, the PPPM algorithm bridges gaps in spatiotemporal resolution, providing a framework for mapping paddied rice systems.

### Forecasting Historical XCH<sub>4</sub> Emission Extents Using the Encoder-Decoder Architecture of DeepLabv3+

#### Machine Learning in Remote Sensing
The integration of machine learning, particularly CNNs, with remotely sensed imagery has revolutionized environmental monitoring by enabling automated and scalable image analysis. CNNs, renowned for their ability to learn spatial and spectral patterns in labeled datasets (Krizhevsky et al., 2012; LeCun et al., 1989), are widely utilized for tasks ranging from land-use classification to object detection (Cheng et al., 2016; Mahdianpari et al., 2018). This study employs the DeepLabv3+ architecture, a semantic segmentation model designed for high-resolution image reconstruction, to predict historical XCH<sub>4</sub> emission boundaries for 2000 and 2010 based on urban and paddied rice extents. Using 2018 as the reference year, where all variables (urban extents, paddied rice extents, and XCH<sub>4</sub> emissions) are simultaneously available, the model bridges temporal data gaps to forecast historical CH<sub>4</sub> emissions.

![DeepLabv3+ Architecture for XCH<sub>4</sub> Emission Forecasting](/assets/DeepLabv3+.png)

**<p align="center">Figure 2: DeepLabv3+ Architecture for XCH<sub>4</sub> Emission Forecasting</p>**
This figure illustrates the encoder-decoder architecture of the DeepLabv3+ model used to forecast historical XCH<sub>4</sub> emission boundaries based on urban and paddied rice extents within the YRD. The model takes urban boundaries, paddied rice boundaries, and a satellite basemap as inputs, which are processed by the encoder. The encoder employs Atrous Spatial Pyramid Pooling (ASPP) to capture multi-scale contextual information through parallel convolutional layers with varying dilation rates. The decoder reconstructs segmentation maps by integrating low-level and high-level features via skip connections, enhancing both granularity and spatial resolution in the output. The final segmentation map predicts XCH<sub>4</sub> emission boundaries for the YRD, reconstructed from the spatial distributions of urban and agricultural extents. This architecture demonstrates the model's capacity to learn complex spatial relationships and address temporal gaps in satellite-derived observations.

#### Theoretical Basis for Spatial Image Reconstruction
The encoder-decoder architecture of CNNs aligns with principles of spatial dependency, famously captured in Tobler’s First Law of Geography: "Everything is related to everything else, but near things are more related than distant things." This spatial interdependence enables CNNs to reconstruct missing image patches by leveraging information from neighboring pixels, making them ideal for addressing data availability gaps (He et al., 2022).

In this study, Landsat imagery (30m resolution) containing urban and paddied rice extents for 2000, 2010, and 2018, and S-5P imagery (7 km² resolution) containing XCH<sub>4</sub> data for 2018, are fed into the CNN’s encoder. The decoder reconstructs masked patches, learning latent representations of spatial distributions to predict historical XCH<sub>4</sub> emission boundaries. The scale and translation invariance of CNNs ensures compatibility despite differing resolutions between Landsat and S-5P imagery.

### DeepLabv3+ Architecture and Implementation

DeepLabv3+ was selected for its ability to generate high-resolution segmentation maps by combining multi-scale contextual information and fine-grained details. The architecture’s key components include:

- #### Encoder Module
  Features are extracted using ResNet50 as the backbone network, pre-trained on ImageNet. The encoder utilizes atrous convolutions with varying dilation rates in the Atrous Spatial Pyramid Pooling (ASPP) module to capture multi-scale contextual features.

- #### Decoder Module with Skip Connections
    The decoder refines segmentation maps by merging high-level features from the ASPP module with low-level features from earlier layers of the encoder. Skip connections recover granular details, enhancing object delineation.

- #### Output
  The final segmentation map assigns a class label to each pixel, predicting XCH<sub>4</sub> emission boundaries based on the input features.

### Training Process

The training set (2018 data) consists of 5,000 randomly cropped images spanning Anhui, Zhejiang, and Shanghai. Each cropping includes four layers: urban extents, paddied rice extents, XCH<sub>4</sub> boundaries, and a satellite basemap.

### Testing Process

The testing set, covering Jiangsu, includes 1,000 cropped images. During training, the model minimizes mean squared error (MSE) between predicted and ground-truth XCH<sub>4</sub> boundaries.

### Evaluation

After training, the model is evaluated on the testing set to measure its ability to generalize predictions. Metrics such as MSE assess segmentation accuracy, ensuring the model’s reliability for historical forecasting of CH<sub>4</sub> emissions.

### Application to Forecast Historical XCH<sub>4</sub> Emissions

The DeepLabv3+ model addresses a critical challenge: predicting historical CH<sub>4</sub> emissions (2000, 2010) in the absence of S-5P data. By training on 2018 data, where XCH<sub>4</sub> boundaries align with urban and paddied rice extents, the model extrapolates these relationships to earlier years. Historical urban and paddied rice boundaries are used as proxies to estimate CH<sub>4</sub> emission distributions, producing high-resolution maps of XCH<sub>4</sub> emissions for 2000 and 2010.

### Advantages of DeepLabv3+ for XCH<sub>4</sub> Prediction

#### Granularity and Resolution  
The decoder’s skip connections recover fine-grained details, enabling high-resolution predictions of CH<sub>4</sub> boundaries.

#### Multi-Scale Contextual Understanding  
The ASPP module captures spatial patterns across varying scales, ensuring accurate segmentation of complex inputs.

#### Robust Generalization  
Random masking during training improves the model’s ability to generalize to unseen data, vital for historical forecasting.

#### Scalability  
DeepLabv3+ effectively processes large datasets with diverse input features, maintaining efficiency and accuracy.

### Limitations and Considerations

#### Spatial and Temporal Constraints  
While DeepLabv3+ compensates for missing XCH<sub>4</sub> data, the reliance on 2018 as the training year introduces potential biases tied to that specific temporal snapshot.

#### Resolution Disparities  
The difference in resolution between Landsat (30m) and Sentinel-5P (7 km²) is mitigated by the scale invariance of CNNs but may influence fine-scale accuracy.

#### Data Representation  
Variability in spectral signatures and masking of heterogeneous regions could affect the consistency of reconstructed outputs.

By leveraging the encoder-decoder architecture of DeepLabv3+, this study successfully predicts historical XCH<sub>4</sub> emissions for 2000 and 2010 based on urban and paddied rice boundaries. The integration of high-resolution imagery with advanced semantic segmentation techniques underscores the transformative potential of deep learning in environmental monitoring, offering new avenues for addressing data gaps in spatiotemporal analyses.

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

![Spatial Distribution of XCH<sub>4</sub> Emissions Across the YRD (2018)](/assets/XCH_4_2018.png)

**<p align="center">Figure 16: Spatial Distribution of XCH<sub>4</sub> Emissions Across the YRD (2018)</p>**
This map depicts raw XCH<sub>4</sub> emissions across the YRD for 2018, derived from the Sentinel-5 Precursor’s (S-5P) TROPOspheric Monitoring Instrument (TROPOMI). Emission intensities are represented on a gradient scale, with darker tones signifying higher CH<sub>4</sub> concentrations.  The dataset's spatial resolution of 7 km² enables the identification of CH<sub>4</sub> hotspots and spatial variability across the four provinces. Noticeable clusters of elevated XCH<sub>4</sub> concentrations align with densely urbanized areas such as Shanghai and significant paddied rice regions in northern Anhui and Jiangsu. These spatial patterns provide foundational insights into the interplay between urbanization, agricultural activity, and atmospheric CH<sub>4</sub> emissions, forming a basis for emission monitoring.

![Hotspot Analysis of XCH<sub>4</sub> Emissions Using Spatial Autocorrelation (2018)](/assets/XCH4_2018_Hotspot.png)

**<p align="center">Figure 17: Hotspot Analysis of XCH<sub>4</sub> Emissions Using Spatial Autocorrelation (2018)</p>**
This map presents the results of a hotspot analysis on XCH<sub>4</sub> emissions across the YRD for 2018, derived from Sentinel-5 Precursor’s (S-5P) TROPOspheric Monitoring Instrument (TROPOMI). Using the Getis-Ord Gi* statistic, the analysis identifies statistically significant clusters of high (hotspots) and low (cold spots) XCH<sub>4</sub> values. Hotspots are concentrated in northern Anhui, Jiangsu, and Zhejiang – areas dominated by extensive paddied rice cultivation – and in urban centers like Shanghai. Cold spots, characterized by lower CH<sub>4</sub> emissions, are found in regions with less intensive agricultural or urban activity. This spatial analysis underscores the strong link between elevated XCH<sub>4</sub> concentrations and anthropogenic sources, including emissions from flooded rice paddies and urban activities, such as the proliferation of NGVs. The visualization offers a detailed, spatially explicit understanding of CH<sub>4</sub> distribution, highlighting key sources and sinks.

### Accuracy Assessment: Remotely Sensed Estimates (GAIA, PPPM) vs. Recorded Agricultural Statistics

![Accuracy Assessment: Bar Chart of Algorithms vs Recorded Statistics](/assets/Provincial-Stats.png)

**<p align="center">Figure 18: Comparative Analysis of Remotely Sensed Data and Recorded Agricultural Statistics Across YRD Provinces (2000–2018)</p>**
This figure provides a comparative analysis of urban extents and paddied rice distributions derived from remotely sensed datasets (GAIA for urban areas and PPPM for rice extents) against China’s official agricultural statistics for the YRD provinces: Shanghai, Zhejiang, Anhui, and Jiangsu. The temporal scope spans three key years: 2000, 2010, and 2018.

For paddied rice extents, notable discrepancies emerge in Shanghai and Zhejiang, where the PPPM algorithm underestimates rice distributions. These differences are likely attributed to Shanghai’s high urbanization levels and Zhejiang’s regional complexities, such as mixed-use landscapes and diverse cropping patterns. Anhui and Jiangsu exhibit closer alignment between PPPM-derived rice extents and official statistics, demonstrating the algorithm’s robustness in agriculturally dominated provinces.

In terms of urban areas, GAIA-derived extents consistently show substantial growth across all provinces, particularly in Jiangsu and Shanghai. Between 2000 and 2018, urban areas in Jiangsu expanded more than sixfold, while Shanghai experienced nearly a fivefold increase. These trends underscore the rapid urbanization and infrastructure development driving land-use changes in the region.

This comparative analysis highlights both the strengths and limitations of remote sensing techniques. While these algorithms effectively capture large-scale trends in urban and agricultural land use, they face challenges in highly urbanized or heterogeneous regions. The visualization underscores the dynamic interplay between human development and agricultural land conversion, offering insights for sustainable land-use management and CH<sub>4</sub> emission mitigation strategies in the YRD.

### Forecasting Historical XCH<sub>4</sub> Emissions (2000, 2010) Based on Recorded Urban Extents and Paddied Rice Extents

![XCH<sub>4</sub> Predicted (2000)](/assets/XCH_4_Predicted_2000.png)

**<p align="center">Figure 9.1: XCH<sub>4</sub> Predicted (2000)</p>**

![XCH<sub>4</sub> Predicted (2010)](/assets/XCH_4_Predicted_2010.png)

**<p align="center">Figure 9.2: XCH<sub>4</sub> Predicted (2010)</p>**

---

## Discussion

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

#### Urban Expansion Analysis

The urban growth trajectory across the YRD over nearly two decades highlights rapid and unprecedented land-use changes. In 2000, artificial impervious areas totaled 8,297 km², with the majority concentrated in Jiangsu (3,008 km²), Anhui (2,326 km²), Zhejiang (1,752 km²), and Shanghai (1,211 km²). By 2010, these extents nearly tripled to 24,830 km², driven by dramatic increases in Jiangsu (10,042 km²) and Zhejiang (6,731 km²). Shanghai and Anhui followed with 3,310 km² and 4,748 km², respectively.

By 2018, artificial impervious areas had nearly doubled again, reaching a total of 49,725 km². Jiangsu retained the largest share at 19,430 km², followed by Zhejiang (14,957 km²), Anhui (10,217 km²), and Shanghai (5,121 km²). The cumulative expansion from 2000 to 2018 amounted to an estimated 41,428 km², underscoring the YRD’s position as a global epicenter of urbanization. While these findings provide a quantitative narrative of urban expansion, they must be contextualized within the unique characteristics of each province. For instance, Jiangsu’s substantial urban growth is consistent with its economic development, bolstered by industrial zones and transportation infrastructure. Meanwhile, Shanghai’s expansion, although smaller in absolute terms, represents a near fivefold increase, indicative of its status as a densely urbanized global hub.

This analysis demonstrates the strengths of GAIA-derived urban extents in capturing overarching trends but also highlights the importance of considering provincial scales. Relying solely on impervious area growth may obscure nuanced dynamics, such as land-use policies or urban renewal processes, which merit further investigation.

#### PPPM-Derived Paddied Rice vs. Sown Area of Rice Statistics

In contrast, the PPPM algorithm significantly underestimates paddied rice extents in Shanghai. For example, while PPPM-derived estimates and recorded statistics were nearly identical in 2000 (1,123 km² vs. 1,130 km²), the 2010 and 2018 estimates diverge, with the PPPM algorithm capturing approximately half of the recorded sown area. These underestimations may stem from Shanghai’s small geographic area and high urban density, which complicates spectral classification. Despite these limitations, the alignment between satellite-derived estimates and recorded statistics demonstrates the algorithm’s utility for large-scale assessments.

The algorithm underestimates rice extents in Shanghai and Zhejiang. For Shanghai, PPPM-derived estimates for 2000 were nearly identical to recorded statistics (1,123 km² vs. 1,130 km²), but by 2010 and 2018, these estimates captured only half of the sown area. This discrepancy may result from Shanghai’s small geographic area and high urban density, which complicate spectral classification. Zhejiang also exhibits underestimations, potentially due to its mixed-use landscapes, where agriculture and urbanization overlap, confounding the algorithm.

Despite these limitations, the PPPM algorithm demonstrates significant utility in capturing broad-scale trends. Its accuracy in Anhui and Jiangsu reinforces its application for monitoring agricultural systems, while its challenges in urbanized provinces highlight areas for refinement. Integrating additional datasets, like high-resolution SAR imagery, might enhance the model’s ability to delineate agricultural extents across complex environments.

#### Spatial Assessment of XCH<sub>4</sub> Emission Concentrations

The spatial analysis of XCH<sub>4</sub> concentrations derived from S-5P TROPOMI data reveals statistically significant clustering, as evidenced by a Moran’s Index of 0.46 and a z-score of 276.31. These metrics confirm a less than 1% likelihood of random spatial patterns, underscoring the structured interplay of emission sources. Hotspots of high XCH<sub>4</sub> concentrations are concentrated in agriculturally intensive areas – notably paddied rice fields in northern Anhui, Jiangsu, and northeastern Zhejiang. Urban hotspots, such as central Shanghai and southwestern Zhejiang, further highlight the contribution of urban emissions, potentially linked to NGVs and industrial activities.

A Moran’s Index of 0.46 and a z-score of 276.31 confirm statistically significant clustering of XCH<sub>4</sub> emissions, with less than a 1% likelihood of random spatial patterns. These findings emphasize the spatial interplay between agricultural and urban CH<sub>4</sub> sources, providing a foundational understanding of the YRD’s CH<sub>4</sub> emission dynamics.

The clustering patterns emphasize the dual role of agriculture and urbanization in shaping regional CH<sub>4</sub> emissions. The alignment of hotspot regions with areas of intensive land-use activity corroborates the hypothesis of anthropogenic drivers behind emission patterns. By establishing these spatial relationships, the study provides potential insights for emission mitigation strategies and supports the development of region-specific policies along the YRD.

#### Merging Remote Sensing and Machine Learning
Using the DeepLabv3+ architecture, this study forecasts historical XCH<sub>4</sub> emission boundaries for 2000 and 2010. By inputting urban and paddied rice boundaries from those years, the model generates segmentation maps to predict CH<sub>4</sub> emissions. Although 2018 data serves as the sole reference for training, the model demonstrates strong potential for reconstructing historical CH<sub>4</sub> patterns, paving the way for deeper considerations into the region’s emission trends.

The predicted XCH<sub>4</sub> emission maps align with observed urban and agricultural dynamics, offering valuable context for interpreting S-5P’s 2018 data. This forecasting approach also underscores the potential for integrating satellite imagery with machine learning to address temporal data gaps.

This study exemplifies the transformative potential of merging remote sensing with machine learning frameworks. The successful integration of high-resolution satellite imagery and advanced algorithms demonstrates the viability of autonomous environmental monitoring at regional scales. As open-source data and computational resources continue to expand, future research will likely achieve real-time observations and unprecedented levels of detail. These advancements hold immense promise for climate modeling, emission mitigation strategies, and sustainable land-use planning.

### Potential Limitations and Future Implications

While this study advances the understanding of CH<sub>4</sub> emissions along the YRD, a few limitations warrant discussion:

- #### Data Availability
  Temporal gaps in satellite data, particularly the absence of pre-2018 XCH<sub>4</sub> observations, limit direct validation of historical predictions.

- #### Emission Representation
   China’s agricultural statistics omit contributions from NGV-emitted CH<sub>4</sub>, which may result in underreported national emissions.

- #### Consistency Assumptions
   The model assumes static relationships between land use and CH<sub>4</sub> emissions over time, which may not fully account for evolving emission dynamics.

Future work could integrate additional data sources, such as provincial CH<sub>4</sub> inventories or high-resolution SAR data, to refine predictions and validate historical trends. Enhancements in model architecture, including advanced feature engineering and multi-sensor data fusion, could further improve segmentation accuracy and computational efficiency.

---
## Open-Source Code Availability

The GEE links and the Google Colab Notebook containing the CNN model can be accessed below:

- **GAIA**: [Link to GAIA on Google Earth Engine](https://code.earthengine.google.com/7f2eb1d430833ff194bd4ccd7e724b39)
- **PPPM**: [Link to PPPM on Google Earth Engine](https://code.earthengine.google.com/a850b64d8fe124e6d2fc4c7ac599a09a)
- **Google Colab Jupyter Notebook (DeepLabv3+ Architecture)**: [Colab Notebook Link](https://colab.research.google.com/drive/1HTWfWMo0rU8-jP6z2rowWxtN6Jt4CJPp?usp=sharing)

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
