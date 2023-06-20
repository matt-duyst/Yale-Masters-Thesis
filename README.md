# Masters-Thesis
Urban-Methane Transfers (2000 - 2018): A Convolutional Neural Network (CNN) Approach at Forecasting Historical XCH4 Emissions through Urban Boundaries and Paddied Rice Extents Along China's YRD

# Abstract

This observational study entwines remotely sensed images (Landsat and Sentinel 5-Precursor) with machine learning algorithms – a Global Artificial Impervious Area (GAIA) algorithm and a Phenology and Pixel-Based Paddied Rice Mapping (PPPM) algorithm – to autonomously classify urban boundaries and paddied rice fields along China’s most densely populated, and agriculturally productive region: The YRD. Alter- ations in land-use patterns, i.e., the urbanization process along provinces home to the largest urban centers (like Shanghai), are examined through these dichotomies of urban boundaries and agricultural (paddied rice) boundaries. Landsat images are compiled and coupled with the GAIA algorithm and PPPM algorithm for autonomous classification. An accuracy assessment of the aglorithmically-derived classification of remotely sensed estimations for paddied rice is performed by comparing this study’s observations with with China’s provincial recordings of agricultural statistics of the sown area of rice. The scope of this observational study is further propelled by an added atmospheric dimension: Methane (CH4). Atmospheric CH4 emission concentrations are identified through sources and sinks via the proxy of column-averaged dry air mixing ratio of CH4 (XCH4), captured by the TROPOspheric Monitoring Instrument (TROPOMI) sensor onboard the Sentinel 5-Precursor (S5-P). This work overcomes temporal lag-times apparent in the image acquisition process – Landsat images available for the entire scope of the study (2000 – 2018), but S-5P images confined to the satellite’s launch in late 2017 – through an image segmentation solution of deep learning architectures. A Convolutional Neural Network (CNN) is trained, tested, and evaluated using 2018 data where all variables (urban extents, paddied rice extents, and XCH4 extents) are recorded. The architecture chosen for the CNN is DeepLabv3+, a well-suited model that combines powerful seman- tic segmentation capabilities, multi-scale contextual understanding, an encoder-decoder architecture, and effective feature representation. Ultimately, this CNN learns to predict XCH4 emission boundaries based on recorded urban and paddied rice extents. It is then applied to the years 2000 and 2010 to identify where historical XHC4 emission extents would likely have been based on the recorded urban and paddied rice extents for those years.

# Project Summary

This project aims to monitor patterns in land-use change, namely alterations of spa- tial extents between urban boundaries and paddied rice fields, along the provincial regions of China’s most populated and agriculturally productive landscape: The Yangtze River Delta (YRD). The spatial scale of this project is composed of four dominant provinces – Anhui, Zhejiang, Jiangsu, and Shanghai. At the heart of this research lies investigations of how the unprecedented rate of urbanization across the YRD has impacted agricultural yields (i.e., the country’s largest export, paddied rice), with larger implications towards climate modeling and predictive analytics towards methane (CH4) discussed below. A temporal scale of roughly two decades (2000, 2010, and 2018) has been selected to re- flect surges in urban demographics and urban landscapes that currently consume much of China’s agricultural nexus.

Automated classification of urban boundaries and paddied rice extents are achieved by coupling machine learning algorithms (supervised classification) with Landsat satellite composites (Landsat 5,7, and 8). Urban boundaries and paddied rice extents captured by the Landsat satellite composites for the years 2000, 2010, and 2018 are at a spatial resolution of 30m x 30m. Land-use changes across this study region should be perceived as dichotomous couplets: paddied rice fields (agriculture) versus city boundaries (ur- ban expansion). These spatial binaries have long since been at odds with one another, saturating much of the current YRD literature. What makes this project novel is the addition of an atmospheric dimension – methane (CH4). The columned-averaged dry air mixing ratio of CH4 (XCH4) is captured by the TROPOspheric Monitoring Instrument (TROPOMI) sensor onboard the Sentinel 5-Precursor (S5-P) satellite at a spatial res- olution of 7km2 x 7km2. S5-P was launched into orbit late 2017 (Zhang et al., 2023), limiting data availability and acquisition to the year 2018 (the conclusion of this study’s temporal trajectory).

### Atmospheric CH4 Investigations (Paddied Rice and The Rise of NGVs):

Recent investigations into GHG emissions related to agricultural productivity suggest biogenic sources (i.e., rice paddies) are the largest contributing factor of atmospheric CH4 (G. Zhang et al., 2020) to-date. The country’s keystone agricultural export (paddied rice), or rather methods employed (i.e., flooding) to continually produce the crops at a rate circulating much of the country’s economy, is disproportionately releasing vast quantities of CH4 into the atmosphere. Moreover, this study region produces the largest quantity of Natural Gas Vehicles (NGVs) at the global playing field. In the past two decades, the production of NGVs increased over one thousand percent: In 2000, there were six thousand NGVs in production; by 2017, this number skyrocketed to six million (Da Pan et al., 2020). An overwhelming portion of NGVs are retrofitted with faulty tailpipes that exacerbate atmospheric CH4 emissions. An estimated 196kg of atmospheric CH4 is emitted per retrofitted NGV each year (Hu et al., 2018). NGVs will be used as a proxy for urbanization, and their contribution towards CH4 emissions will be observed at a Fleet-Level.

### XCH4 Emissions (TROPOMI Sentinel 5-Precursor):

From a climate mitigation perspective, CH4 is a pivotal Greenhouse Gas (GHG) when considering climate projection forecasts because its warming potentials are 25-30 times higher than its often-prioritized counterpart, Carbon Dioxide (CO2) (Y. Zhang, et al., 2011). This study utilizes column-averaged dry air mixing ratio of CH4 (XCH4) estimates, captured by the TROPOspheric Monitoring Instrument (TROPOMI) sensor onboard the Sentinel 5-Precursor (S5-P) satellite. XCH4 has proven a useful indica- tor when analyzing spatial concentrations and temporal changes in atmospheric CH4 concentrations (Zhang et al., 2023), capable of identifying sources and sinks of CH4. The collected XCH4 emission distributions are overlayed across the spatially heteroge- nous provincial landscapes along the YRD. XCH4 emissions captured S5-P satellite are recorded at a spatial resolution of 7 x 7 km2.

Spatial clustering and analyses of spatial autocorrelation for XCH4 emissions are considered through incorporation of hot spot analyses (using the Getis-Ord Gi\* statistic to isolate values of high and low spatial clusters) and inclusion of Global Moran’s I (an autocorrelation assessment that considers XCH4 values and location, simultaneously). Statistically significant hot spots of XCH4 emissions are amassed with consideration to neighboring values, i.e., XCH4 emissions are considered statistically significant hot spots if high values are recorded among surrounding high values. This allows the reader to assess XCH4 emissions through the lens of spatial clustering and reduces associations or likelihoods of randomness in XCH4 distribution patterns.

The temporal trajectory of XCH4 emissions quantified in this study are confined by the launch window of S5-P into orbit (2018). Spatial visualizations of atmospheric XCH4 concentrations will follow the provincial-approach employed for urban expansion observations and paddied rice analyses; however, the XCH4 mappings begin where the aforementioned mappings conclude (2018).

### Machine Learning Applications (Encoder-Decoder Architecture of CNNs):

This study compensates for satellite-derived observation lag-times (Landsat images amassed for 2000, 2010, and 2018, and S5-P images amassed for 2018) through implemen- tation of a Convolutional Neural Network (CNN). The architecture of a traditional CNN is composed of two fully convolutional neural networks – an encoder and a decoder – and is commonly applied to image segmentation problems (Long et al., 2015). The encoder works by learning (encoding) representations of a multi-channel image and capturing the associated characteristics across dimensions. The encoder then outputs a score (a heat map) for the associated class or label. Training process involves a fully supervised im- age to segmentation mapping vis-`a-vis minimizing the loss with respect to ground truth observations.

This CNN takes the form of Google’s state-of-the-art semantic segmentation neu- ral network architecture (DeepLabv3+). Improvements for image segmentation tasks by DeepLabv3+ are achieved through two modifications: implementation of atrous convolu- tion with spatial pyramid pooling (ASPP), and a decoder module with skip connections. Multi-scale contextual information of input images are gathered by the model’s ASPP module, assisting for higher accuracy between object delineations. The decoder module with skip connections provides continued refinement for segmentation - achieved through combining low-level and high-level features amongst varying stages of the network - and works to recover granularity (like object boundaries) in the segmentation map.

This encoder-decoder architecture takes in Landsat images of urban boundaries and paddied rice boundaries as geospatial maps. It then outputs the projected XCH4 emission boundaries based on recorded urban extents and paddied rice extents over the domain (the YRD). Lag-times witnessed between image acquisition (Landsat observations captured 2000, 2010, and 2018; S-5P observations captured 2018) poses a missing data problem for the study: XCH4 emissions for the years 2000 and 2010 are not recorded. The encoder- decoder architecture of a CNN is a practical solution for the missing XCH4 emissions data (2000, 2010) because it can learn to project historical XCH4 emissions based on the spatial distributions of urban boundaries and paddied rice boundaries for the years 2000 and 2010.

The CNN takes advantage of the accumulated data for a single year (2018) where spatial boundaries of all three variables of interest are simultaneously captured. The CNN uses 2018 data for testing and validation objectives. Ultimately, this image segmentation process leverages spatial variations demonstrated between its inputs (urban boundary extents and paddied rice extents) and capitalizes on the encoder-decoder architecture of a CNN to predict spatial distributions of historical XCH4 concentrations for the years 2000 and 2010.

### Novelty of Study:

This study discusses its findings through two categories: urban extents and paddied rice extents. Traditionally, these opposing facets (urban versus agriculture) have been analyzed as separate entities. To our knowledge, this is the first attempt in linking the urbanization process with paddied rice distributions to estimate XCH4 emissions along the YRD. Moreover, the emergence of an encoder-decoder architecture capable of predicting historical XCH4 emissions (2000, 2010) based on urban boundaries and paddied rice extents has never been executed. This study represents the first attempt in doing so: a culmination of data fusion techniques, i.e., the combination of varying data structures and data types acquired across different platforms (Landsat, S5-P), with multi-layered pre-processing and post-processing procedures.

### Related-Works and Contributions:

I regard two works of literature (Gong et al., 2019; and Zhu et al., 2021) as pioneering pillars for this observational study. Without individual advancements towards mapping Global Artificial Impervious Areas (GAIA) (Gong et al., 2019), or developing a phenology and pixel-based paddied rice mapping (PPPM) algorithm to isolate paddied rice extents across heterogenous surfaces (Zhu et al., 2021), this observational study would not have come to fruition. Methodologies employed by these two pillaring literatures are the backbone of this study and are discussed in detail below.

### Auxiliary Data:

Historical records of China’s CH4 emissions takes the form of an emissions inventory comprised of paddied rice contributions and urban contributions. The first year of CH4 recorded emissions data is 2000. Paddied rice related atmospheric CH4 emissions is collected from the Global Methane Initiative (GMI), a data compilation project undertaken by the Environmental Protection Agency (EPA) to quantify and project emissions from 1990 – 2050, which categorizes a country by its industry-sector contributions. All values are presented in million metric tons of CO2-eq (MMTCO2e). Data can be downloaded at https://www.globalmethane.org/methane-emissions-data.aspx.

Urban atmospheric CH4 emissions at the provincial-level are considered through the dimensions of population statistics (per 10,000 persons) and proportion of Natural Gas data compiled by the National Bureau of Statistics of China. Population statistics data and Natural Gas data can be downloaded at https://data.stats.gov.cn/english/easyquery.htm?cn=E0103.

Paddied rice related CH4 contributions at the provincial-level were also acquired. Paddied rice atmospheric CH4 emissions are considered through the physical extent of recorded rice fields (the sown area of rice per 1,000 hectares) and can be downloaded at https://data.stats.gov.cn/english/easyquery.htm?cn=E0103.

Climatology data (annual temperature recordings) provided by the Climate Knowledge Portal (World Bank) were also compiled at the provincial-level, and account for the seasonality of paddied rice flooding periods and associated CH4 releases. Annual temperature recordings at the provincial-level can be downloaded at https://climateknowledgeportal.worldbank.org/country/china/climate-data-historical.

### Intellectual Merits and Broader Implications:

These research interests lie at the intersection of environmental monitoring (remote sensing via satellite imagery) and predictive modeling (machine learning algorithms). These interests are personified within this observational study as spatiotemporal analyses of urban expansion, paddied rice extent, and XCH4 concentrations. Quantifying Urban-Methane transfers at this magnitude – regional emissions compiled along China’s most densely populated and agriculturally productive provinces – poses a myriad of real-life applications. Showcasing regional contributions of China’s past, present, and future atmospheric CH4 emissions might capture the gaze of stakeholders near and far, expediting mitigation efforts towards environmentally regulated atmospheric CH4 standards and hindering future emissions along the world’s most densely urbanized city centers: The YRD.

# Background

![](Case_Study.png)

<a name="_page7_x72.00_y72.00"></a>Figure 1.1: Case Study

China houses an estimated 1.44 billion people, positioning itself as the world’s most populated country and accounting for roughly 18.47 percent of the world’s global population (worldometer, 2021). This study investigates historical trends of China’s urbanization process, a land-use change often coinciding with the conversion of agricultural land (i.e., paddied rice), through decadal segmentation over the last twenty years (2000, 2010, 2018). Urban boundaries and paddied rice fields are mapped across four spatially heterogenous provinces: Anhui, Zhejiang, Jiangsu, and Shanghai. Together, these provinces comprise the YRD – home to the largest percentage of the world’s population per region living amongst its urban metropolises (worldometer, 2021).

*Anthology of the YRD: Economic Blossoming and Environmental Positioning*

The emergence of the YRD as China’s current economic center stems from its natural environment and geographic positioning. The Yangtze River flows west to east, its formation beginning near the Qinghai-Tibet plateau, and extends roughly 1.8 million km2 (Zhu et al., 2020). It is China’s largest river and the third largest river in the world (Zhu et al., 2020). Regionally, the YRD is composed of 27 cities, reaches 225,065 km2, and houses a total population of 163 million people (EY Greater China, 2020). The YRD encompasses the world’s most populated city centers and generates nearly 24 percent of China’s total Gross Domestic Product (GDP) (EY Greater China, 2020). The current state of the YRD’s economic success would not be realized without the region’s environmental positioning: a region inseparable from the river and sea. Tracking the historical development of the first cities to emerge within the YRD – namely Yangzhou, Wuxi, Suzhou, Hangzhou, Ningbo, and Yin – allows for a relationship to surface between the region’s climate and its economic success. Yangzhou was at the heart of the country’s salt transport business; Wuxi produced nearly one-fourth of the country’s total rice production; Suzhou and Hangzhou emerged as textile trading havens; and Ningbo and Yin served as the country’s largest trading ports for merchants to gather (Gu et al., 2011). This natural environment construed of river networks propelled the YRD’s multi-level marketing structure (a region capable of

producing unique goods of varying products at vast scales) and shaped a business model that directly altered the urban dynamics within the region. At a national level, towns within the YRD capitalized on this water accessibility – they relied on the river system as a form of transportation for boats to shuttle between markets within each town (Gu et al., 2011).

*Shanghai: The Global Catalyst for YRD’s Succession*

Eventually, continued urbanization along the YRD ascended to global potentials. A single historical event can be attributed for the YRD’s urban succession: the emergence of Shanghai (Gu et al., 2011). Shanghai’s rise as a global enterprise was supported by the city’s location. The signing of the 1842 “Nanjing Treaty” opened the city’s ports and took advantage of its geographic placement within the YRD’s estuary. Shanghai’s environmental advantage gave way to China’s first foreign goods exportation center (Gu et al., 2011). In 1843, the “Treaty of Humen” was signed between China and the United Kingdom. This treaty stimulated endless migration of concessions between China and other global powerhouse players like France and the United States, and welcomed unprecedented rates of prosperity (Gu et al., 2011). Soon after, Shanghai came to epitomize China’s international presence and prosperity; the signing of the 1895 “Treaty of Shimonoseki” solidified the country’s agreement of international factories on Chinese soil (Gu et al., 2011), and Shanghai garnered the reputation of the largest city hub for foreign good exportations.

*The YRD: China’s Agricultural Epitome of Paddied Rice*

The YRD’s marine monsoon subtropical climate induces hot, humid summers, and cool, dry winters. These climactic conditions generate some of the highest volumes of agricultural productivity in all of China. The Yangtze Region harvests 40 percent of China’s total agricultural output (Li et al., 2021). Rice cultivation accounts for 70 percent of the YRD’s total agricultural output (Li et al., 2021). The future trajectory of a globally warmer climate will augment China’s rice productivity as rising temperatures increase the crops’ fertilization process (G. Zhang et al., 2020). Ergo, atmospheric CH4 emissions released from China’s largest agricultural yield is expected to increase in the foreseeable future, contributing the highest volume of CH4 emissions at a global scale.

*Paddied Rice: Biogenic CH4 Emitters*

The continued rise in number of inhabitants and transition towards urban land directly affects the agricultural component of this study: regional distributions of paddied rice fields. In 2020, approximately 167.5 million hectares of China’s land was classified as agricultural fields (National Bureau of Statistics of China, 2021). Nearly 30 million hectares represent paddied rice fields (Jiang et al., 2018). Recent investigations of greenhouse gas (GHG) emissions related to agricultural productivity attribute biogenic sources (i.e., rice paddies) as the largest contributing factor of atmospheric CH4 (G. Zhang et al., 2020). CH4 is a leading GHG with warming potentials 25-30 times higher than Carbon Dioxide (CO2) per unit of weight given a 100-year global warming scenario (Y. Zhang et al., 2011). Agricultural activities account for nearly half of the world’s atmospheric outputs of CH4 (Y. Zhang et al., 2011), with an estimated 25-36 percent of those global atmospheric CH4 emissions directly released through the cultivation of paddied rice fields (G. Zhang et al., 2020).

*NGVs: A Proxy for Urban CH4 Emissions and the Retrofitting Crisis*

Compensating for China’s contribution of global GHG emissions is a country-wide fuel-switch that accentuates the production of NGVs. This sustainable transportation underscores the transition from fossil fuel to clean energy. Over the past two decades, the production of NGVs throughout China has increased over one thousand percent: a reported number of 6,000 NGVs were in production in the year 2000; by 2017, that number skyrocketed to 6.08 million (Da Pan et al., 2020). The energy source of these vehicles is derived through burning natural gas (NG), which produces significantly lower amounts of CO2 and varying traces of air pollutants per unit of heat released (Hu et al., 2018). Although this transition deviates from the burning of fossil fuels like liquid gasoline and coal, which reduces the concentration of CO2 released into the atmosphere, the current state of retrofitting vehicles disproportionately exacerbates the amount of atmospheric CH4 released. An estimated 196kg of atmospheric CH4 emissions are emitted through the tailpipes of retrofitted NGVs each year (Hu et al., 2018). China currently manufactures the largest fleet of NGVs at a global level (Hu et al., 2018). This study suggests surges in CH4 surface concentrations – identified as sources/sinks through the proxy of XCH4 – along urban settings within the YRD to be the result of increased retrofitting of NGVs.

# Objectives, Goals and Hypotheses
### Objectives:

(1): Quantify and characterize spatiotemporal dynamics of urbanization in the past two decades (2000, 2010, 2018) using Landsat imagery composites and Global Artificial Impervious Area (GAIA) data.

(2): Quantify and characterize spatiotemporal dynamics of paddied rice extents in the past two decades (2000, 2010, 2018) using Landsat imagery composites and a phenology and pixel-based paddied rice mapping (PPPM) algorithm.

(3): Perform spatial assessment (hotspot clustering) on raw XCH4 data obtained from S5-P satellite to identify regions of statistical significance (2018).

(4): Implement DeepLabv3+ Model to project historical XCH4 emission distributions (2000, 2010) based on recorded urban boundaries and paddied rice extents for those years.

### Questions Driving Study:

(1): Can remote sensing and supervised machine learning techniques accurately capture spatiotemporal tradeoffs between urban expansion and agricultural extent (paddied rice fields)?

(2): At what rate has urbanization been occurring along the YRD in the past 2 decades? Will the region’s atmospheric CH4 emissions increase or decrease with city expansion patterns?

(3): Can a convolutional neural network (CNN) take in urban boundaries and paddied rice boundaries for training sets and output projected XCH4 emission boundaries along the YRD for the years 2000 and 2010?

### Hypotheses:

*Hypothesis 1:* I speculate paddied rice atmospheric CH4 emissions to be lower than previous historical recordings. The continued development of urban land equates to a general decrease in agricultural crops. Trends in atmospheric CH4 emissions will be analyzed through the percentage of agricultural land lost to urban expansion. This portion of the study relies heavily on accurately predicting the rate of urban development along the YRD.

*Hypothesis 2:* I speculate urban-related atmospheric CH4 emissions to be higher than previous historical recordings. Continued growth of population rates along the YRD equates to a higher demand for transportation among the city centers. Underscoring the exponential progression of NGV fleet production is the continued existence of faulty infrastructure.

# Methodology

This study contains three broad objectives and uses a multi-method approach:

*(1) the creation of urban land expansion mappings via Landsat images and GAIA data.*

*(2) mapping paddied rice distributions using Landsat images and algorithmically identifying rice extents using phenology characteristics (vegetation indices) and conditional thresholds (elevation, rice cultivation calendar).*

*(3) building a Convolutional Neural Network (CNN) to predict historical spatial distributions of XCH4 emissions based on urban boundary extents and paddied rice extents for the years 2000 and 2010.*

### Quantifying and Characterizing Spatiotemporal Dynamics of Urbanization (2000, 2010, 2018) using GAIA Data (Gong et al., 2019):

Tracking the development of the YRD’s urbanization process is realized through the acquisition of Landsat timeseries images (1985 – 2018) and facilitated through Google Earth Engine (GEE). It has been suggested that a population increase of 2.5 billion individuals will occur in the next few decades (Seto et al., 2011). This outward expansion of urban land encroaches on rural acreage and has serious environmental implications, such as soil degradation (Yan et al., 2015) and air pollution (Bereitschaft and Debbage, 2013; Zhu et al., 2020). Monitoring the rate of urban development relies on high resolution spatial data ( 30m) and temporal data (annual, decadal) for regional growth perspectives (Ban et al., 2015; Chen et al., 2016). Previous attempts of large-scale urbanization monitoring fail to capture both dimensions of spatial and temporal data in high resolution. For instance, some studies rely on coarse spatial resolution (e.g., using the 500m Moderate Resolution Imagining Spectroradiometer (MODIS) for land classification (Friedl et al., 2010). Other studies fail to capture temporal consistencies of urbanization, relying on urban land products of broad time captures (e.g., 5-year global urban products from Liu et al. in 2017 or the 10-year GlobeLand30 products from Chen et al. in 2016). The reliance of coarse spatial data and low-resolution temporal data poses issues for accurately identifying the speed and extent of urban land conversion.

Implementing an autonomous system of land cover classification requires large training datasets and large quantities of time and money for data processing (Yang et al., 2017). In 2019, Gong et al. proposed an alternative, low-cost method that avoided reliance on large training sets for land cover sampling: mapping Global Artificial Impervious Areas (GAIA) using the complete archive of 30-m resolution Landsat images (1985 – 2018) on the Google Earth Engine (GEE) platform. The creation of this GAIA dataset is the basis for mapping urban expansion along the YRD.

Human settlements are often characterized by artificial impervious areas – industrial surfaces like pavements (roads, sidewalks, driveways, etc.) and roofs (Gong et al., 2019). Monitoring and quantifying urban expansion along the YRD over the last 30 years is made possible through the development of an annual GAIA dataset that extends 34-years (1985 to 2018), and uses the complete archive of 30-m resolution Landsat timeseries images. Concerns of using GAIA data as a proxy for urban centers stems from performance issues when monitoring arid and semi-arid regions – spectral information is difficult to ascertain when artificial impervious areas are concentrated in dryland regions, resulting in over commissioning of artificial surfaces (Gong et al., 2019). This concern does not pertain to the project’s region of the interest; the YRD is not classified as an arid region teeming with deserts or shrublands.

Algorithms to automatically identify artificial impervious areas by masking out vegetated regions, bodies of water, and bare lands (arid territories) were facilitated on the Google Earth Engine (GEE) platform. The complete Landsat archive obtained to identify artificial impervious areas is comprised of Landsat Thematic Mapper (TM), Enhanced Thematic Mapper Plus (ETM+), and Landsat 8 Operational Land Imager (OLI) data. Early Landsat timeseries data (images captured before the year 2000) can be thought as auxiliary data that supplements higher resolution Google Earth images with greater spatial prose, generalizing urban cores for years pre-dating high resolution Google Earth capabilities. Urban boundaries were identified for these earlier years on the premise of locally homogeneous pixels with averaged percentages of impervious area above 50 percent (Gong et al., 2019). The entirety of Landsat images for a given year were merged using the Normalized Difference Vegetation Index (NDVI) as a baseline (Gong et al., 2019). Once a yearly collection of Landsat images was compiled using this NDVI quality index, artificial impervious areas were identified using training sample units of annual timeseries data that simultaneously incorporated the modified normalized difference water index (MNDWI) and shortwave infrared (SWIR) data (Gong et al., 2019). Compiling the entire Landsat timeseries archive underscores a detachment from previous reliance on the arduous and timely collection of training samples.

General uncertainties surrounding the GAIA dataset built by Gong et al., surface in earlier year observations (i.e., 1985) when Landsat images were of low availability. The quantity of cloud-free Landsat images were weighted for each year (Gong et al., 2019) – with notable increases in cloud-free images when traversing the 30-year timeframe (1985 to 2018). Uncertainties also arise when spectral signatures of 30m Landsat pixels are mixed across spatially complex surfaces, notable in urban settings (Wang and Li, 2019).

Underlying Gong et al.’s GAIA dataset is the assumption that once an area is classified as urban, it remains urban. This logic relies on the established relationship between artificial areas and urban cores, witnessed in regions undergoing rapid rates of urbanization (Gong et al., 2019). Considerations for urban renewal processes like afforestation, or regenerative and reverted land-use changes (i.e., from urban to rural) were disregarded.

This GAIA dataset is open-source and available at http://data.ess.tsinghua.edu.cn.

### Quantifying and Characterizing Spatiotemporal Dynamics of Paddied Rice (2000, 2010, 2018) using PPPM Algorithm (Zhu et al., 2021):

China’s economic standing is partially attributed to the country’s rice-producing potentials: an agricultural system comprised of two domineering mixed-cropping practices - single-cropping rice (SCR) and double-cropping rice (DCR). Algorithms employed to identify signatures of SCR and DCR paddies by coupling the phenology signatures of rice transplanting and heading periods with the entire collection of Landsat TM, Landsat ETM+, and Landsat 8 OLI images (from the duration of 1999 – 2019), were developed in a recent study by Zhu et al., in 2021. This study utilizes Zhu et al.’s phenology and pixel-based paddy rice mapping (PPPM) algorithm and combines SCR paddies with DCR paddies to quantify total paddied rice extent along the YRD over the temporal scope of the past two decades (2000 – 2018).

Previous studies suggests vegetation phenology for precise classification produces higher results than reliance on monotemporal images (Xiao, X et al. 2005; Xiao, X et al. 2006). Countless studies have used timeseries remote sensing data for paddied rice monitoring and distribution mappings (Wardlow, et al. 2008; Pittman, et al. 2010; Peng, et al. 2011; Son, et al. 2013; Qin, et al. 2015; Dong, et al. 2015; Kongtgis, et al. 2015; Zhou, et al. 2016). For example, Moderate Resolution Imaging Spectroradiometer (MODIS) satellite data has been widely employed due to the sensor’s high temporal resolution (Boschetti et al., 2014). Higher accuracy mapping for paddied rice distributions can be realized using Landsat (30m) data, which has higher spatial resolution capabilities but covers smaller regions (Dao et al., 2015; Xu et al., 2018). In more recent studies, the acquisition of Sentinel-2A MSI (Multispectral Instrument) data has been utilized for land classification mappings; unlike the aforementioned sensors, Sentinel-2A MSI offers higher spatial and spectral resolutions, providing greater analysis for crop classification schemas (L¨ow et al., 2015; Marshall et al., 2015; Mariotto et al., 2013). It is suggested the highest accuracy for monitoring land-use/land-cover mappings is achieved using Multiseasonal synthetic aperture radar (SAR) data, due to the sensors ability to capture images regardless of poor weather conditions (Du et al., 2016; Sonia, A. et al., 2014; Zhang, X et al., 2018; Park, S. et al., 2018). Acquisition of high-resolution SAR data for mapping paddied rice is not available for this study’s 30-year timeline.

Statistical data of rice-cropping patterns alone cannot account for spatially heterogenous areas (Liu et al., 2018), such as the regional expanse of intricately embedded surface types characterizing the provincial areas within this study. Advancements in the spatial capabilities of remote sensing, coupled with the temporal accounting of historically archived images, have propelled identification of objects within spatially heterogenous regions – dynamics like paddied rice systems (Dou et al., 2020; Hao et al., 2018; Li et al., 2021). This study identifies paddied rice acreage by coupling remotely sensed images (30m resolution scenes captured by Landsat TM, ETM+, and OLI) with phenological characteristics that coincide with China’s transplanting periods of paddied rice. The combination of satellite imagery with phenological data – vegetation indices and transplanting periods – to map paddied rice crops is recognized as the PPPM algorithm (Zhu et al., 2021). This algorithm isolates paddied rice on the premise of flooding signals (mixed-cropping practices of rice paddies involve flooding during transplant phases) with three key vegetation indices: the enhanced vegetation index (EVI), normalized difference vegetation index (NDVI), and land surface water index (LSWI) (Xiao et al., 2006).

Concerns around using the PPPM algorithm to map paddied rice extents circulate around similarities between flooding signals of other aquatic-based crops, like duckweed, during periods of transplant (Zhu et al., 2021). This study avoids mischaracterization of paddied rice crops by further embedding phenological features (transplanting and heading signatures) into the PPPM algorithm to isolate the biophysical characteristics unique to rice (Liu et al., 2020). Ensuring accuracy of rice-related phenological characteristics is integral for the success of the PPPM algorithm.

Acquisition of rice phenology data – agriculturally verified dates for periods of transplanting and heading – was obtained from the Ministry of Agriculture of China (https://www.zzys.moa.gov.cn/). This phenology data provided thresholds (time periods) of optimum windows for observing the flooding/transplanting and heading phases of the mixed-cropping rice systems along the YRD. Accuracy and validation assessments of paddied rice extents at the provincial scale of this study – Anhui, Zhejiang, Jiangsu, and Shanghai – were verified by comparing agricultural statistics data from the National Bureau of Statistics of China (https://data.stats.gov.cn/). This statistical data embodies a neutral baseline when comparing Landsat observed results through the PPPM algorithm, with historically reported provincial paddied rice extents (1999 – 2019).

### Forecasting Historical XCH4 Emission Extents: The Encoder-Decoder Architecture of DeepLabv3+ for Image Segmentation

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.003.png)

Figure 3.1: DeepLabv3+ Architecture

The intersection of machine learning – supervised machine learning and deep learning architectures, in particular – with remotely sensed images (labeled datasets containing spatial and spectral information of objects) is realized through the encoder-decoder architecture of a CNN. Vast literature supports melding these realms (machine learning efforts for automated performances in environmental monitoring) through convolutional neural networks (CNNs) (Krizhevksy et al., 2012; LeCun et al., 1989; Cheng, G. et al., 2016; Esam, O. et al., 2016; Hu, F. et al., 2015; Mahdianpari, M. et al., 2018; Zhang, M. et al., 2018). This study utilizes the architecture of CNNs for image segmentation; i.e., 2018 data where all variables of the study are captured (urban extents, paddied rice extents, and XCH4 extents) is used for training, testing, and evaluation of semantic performance of predicting XCH4 emissions based on recorded urban boundaries and paddied rice boundaries. This model is then applied to data captured in 2000 and 2010 (where XCH4 emissions are non-existent) and works to forecast XCH4 spatial extents based on the recorded urban boundaries and paddied rice boundaries for those years.

He et al.’s work in 2022 underscored the success of using CNNs as scalable vision learners, with the realization that images are labeled datasets constructed of natural signatures with weighted spatial relationships (He et al., 2022). Logic surrounding the likelihood of spatially-dependent observations originate from Tobler’s First Law of Geography, famously reverberated as: “everything is related to everything else, but near things are more related than distant things.” This theory implies image segmentation and reconstruction efforts of spatial observations – i.e., urban boundary extents, paddied rice extents, and XCH4 extents – is plausible through CNNs because neighboring pixels likely carry spectral and spatial information of their masked counterparts.

The encoder-decoder architecture of CNNs reconstruct missing pixels by randomly masking patches of input images (He et al., 2022) and should be conceptually perceived as a workaround for the lag-time witnessed between satellite (Landsat, S-5P) image availability and acquisition. The compilation of Landsat image archives for mapping urban extents and paddied rice extents follow the temporal trajectory of 2000, 2010, and 2018. The compilation of S-5P image archives for mapping XCH4 extents are confined to the year 2018. The differences in spatial resolution between satellites (Landsat at 30m x 30m and S-5P at 7km2 x 7km2) can be ignored because CNNs are scale and translation invariant.

Landsat images containing information of urban extents and paddied rice extents (2000, 2010, 2018) and S-5P images containing information of XCH4 extents (2018) are fed into the encoder portion (inputs) of the CNN model and used to create training and testing sets. The CNN then performs random masking (removal) of patches (pixels) along the urban and paddied rice inputs for the years of interest. The decoder is designed to reconstruct the urban and paddied rice extents, learning latent representation (He et al., 2022), or spatial distribution, of the inputs through this process of recreating the masked images.

CNNs have been proven successful as scalable models for increased generalized performances of large-volume datasets (He et al., 2022). Images are first segmented in non-overlapping patches. Subsets of these patches are then sampled and masked (removed) from the remaining images. This process of sampling and masking subsets follows a uniform distribution and is repeated iteratively and randomly without replacement (random sampling). The incorporation of a uniform distribution hinders the likelihood of center bias, i.e., the probability of masked patches appearing at an image’s center (He et al., 2022).

The union of randomly sampled subsets with uncharacteristically high masking ratios (the portion of removed patches) eliminates redundancy in the model, generating requirements that cannot be learned simply through extrapolation of nearby patches (He et al., 2022). The encoder inserts patches through a linear function with consideration towards positional embeddings (spatial distributions) and computes subsequent patch sets through a chain of Transformer blocks (He et al., 2022).

The encoder can be interpreted as the image recognition process; the decoder can be interpreted as the image reconstruction process (pre-training). The decoder yields a vector containing pixel estimates that characterize a given patch: a linear projection is then applied to this vector, with output channels equating to pixel estimates for a given patch (He et al., 2022). The output is a reconstructed image of the input (original) image. Differences between the decoder-generated output (the reconstructed image) and input (original) images are calculated through a loss function that calculates the mean squared error (MSE) on the masked patches (He et al., 2022).

The goal of this model is to predict XCH4 emission boundaries for the years 2000 and 2010 based on urban boundaries and paddied rice boundaries. However, data for all variables (urban boundaries, paddied rice boundaries, and XCH4 emissions boundaries) is only present in the year 2018. To train the DeepLabv3+ model, a training set and a testing set was compiled using 2018 data.

The training set contains 5,000 randomly generated image croppings, each consisting of four layers: urban boundaries, paddied rice boundaries, XCH4 boundaries, and a basemap. The training set covers three provinces (Anhui, Shanghai, and Zhejiang), all for the year 2018. Similarly, the testing set contains 1,000 randomly generated image croppings, each consisting of the same four layers, but only covering one province (Jiangsu) for the year 2018. During the training process, the model takes the training set as input and learns to predict the XCH4 emission boundaries based on the urban boundaries and paddied rice boundaries. The loss between the predicted output and the ground truth XCH4 emission boundaries is calculated and backpropagated through the network to update the weights. This process is repeated multiple times until the model has converged and can accurately predict the XCH4 emission boundaries. Once the training process is complete, the model is evaluated on the testing set to see how well it generalizes to new data. The evaluation process involves passing the testing images through the trained network and comparing the predicted XCH4 emission boundaries with the ground truth boundaries (S-5P estimates captured in 2018). The performance metric Mean Squared Error (MSE) is calculated to evaluate the model’s accuracy.

DeepLabv3+ was selected for this study’s objective in forecasting historical XCH4 emission boundaries because its architecture allows for high granularity and increased resolution. Improvements in these object segmentation tasks are witnessed by assigning a class label to each pixel in the image, made possible by combining multi-scale contextual information with low-level features and recovering granularity in details by using skip connections in the decoder module.

*Listed below are high-level steps/objectives of the DeepLabv3+ architecture using Resnet50 as the Backbone:*

1. Input Image: An input image is provided for the network. This image is generally preprocessed and resized to a selected size with normalized pixel values.
2. Backbone Network: The input image is fed into the backbone network (like ResNet50), where features are extracted with varying spatial resolutions. Backbone Networks are usually pre-trained using a large-scale image classification dataslet (Like ImageNet).
3. Atrous Spatial Pyramid Pooling (ASPP): The ASPP module is used to capture multi-scale contextual information from the features extracted by the backbone network. The ASPP module consists of parallel atrous convolutional layers with different dilation rates, which allows the network to capture features at different scales.
4. Decoder with Skip Connections: The output of the ASPP module is upsampled to the original image resolution using a decoder module with skip connections. The skip connections allow the network to combine low-level features from the backbone network with high-level features from the ASPP module, which helps to recover fine-grained details in the segmentation map.
5. Prediction/Outcome: The output of the decoder module is passed through a 1x1 convolutional layer, which generates the final segmentation map. The segmentation map has the same spatial resolution as the input image and assigns a class label to each pixel in the image.

# Results
1. <a name="_page18_x72.00_y81.35"></a><a name="_page18_x72.00_y72.00"></a>YRD Urban Extent Mappings (2000, 2010, 2018): GAIA and Landsat Composites

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.004.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.005.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.006.png)

(a) Urban Extent (2000) (b) Urban Extent (2010) (c) Urban Extent (2018)

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.007.png)

(d) Total Urban Expansion

Figure 4.1: Urban extents based on GAIA dataset and Landsat composites (2000, 2010, 2018).

2. Provincial<a name="_page18_x72.00_y444.51"></a> Urban Extent Mappings (2000, 2010, 2018): GAIA and Landsat Composites

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.008.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.009.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.010.png)

(a) Urban Extent (2000) (b) Urban Extent (2010) (c) Urban Extent (2018)

Figure 4.2: Provincial urban extents based on GAIA dataset and Landsat composites (2000, 2010, 2018).

3. Paddied<a name="_page19_x72.00_y72.00"></a> Rice Extent Mappings (2000, 2010, 2018): PPPM and Landsat Composites

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.011.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.012.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.013.png)

(a) Rice Extent (2000) (b) Rice Extent (2010) (c) Rice Extent (2018)

Figure 4.3: Paddied rice extents based on PPPM algorithm and Landsat composites (2000, 2010, 2018).

4. Urban<a name="_page19_x72.00_y289.18"></a> Extents and Paddied Rice Mappings (2000, 2010, 2018)

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.014.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.015.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.016.png)

1) Total Extents (2000) (b) Total Extents (2010) (c) Total Extents (2018)

Figure 4.4: Overlaying urban expansion with paddied rice extents: Landsat composites coupled with GAIA and PPPM (2000, 2010, 2018).

5. XCH4<a name="_page20_x72.00_y72.00"></a> Emission Extents: S5-P TROPOMI Measurements (2018)

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.017.png)

2) Spatial Autocorrelation: ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.018.png)Hotspot Analysis of XCH4

(a) Raw XCH4 emissions emissions

Figure 4.5: S-5P TROPOMI estimated XCH4 emissions (left) and Spatial Autocorrelation assessment (right). XCH4 estimates captured by S-5P are represented in parts per billion (ppb) and range from 1650 to 1950. Estimates captured over this study area for the year 2018 have a range in intensity between 1805 and 1910.

6. Comparing<a name="_page20_x72.00_y343.48"></a> Remotely Sensed Data with China’s Recorded Estimates: Urban Extents (GAIA), and Paddied Rice Extents (PPPM vs China’s Recorded Agricultural Statistics)

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.019.png)

Figure 4.6: Provincial comparison of remotely sensed data and China’s recorded statistics (2000 to 2018).

7. CNN-Forecasted<a name="_page21_x72.00_y72.00"></a> Historical XCH4 Emissions (2000, 2010) Based on Recorded Urban Extents and Paddied Rice Extents

![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.018.png) ![](Aspose.Words.569e3dbb-945b-44d9-a993-3db3ff2ba5e2.018.png)

(a) XCH4 Predicted (b) XCH4 Predicted Boundaries (2000) Boundaries (2010)

Figure 4.7: DeepLabV3+ estimated historical XCH4 emission boundaries for the years 2000 and 2010, based on recorded urban and paddied rice extents in the year 2018.

# Discussion
1. <a name="_page22_x72.00_y81.35"></a><a name="_page22_x72.00_y72.00"></a>Accuracy Assessment: Remotely sensed estimations versus China’s recorded estimations

Table 1: Provincial Comparison (2000 - 2018) by km2: Urban Extent (GAIA), Paddied Rice Extent (PPPM), and China’s Recorded Agricultural Statistics (Sown Area)



|Province|UrbanExtent (GAIA)|Paddi|ed Rice (PPPM)|Sown Are|aof Rice|
| - | - | - | - | - | - |
|Shanghai (2000)|1,211||1,123||1,130|
|Zhejiang (2000)|1,752||5,983||10,290|
|Anhui (2000)|2,326||19,651||21,490|
|Jiangsu (2000)|3,008||15,505||22,090|
|Shanghai (2010)|3,310||577||1,210|
|Zhejiang (2010)|6,731||6,028||8,220|
|Anhui (2010)|4,748||22,977||23,390|
|Jiangsu (2010)|10,042||18,825||22,240|
|Shanghai (2018)|5,121||536||1,040|
|Zhejiang (2018)|14,957||4,463||6,510|
|Anhui (2018)|10,217||17,430||25,450|
|Jiangsu (2018)|19,430||16,038||22,150|

### Urban Expansion Analysis:

In the year 2000, the YRD’s accumulation of artificial impervious areas (i.e., urban extent) was 8,297 km2. The majority of this urban extent was accounted by Jiangsu (3,008 km2), followed by Anhui (2,326 km2), Zhejiang (1,752 km2) and Shanghai (1,211 km2).

Over the span of a decade (2010), the YRD’s accumulation of artificial impervious areas (i.e., urban extent) nearly tripled for a total estimated area of 24,830 km2. The majority of this urban extent was again accounted by Jiangsu (10,042 km2), but this time followed by Zhejiang (6,731 km2), Anhui (4,748 km2) and Shanghai (3,310). Jiangsu and Shanghai’s urban extents followed the YRD’s trajectory of a tripling in size. Anhui’s urban extent doubled in size. Zhejiang experienced an urban expansion rate 6 times greater than the recorded extent for the year 2000.

Within the same decade (2018), the YRD’s accumulation of artificial impervious areas (i.e., urban extent) nearly doubled for a total estimated area of 49,725 km2. A pattern persists with Jiangsu accounting for the majority of this urban extent (19,430 km2), again followed by Zhejiang (14,957 km2), Anhui (10,217 km2) and Shanghai (5,121 km2). Jiangsu, Anhui, and Zhejiang all experienced nearly a doubling (or more than a doubling) in urban extents.

Urban expansion rates along the YRD (defined in this study through artificial impervious areas) happened at unparalleled rates. From 2000 to 2010, the change in urban area (urban expansion) autonomously recorded by coupling Landsat composites with GAIA was 16,533 km2. From 2010 to 2018, the change in urban area recorded was 24,895 km2. The total rate of urban expansion for the scope of this study (2000 to 2018) was 41,428 km2.

I’d like to remind the reader that objectively analyzing urban expansion according to artificial area growth recordings leads to slight biases in perspectives. A provincial scale (the total area amassed for a particular province) should also be taken into account for a more insightful perspective of total urban extents.

### PPPM-Derived Paddied Rice vs. China’s Recorded Statistics:

Comparing this observational study’s remotely-sensed paddied rice extents with China’s recorded statistics of the sown area of rice reinforces the success and continuation of coupling high-resolution satellite imagery (Landsat) with supervised classification algorithms (PPPM) for autonomous classifications. The PPPM algorithm does a remarkable job of capturing generalized trends in the spatial distributions of paddied rice fields along the YRD; however, there are apparent discrepancies when comparing province to province. The highest concentrations of paddied rice fields for both the PPPM-derived extents and the country’s recorded agricultural statistics are Anhui and Jiangsu. These two provinces also have the closest estimations when comparing PPPM-derived extents and the sown area of rice extents. However, the PPPM algorithm appears to grossly underestimate paddied rice extents for one province in particular: Shanghai.

In the year 2000, the PPPM-derived paddied rice extents and China’s recorded statistics of the sown area of rice were nearly identical (1,123 km2 and 1,130 km2, respectively). But in the years 2010 and 2018, the PPPM-derived estimates of paddied rice extents are about half of what China recorded as the sown area of rice fields. Perhaps these underestimations are due to the province’s smaller area (the smallest extent of all provinces) and large concentration of urban centers. Regardless, the overall comparison between satellite observations, advanced by machine learning algorithms, with China’s recorded statistics are within close proximity for large-scale observations.

### Spatial Assessment of XCH4 Emission Concentrations:

A spatial assessment of the S-5P TROPOMI estimated XCH4 emission concentrations showcased a positive correlation between XCH4 emissions, urban extents, and paddied rice extents. However, the largest driver (hotspots of intense positive correlations) appear to be paddied rice fields, particularly in northern regions of Anhui and Jiangsu, and northeast regions of Zhejiang. Smaller hotspots of positively correlated XCH4 emissions appear within central Shanghai and southwest regions of Zhejiang.

A Moran’s Index of 0.46 was recorded when computing the spatial autocorrelation assessment for XCH4 emissions (2018). Positive autocorrelation is apparent. A z-score of 276.31 was further generated, indicating less than a 1 percent likelihood that XCH4 emission clustered spatial patterns are the result of random chance.

## The Interplay of Remote Sensing and Machine Learning

Historical XCH4 emission boundaries for the years 2000 and 2010 were predicted through the architecture of this study’s trained DeepLabv3+ model. The respective urban boundaries and paddied rice boundaries for each target year were inputted into the trained model. Segmentation maps were then generated to delineate the predicted XCH4 emission boundaries for the target years (2000, 2010).

The model’s predicted XCH4 emission boundaries were analyzed to identify historical trends and spatial distribution patterns along the YRD. Advances in the model’s accuracy and validation efforts would incorporate a comparison between the model’s predicted XCH4 emissions with available reference data (provincial estimates of Methane emissions) or previous models that have worked on this area to identify Methane concentrations (none to our knowledge exist). Insights and interpretations regarding the historical XCH4 emission patterns may foreshadow potential drivers for 2018 S-5P estimates, and unveil implications for emission control and mitigation strategies. Potential limitations of this study are addressed in full - namely data availability (the lag-time between satellite launches), uncertainties in historical records (China has not released provincial-estimated Methane recordings, nor and does it include NGV-emitted Methane concentrations in their reportings, implying false country-level estimations). There is also an assumption of consistent emission patterns over time.

The hope of this study is to enlighten the viewer on the prolific capabilities of merging satellite observations (images) with machine learning frameworks (supervised classification algorithms and deep learning architectures). As both realms advance and new technologies emerge, the potentials for blending and dabbling between architectures and algorithms will catapult to unseen heights. The boom in big data and open-source availability of code will propel techniques used in this observational study and advance new techniques that will capture intricacies at greater resolutions and faster computational run-times. In-real-time observations and data acquisition is upon us.

## Open-Source Code Availability:

GEE link(s) and the Google Colab Notebook containing the CNN model can be followed below.

GAIA: https://code.earthengine.google.com/7f2eb1d430833ff194bd4ccd7e724b39 PPPM: https://code.earthengine.google.com/a850b64d8fe124e6d2fc4c7ac599a09a Google Colab Jupyter Notebook (DeepLabv3+ Architecture):

https://colab.research.google.com/drive/1HTWfWMo0rU8- jP6z2rowWxtN6Jt4CJPp?usp=sharing

# References

<a name="_page26_x72.00_y72.00"></a>Aitken, Kyle, et al. “Understanding How Encoder-Decoder Architectures Attend.” Advances in Neural Information Processing Systems, edited by M. Ranzato et al., vol. 34, Curran Associates, Inc., 2021, pp. 22184–95, https://proceedings.neurips.cc/paper/2021/file/ba3c736667394d5082f86f28aef38107- Paper.pdf.

Asilo, Sonia, et al. “Complementarity of Two Rice Mapping Approaches: Characterizing Strata Mapped by Hypertemporal MODIS and Rice Paddy Identification Using Multitemporal SAR.” Remote Sensing, vol. 6, no. 12, Dec. 2014, pp. 12789–814. DOI.org (Crossref), https://doi.org/10.3390/rs61212789.

Ball, John E., et al. “Comprehensive Survey of Deep Learning in Remote Sensing: Theories, Tools, and Challenges for the Community.” Journal of Applied Remote Sensing, vol. 11, no. 04, Sept. 2017, p. 1. DOI.org (Crossref), https://doi.org/10.1117/1.JRS.11.042609.

Ban, Yifang, et al. “Global Land Cover Mapping Using Earth Observation Satellite Data: Recent Progresses and Challenges.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 103, May 2015, pp. 1–6. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2015.01.001.

Bereitschaft, Bradley, and Keith Debbage. “Urban Form, Air Pollution, and CO 2 Emissions in Large U.S. Metropolitan Areas.” The Professional Geographer, vol. 65, no. 4, Nov. 2013, pp. 612–35. DOI.org (Crossref), https://doi.org/10.1080/00330124.2013.799991.

Bloom, A. Anthony, et al. “Large-Scale Controls of Methanogenesis Inferred from Methane and Gravity Spaceborne Data.” Science, vol. 327, no. 5963, Jan. 2010, pp. 322–25. DOI.org (Crossref), https://doi.org/10.1126/science.1175176.

Boschetti, Mirco, et al. “Comparative Analysis of Normalised Difference Spectral Indices Derived from MODIS for Detecting Surface Water in Flooded Rice Cropping Systems.” PLoS ONE, edited by Guy J.-P. Schumann, vol. 9, no. 2, Feb. 2014, p. e88741. DOI.org (Crossref), https://doi.org/10.1371/journal.pone.0088741.

Chen, XueHong, et al. “Global Mapping of Artificial Surfaces at 30-m Resolution.” Science China Earth Sciences, vol. 59, no. 12, Dec. 2016, pp. 2295–306. DOI.org (Crossref), https://doi.org/10.1007/s11430-016-5291-y.

Cheng, G. et al. “Learning rotation-invariant convolutional neural networks for object detection in VHR optical remote sensing images.” IEEE Trans. Geosci. Remote Sens. 2016, 54, 7405–7415. (Crossref), https://ieeexplore.ieee.org/document/7560644.

China Banking News. “Yangtze River Delta’s GDP Reached USD 3.35 Trillion in 2019, Accounts for Nearly Quarter of National Total.” China Banking News, Jun. 2020. (Crossref), https://www.chinabankingnews.com/2020/06/07/yangtze-river-deltas-

gdp-reached-3-35-trillion-yuan-in-2019-accounts-for-nearly-quarter-of-national-total/.

Da Pan, et al. “Methane Emissions from Natural Gas Vehicles in China.” Nature Communications, vol. 11, no. 1, Dec. 2020, p. 4588. DOI.org (Crossref), https://doi.org/10.1038/s41467-020-18141-0.

Dao, Phuong, and Yuei-An Liou. “Object-Based Flood Mapping and Affected Rice Field Estimation with Landsat 8 OLI and MODIS Data.” Remote Sensing, vol. 7, no. 5, Apr. 2015, pp. 5077–97. DOI.org (Crossref), https://doi.org/10.3390/rs70505077.

Dong, Jinwei, et al. “Tracking the Dynamics of Paddy Rice Planting Area in 1986–2010 through Time Series Landsat Images and Phenology-Based Algorithms.” Remote Sensing of Environment, vol. 160, Apr. 2015, pp. 99–113. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2015.01.004.

Dosovitskiy, Alexey, et al. An Image Is Worth 16x16 Words: Transformers for Image Recognition at Scale. arXiv:2010.11929, arXiv, 3 June 2021. arXiv.org, http://arxiv.org/abs/2010.11929.

Dou, Yujie, et al. “Mapping High Temperature Damaged Area of Paddy Rice along the Yangtze River Using Moderate Resolution Imaging Spectroradiometer Data.” International Journal of Remote Sensing, vol. 41, no. 2, Jan. 2020, pp. 471–86. DOI.org (Crossref), https://doi.org/10.1080/01431161.2019.1643936.

Du, Lin, et al. “Estimation of Rice Leaf Nitrogen Contents Based on Hyperspectral LIDAR.” International Journal of Applied Earth Observation and Geoinformation, vol. 44, Feb. 2016, pp. 136–43. DOI.org (Crossref), https://doi.org/10.1016/j.jag.2015.08.008.

Esam, Othman, et al. “Using convolutional features and a sparse autoencoder for land-use scene classification.” International Journal of Remote Sensing, 2016, 37:10, 2149 2167, DOI.org (Crossref): 10.1080/01431161.2016.1171928.

EY Greater China. “How is the Yangtze River Delta driving China’s economic development?”

EY, Apr. 2020. (Crossref), https://www.ey.com/en-cn/china-opportunities/how-is- yangtze-river-delta-driving-china-economic-development.

Feichtenhofer, Christoph, et al. Masked Autoencoders As Spatiotemporal Learners. arXiv:2205.09113, arXiv, 21 Oct. 2022. arXiv.org, http://arxiv.org/abs/2205.09113.

Frankenberg, C. et al. “Assessing methane emissions from global space-borne observations.” Science, 308, 1010–1014, 2005.

Friedl, Mark A., et al. “MODIS Collection 5 Global Land Cover: Algorithm Refinements and Characterization of New Datasets.” Remote Sensing of Environment, vol. 114, no. 1, Jan. 2010, pp. 168–82. DOI.org (Crossref),

https://doi.org/10.1016/j.rse.2009.08.016.

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

Liu, Dandan, et al. “Annual Large-Scale Urban Land Mapping Based on Landsat Time Series in Google Earth Engine and OpenStreetMap Data: A Case Study in the Middle Yangtze River Basin.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 159, Jan. 2020, pp. 337–51. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2019.11.021.

Liu, Dandan, and Nengcheng Chen. “Satellite Monitoring of Urban Land Change in the Middle Yangtze River Basin Urban Agglomeration, China between 2000 and 2016.” Remote Sensing, vol. 9, no. 11, Oct. 2017, p. 1086. DOI.org (Crossref), https://doi.org/10.3390/rs9111086.

Liu, Mengyao, et al. “A New Divergence Method to Quantify Methane Emissions Using Observations of Sentinel-5P TROPOMI.” Geophysical Research Letters, vol. 48, no. 18, Sept. 2021. DOI.org (Crossref), https://doi.org/10.1029/2021GL094151.

Liu, Xiaoping, et al. “High-Resolution Multi-Temporal Mapping of Global Urban Land Using Landsat Images Based on the Google Earth Engine Platform.” Remote Sensing of Environment, vol. 209, May 2018, pp. 227–39. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2018.02.055.

L¨ow, Fabian, et al. “Decision Fusion and Non-Parametric Classifiers for Land Use Mapping Using Multi-Temporal RapidEye Data.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 108, Oct. 2015, pp. 191–204. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2015.07.001.

Luus, F.P.S, et al. “Multiview deeplearning for land-use classification.” IEEE Geosci. Remote Sens. Lett. 2015, 12, 2448–2452. (CrossRef), https://ieeexplore.ieee.org/document/7307121.

M. Boschetti, et al. “Multi-year monitoring of rice crop phenology through time

series analysis of MODIS images.” International Journal of Remote Sensing, 2009, 30:18, 4643 4662, DOI.org (Crossref), 10.1080/01431160802632249.

Mahdianpari, Masoud, et al. “Very Deep Convolutional Neural Networks for Complex Land Cover Mapping Using Multispectral Remote Sensing Imagery.” Remote Sensing, vol. 10, no. 7, July 2018, p. 1119. DOI.org (Crossref), https://doi.org/10.3390/rs10071119.

Mariotto, Isabella, et al. “Hyperspectral versus Multispectral Crop-Productivity Modeling and Type Discrimination for the HyspIRI Mission.” Remote Sensing of Environment, vol. 139, Dec. 2013, pp. 291–305. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2013.08.002.

Marmanis, D.; Datcu, M.; Esch, T.; Stilla, U. Deep learning earth observation classification using imageNet pretrained networks. IEEE Geosci. Remote Sens. 2016, 13, 105–109. (CrossRef), https://ieeexplore.ieee.org/document/7342907.

Marshall, Michael, and Prasad Thenkabail. “Advantage of Hyperspectral EO-1 Hyperion over Multispectral IKONOS, GeoEye-1, WorldView-2, Landsat ETM+, and MODIS Vegetation Indices in Crop Biomass Estimation.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 108, Oct. 2015, pp. 205–18. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2015.08.001.

National Bureau of Statistics of China. ”Acreage of Sown or Harvested Land of Farm Crops in China from 1980 to 2021 (in Million Hectares).” Statista, Statista Inc., 7 Jul 2022, https://www.statista.com/statistics/275574/acreage-of-sown-or-harvested-land-of- farm-crops-in-china/.

Park, Seonyoung, et al. “Classification and Mapping of Paddy Rice by Combining Landsat and SAR Time Series Data.” Remote Sensing, vol. 10, no. 3, Mar. 2018, p. 447. DOI.org (Crossref), https://doi.org/10.3390/rs10030447.

Peng, Dailiang, et al. “Detection and Estimation of Mixed Paddy Rice Cropping Patterns with MODIS Data.” International Journal of Applied Earth Observation and Geoinformation, vol. 13, no. 1, Feb. 2011, pp. 13–23. DOI.org (Crossref), https://doi.org/10.1016/j.jag.2010.06.001.

Peng, Shushi, et al. “Inventory of Anthropogenic Methane Emissions in Mainland China from 1980 to 2010.” Atmospheric Chemistry and Physics, vol. 16, no. 22, Nov. 2016, pp. 14545–62. DOI.org (Crossref), https://doi.org/10.5194/acp-16-14545-2016.

Pittman, Kyle, et al. “Estimating Global Cropland Extent with Multi-Year MODIS Data.” Remote Sensing, vol. 2, no. 7, July 2010, pp. 1844–63. DOI.org (Crossref), https://doi.org/10.3390/rs2071844.

Qin Y, et al. “Mapping paddy rice planting area in cold temperate climate region through analysis of time series Landsat 8 (OLI), Landsat 7 (ETM+) and MODIS imagery.” ISPRS Journal Photogrammetry and Remote Sensing, 2015 Jul;105:220-233. DOI.org (Crossref), https://pubmed.ncbi.nlm.nih.gov/27695195.

Seto, Karen C., et al. “A Meta-Analysis of Global Urban Land Expansion.” PLoS ONE, edited by Juan A. Anel,˜ vol. 6, no. 8, Aug. 2011, p. e23777. DOI.org (Crossref), https://doi.org/10.1371/journal.pone.0023777.

Son, Nguyen-Thanh, et al. “A Phenology-Based Classification of Time-Series MODIS Data for Rice Crop Monitoring in Mekong Delta, Vietnam.” Remote Sensing, vol. 6, no. 1, Dec. 2013, pp. 135–56. DOI.org (Crossref), https://doi.org/10.3390/rs6010135.

Song, Hongqing, et al. “Energy Consumption and Greenhouse Gas Emissions of Diesel/LNG Heavy-Duty Vehicle Fleets in China Based on a Bottom-up Model Analysis.” Energy, vol. 140, Dec. 2017, pp. 966–78. DOI.org (Crossref), https://doi.org/10.1016/j.energy.2017.09.011.

Thenkabail, P.S. “Mapping rice areas of South Asia using MODIS multitemporal data.” J. Appl. Remote Sens. 2011, 5, 863–871.

Wardlow, Brian D., and Stephen L. Egbert. “Large-Area Crop Mapping Using Time- Series MODIS 250 m NDVI Data: An Assessment for the U.S. Central Great Plains.” Remote Sensing of Environment, vol. 112, no. 3, Mar. 2008, pp. 1096–116. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2007.07.019.

Worldometer. China Statistics. https://www.worldometers.info/world-population/china-population/ (2021).

Xiao, Xiangming, Stephen Boles, Steve Frolking, et al. “Mapping Paddy Rice Agriculture in South and Southeast Asia Using Multi-Temporal MODIS Images.” Remote Sensing of Environment, vol. 100, no. 1, Jan. 2006, pp. 95–113. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2005.10.004.

Xiao, Xiangming, Stephen Boles, Jiyuan Liu, et al. “Mapping Paddy Rice Agriculture in Southern China Using Multi-Temporal MODIS Images.” Remote Sensing of Environment, vol. 95, no. 4, Apr. 2005, pp. 480–92. DOI.org (Crossref), https://doi.org/10.1016/j.rse.2004.12.009.

Xu, Xinjie, et al. “Evaluation of One-Class Support Vector Classification for Mapping the Paddy Rice Planting Area in Jiangsu Province of China from Landsat 8 OLI Imagery.” Remote Sensing, vol. 10, no. 4, Apr. 2018, p. 546. DOI.org (Crossref), https://doi.org/10.3390/rs10040546.

Yan, Yan, et al. “Impacts of Impervious Surface Expansion on Soil Organic Carbon

- a Spatially Explicit Study.” Scientific Reports, vol. 5, no. 1, Dec. 2015, p. 17905. DOI.org (Crossref), https://doi.org/10.1038/srep17905.

Yang, Di, et al. “Open Land-Use Map: A Regional Land-Use Mapping Strategy for

Incorporating OpenStreetMap with Earth Observations.” Geo-Spatial Information Science, vol. 20, no. 3, July 2017, pp. 269–81. DOI.org (Crossref), https://doi.org/10.1080/10095020.2017.1371385.

Zhang, Ce, Xin Pan, et al. “A Hybrid MLP-CNN Classifier for Very Fine Resolution Remotely Sensed Image Classification.” ISPRS Journal of Photogrammetry and Remote Sensing, vol. 140, June 2018, pp. 133–44. DOI.org (Crossref), https://doi.org/10.1016/j.isprsjprs.2017.07.014.

Zhang, Geli, Xiangming Xiao, et al. “Fingerprint of Rice Paddies in Spatial–Temporal Dynamics of Atmospheric Methane Concentration in Monsoon Asia.” Nature Communications, vol. 11, no. 1, Dec. 2020, p. 554. DOI.org (Crossref), https://doi.org/10.1038/s41467-019-14155-5.

Zhang, Jiaxing, et al. “The Spatial and Temporal Distribution Patterns of XCH4 in China: New Observations from TROPOMI.” Atmosphere, vol. 13, no. 2, Jan. 2022, p. 177. DOI.org (Crossref), https://doi.org/10.3390/atmos13020177.

Zhang, Meng, Hui Lin, et al. “Mapping Paddy Rice Using a Convolutional Neural Network (CNN) with Landsat 8 Datasets in the Dongting Lake Area, China.” Remote Sensing, vol. 10, no. 11, Nov. 2018, p. 1840. DOI.org (Crossref), https://doi.org/10.3390/rs10111840.

Zhang, Xiaoyang, et al. “Monitoring Vegetation Phenology Using MODIS.” Remote Sensing of Environment, vol. 84, no. 3, Mar. 2003, pp. 471–75. DOI.org (Crossref), https://doi.org/10.1016/S0034-4257(02)00135-9.

Zhang, Xin, Bingfang Wu, et al. “Mapping Up-to-Date Paddy Rice Extent at 10 M Resolution in China through the Integration of Optical and Synthetic Aperture Radar Images.” Remote Sensing, vol. 10, no. 8, July 2018, p. 1200. DOI.org (Crossref), https://doi.org/10.3390/rs10081200.

Zhang, Y., et al. “Quantifying Methane Emissions from Rice Paddies in Northeast China by Integrating Remote Sensing Mapping with a Biogeochemical Model.” Biogeosciences, vol. 8, no. 5, May 2011, pp. 1225–35. DOI.org (Crossref), https://doi.org/10.5194/bg-8-1225-2011.

Zhang, Yuan, et al. “Characterizing Spatiotemporal Dynamics of Methane Emissions from Rice Paddies in Northeast China from 1990 to 2010.” PLoS ONE, edited by Julian Clifton, vol. 7, no. 1, Jan. 2012, p. e29156. DOI.org (Crossref), https://doi.org/10.1371/journal.pone.0029156.

Zhou, Feng, et al. “A New High-Resolution N 2 O Emission Inventory for China in 2008.” Environmental Science Technology, vol. 48, no. 15, Aug. 2014, pp. 8538–47. DOI.org (Crossref), https://doi.org/10.1021/es5018027.

Zhou, Yuting, et al. “Mapping Paddy Rice Planting Area in Rice-Wetland Coexistent Areas through Analysis of Landsat 8 OLI and MODIS Images.” International Journal of Applied Earth Observation and Geoinformation, vol. 46, Apr. 2016, pp. 1–12. DOI.org (Crossref), https://doi.org/10.1016/j.jag.2015.11.001.

Zhu, Lihong, et al. “Detection of Paddy Rice Cropping Systems in Southern China with Time Series Landsat Images and Phenology-Based Algorithms.” GIScience Remote Sensing, vol. 58, no. 5, July 2021, pp. 733–55. DOI.org (Crossref), https://doi.org/10.1080/15481603.2021.1943214.

Zhu, Min, et al. “Population and Economic Projections in the Yangtze River Basin Based on Shared Socioeconomic Pathways.” Sustainability, vol. 12, no. 10, May 2020, p. 4202. DOI.org (Crossref), https://doi.org/10.3390/su12104202.
31
