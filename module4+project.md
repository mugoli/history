# Fail-log Module 4/Final Project

### Topic Modelling in R

* Downloaded nodes and links csv files
* Opened RStudio in DHBoxâ¨* Created a new project in RStudio
* Uploaded nodes and links to project folder in File Manager
* Ran a new script in RStudio: install.packages('igraph')
* Then, ran following script: library('igraph')
* Console says:
	* The following objects are masked from 'package:stats':
	* decompose, spectrum
	* The following object is masked from 'package:base':
	* union
* Made a mistake...
* Went into file manager and deleted the module4 folder
* Created a new folder called texas
* Uploaded nodes and links files to the folder via RStudio
* Ran install.packages('igraph') script
* Ran library('igraph')
* Ran nodes <- read.csv("texasnodes.csv", header=T, as.is=T)
	*links <- read.csv("texaslinks.csv", header=T, as.is=T)
* Ran #examine data
	* head(nodes)
	* head(links)
	* nrow(nodes); length(unique(nodes$id))
	* nrow(links); nrow(unique(links[,c("source", "target")]))â¨
* Ran links <- aggregate(links[,3], links[,-3], sum)
	* links <- links[order(links$target, links$source),]
	* colnames(links)[3] <- "weight"
	* rownames(links) <- NULL
	* head(links)
* Ran net <- graph.data.frame(d=links, vertices=nodes, directed=T)
* Ran plot(net, edge.arrow.size=.4,vertex.label=NA) which was supposed to allow me to visualize the data, but ran into this error in the console: Error in plot.new() : figure margins too large
* Tried it again, still the same
* Does plots too large mean I selected the wrong files?
* Tried to play around and change the size=X to different numers (1, 9, 100) and run the scripts, which did nothing. 
* Ran plot(net, edge.arrow.size=.4,vertex.label=NA)

Note: I truly hope that I will be able to find a fix for this, since I believe that this visualization has an interesting story to tell from the data. There are plenty letters being written to-from individuals, what were the networks, and how can I tie these findings to outside literature in order to build a data-driven story? Saving this script to try again with fresh eyes.

Note 2: Tries again this exact process and got to the same point. Abort mission.

### Data visualization using Cytoscape
* downloaded Cytoscape from http://www.cytoscape.org/
* created new project with nodes list
* played around with settings, opted for a circular chart
	* went in the layout menu -> selected attribute circle layout -> then selected the "selected" option
* selected people of interest, coloured them light blue by using the bypass setting in the left window
* Created a pink background by using the network mode in the left window, then selecting the "network" bypass backgroung paint -> pink
* the style or this visualization: big labels
* followed this tutorial to save my style file and my network file
* uploaded both to gsit
* have my visualization complete!

