article_title:: Street Network Models and Indicators for Every Urban Area in the World
article_author:: Boeing
article_date:: 2021
citekey:: boeingStreetNetworkModels2021
tags:: Article, Urban science
status::

- Abstract:
	- Cities worldwide exhibit a variety of street network patterns and configurations that shape human mobility, equity, health, and livelihoods. This study models and analyzes the street networks of every urban area in the world, using boundaries derived from the Global Human Settlement Layer. Street network data are acquired and modeled from OpenStreetMap with the open-source OSMnx software. In total, this study models over 160 million OpenStreetMap street network nodes and over 320 million edges across 8,914 urban areas in 178 countries, and attaches elevation and grade data. This article presents the study’s reproducible computational workflow, introduces two new open data repositories of ready-to-use global street network models and calculated indicators, and discusses summary findings on street network form worldwide. It makes four contributions. First, it reports the methodological advances of this open-source workflow. Second, it produces an open data repository containing street network models for each urban area. Third, it analyzes these models to produce an open data repository containing street network form indicators for each urban area. No such global urban street network indicator data set has previously existed. Fourth, it presents a summary analysis of urban street network form, reporting the first such worldwide results in the literature.
- Notes
	- The main idea
		- “It uses the Global Human Settlement Layer (GHSL) to define urban area boundaries and other variables. Using OSMnx, it downloads and models urban-scale street network data globally from OpenStreetMap, attaches elevation data, then calculates indicators for each urban area.” The data they build.
		- “Across all urban areas worldwide, both total street length and intersection count scale sublinearly with population. Higher per capita GDP is associated with higher per capita total street length.” Some descriptive analysis they run on it.
	- On data quality and sources
		- “1) global coverage and availability, 2) consistent digitization and attribute data, 3) consistent representation of both geometric and topological data, and 4) better public accessibility and usability.” Areas where local street network data fails.
		- OSM
			- “Barrington-Leigh and Millard-Ball (2017) found that, as of 2016, OpenStreetMap was 83% complete worldwide, over 40% of countries’ (including many developing countries) street networks were effectively 100% complete, and completeness was highest in both dense cities and sparsely populated areas.” On the completeness of osm.
			- “a recent project modeled the street networks of every US city/town, county, urbanized area, census tract, and Zillow-defined neighborhood, placed these models online in a public open data repository, and conducted spatial network analyses on them (Boeing, 2020a).” Usage examples of OSMnx to create streen network indicators.
			- “Similarly, Dingil et al. (2018) used OSMnx to calculate transportation indicators for 151 urban areas worldwide. Karduni et al. (2016) created a data repository with 80 worldwide cities’ street networks derived from OpenStreetMap data. da Cruz et al. (2020) developed a database of urban indicators across 58 metropolitan areas worldwide, but did not include street network form indicators. Barrington-Leigh and Millard-Ball (2019, 2020) used all the streets mapped in OpenStreetMap to generate global indicators of street network disconnectivity to explore cross-sectional and longitudinal trends in urban sprawl.”
		- UCD
			- “spatial boundaries derived from the publicly available GHSL Urban Centre Database (UCD) version 2019a 1.2, a project supported by the European Commission’s Joint Research Centre and DirectorateGeneral for Regional and Urban Policy (Florczyk et al., 2019). In addition to these urban area boundaries, the UCD provides attribute data such as the names of the country and core city, population, built-up area, gross domestic product (GDP), UN income class and development group, transport-sector emissions, particulate matter concentration, climate, and land use efficiency.” On the source of spatial boundary data.
			- “the UCD consists of “high-density clusters of contiguous grid cells of 1 km2 with a density of at least 1,500 inhabitants per km2 and a minimum population of 50,000” (Florczyk et al., 2019, p. 13).” the UCD is built with population data from censuses and satellite imagery.
			- “three conditions: 1) is marked “true positive” in the UCD, 2) has ≥ 1 km2 built-up area, and 3) includes at least three OpenStreetMap drivable street network nodes within its boundaries. This comprises 8,914 total urban areas.” On how the author selects urban areas for which to create street networks.
		- How they process OSM data
			- “This study models these street networks as nonplanar directed multigraphs with possible self-loops. All of these models are primal graphs to account for the full geographic characteristics of the street network (Ratti, 2004; Batty, 2005). The workflow retains all graph components even if they are not fully connected and is parameterized to retrieve all public drivable streets” The data they select from osm and the graph they make with it.
			- “Raw OpenStreetMap data represent nodes as geometric vertices of straight-line segments composing more complex lines. Simplification produces a model that corresponds better to graph theory and transportation geography with nodes representing intersections and dead-ends and edges representing street segments.” How they process these data to produce clean graphs.
		- Elevation data
			- “the Advanced Spaceborne Thermal Emission and Reflection Radiometer (ASTER) v2 and the Shuttle Radar Topography Mission (SRTM). The ASTER DEM covers the world from 83° N to 83° S at a spatial resolution of one arcsecond (roughly 30 meters at the equator). The SRTM DEM covers the world from 60° N to 56° S at a spatial resolution of three arcseconds (roughly 90 meters at the equator). The ASTER DEM is finer resolution but exhibits more noise. The SRTM DEM is coarser resolution but less noisy, and was further processed by CGIAR-CSI to fix errors and fill voids (Gorokhovich and Voustianiouk, 2006).” The sources of elevation data.
			- “It selects for each node whichever of the ASTER or SRTM elevation values has the least absolute difference from the corresponding Google value, as a validation reference point.” They treat google elevation data as the most reliable, but closed source, and select whichever open source approximates closer to it.
	- Street network indicators
		- “The circuity indicator is the graph’s ratio of street lengths to straight-line distances between adjacent nodes, and straightness is its inverse. The former measures how circuitous the street network is on average, whereas the latter measures how closely its streets approximate straight lines (Boeing, 2021).”
		- “The elev_mean, elev_median, elev_std, elev_iqr, and elev_range represent the calculated mean, median, standard deviation, interquartile range, and range of node elevations, in meters. These provide indicators of the topography underlying the network”
		- “The grade_mean and grade_median fields represent the calculated mean and median street grade absolute values.”
		- “The intersect_count indicator represents the number of street intersections in the urban area—that is, the number of nodes with more than two incident edges in an undirected representation of the graph”
		- “The intersect_count_clean indicator is calculated by merging intersections within 10 meter buffers of each other geometrically (i.e., 10 meter Euclidean radii) before counting them”
		- “The intersect_count_clean_topo indicator is calculated by merging intersections within 10 meters of each other topologically along the network. This prevents topologically remote but spatially proximate nodes from being merged.”
		- “Clustering coefficients measure the extent to which a node’s neighbors form a complete graph (Jiang and Claramunt, 2004; Opsahl and Panzarasa, 2009)”
		- “The pagerank_max indicator is the maximum PageRank value of any node in the urban area: PageRank ranks nodes’ importance based on the structure of their links (Agryzkov et al., 2012; Boeing, 2020a).”
		- “The self_loop_proportion measures the urban area’s proportion of physical street segments that self-loop.”
		- “The k_avg indicator represents the average node degree of the undirected representation of the graph”
		- “The length_mean and length_median indicators are the calculated mean and median physical street segment (i.e., undirected edge) lengths in meters,”
		- “The street_segment_count and node_count fields contain the counts of physical street segments and nodes respectively.”
		- “The prop_4way, prop_3way, and prop_deadend fields contain the proportions of nodes in the graph that represent four-way intersections, three-way intersections, and culs-de-sac respectively.”
		- “The orientation_entropy and orientation_order indicators represent the calculated entropy of street bearings and their linearized and normalized order, as developed in Boeing (2019).”
	- On validation
		- “Barrington-Leigh and Millard-Ball (2017) note that OpenStreetMap was particularly incomplete in China as of 2016 due to restrictions”
		- “the elevation data are validated by comparing the ASTER, SRTM, and Google values for each node. Across all 37 million nodes worldwide, the elevation values between these three sources exhibit high correlation (all r > 0.999, p < 0.001).”
		- “we compare our street networks’ elev_mean indicator with the UCD’s estimated average elevation for each urban area. They strongly correlate (r > 0.999, p < 0.001) and the median difference between the two is 16 centimeters”
- Links
	- [Urban Centre Database](https://data.jrc.ec.europa.eu/dataset/53473144-b88c-44bc-b4a3-4583ed1f547e)
	  id:: 62d39c31-a84a-45ec-9121-a86c252cafa0
	- [All data at Harvard dataverse](https://dataverse.harvard.edu/dataverse/global-urban-street-networks/)
	  id:: 62d39c54-8007-4144-9f58-4f877fa7519a
	- [Models source at github](https://github.com/gboeing/street-network-models)
- Next
	- LATER Read and play with the ((62d39c31-a84a-45ec-9121-a86c252cafa0))
	- LATER Read and play with ((62d39c54-8007-4144-9f58-4f877fa7519a))
	- LATER Check other projects by the author at [his website](https://geoffboeing.com/), [osf](https://osf.io/28jpy/), [github](https://github.com/gboeing)
	- LATER Read [this other paper](https://www.sciencedirect.com/science/article/pii/S0198971522000539?via%3Dihub) by [the urban analytics lab](https://ual.sg/)
- Play
	- Indicator scatterplot with bolivian cities in blue
		- <iframe width="100%" height="570" frameborder="0"
		    src="https://observablehq.com/embed/@mauforonda/street-network-indicators?cells=scatter%2Cviewof+x_axis%2Cviewof+y_axis"></iframe>