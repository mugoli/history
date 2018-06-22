# Fail-log Module 4/Final Project

### Topic Modelling in R

* Downloaded nodes and links csv filesâ¨* Opened RStudio in DHBoxâ¨* Created a new project in RStudioâ¨* Uploaded nodes and links to project folder in File Managerâ¨* Ran a new script in RStudio: install.packages('igraph')â¨* Then, ran following script: library('igraph')â¨* Console says:â¨	* The following objects are masked from âpackage:statsâ:
	* decompose, spectrum
	* The following object is masked from âpackage:baseâ:
	* unionâ¨â¨* Made a mistakeâ¦â¨* Went into file manager and deleted the module4 folderâ¨* Created a new folder called texasâ¨* Uploaded nodes and links files to the folder via RStudioâ¨* Ran install.packages('igraph') scriptâ¨* Ran library('igraph')â¨* Ran nodes <- read.csv("texasnodes.csv", header=T, as.is=T)â¨	*links <- read.csv("texaslinks.csv", header=T, as.is=T)â¨* Ran #examine dataâ¨	* head(nodes)â¨	* head(links)
	* nrow(nodes); length(unique(nodes$id))
	* nrow(links); nrow(unique(links[,c("source", "target")]))â¨
* Ran Â links <- aggregate(links[,3], links[,-3], sum)â¨	* links <- links[order(links$target, links$source),]â¨	* colnames(links)[3] <- "weight"â¨	* rownames(links) <- NULLâ¨	* head(links)â¨
* Ran net <- graph.data.frame(d=links, vertices=nodes, directed=T)â¨* Ran plot(net, edge.arrow.size=.4,vertex.label=NA) which was supposed to allow me to visualize the data, but ran into this error in the console: Error in plot.new() : figure margins too largeâ¨* Tried it again, still the sameâ¨* Does plots too large mean I selected the wrong files?â¨* Tried to play around and change the size=X to different numers (1, 9, 100) and run the scripts, which did nothing. â¨* Ran plot(net, edge.arrow.size=.4,vertex.label=NA)â¨

Note: I truly hope that I will be able to find a fix for this, since I believe that this visualization has an interesting story to tell from the data. There are plenty letters being written to-from individuals, what were the networks, and how can I tie these findings to outside literature in order to build a data-driven story? Saving this script to try again with fresh eyes.

Note 2: Tries again this exact process and got to the same point. Abort mission.

### Data visualization using Cytoscape
* downloaded Cytoscape from http://www.cytoscape.org/
* created new project with nodes list
* played around with settings, opted for a circular chart
	* went in the layout menu -> selected attribute circle layout -> then selected the âselectedâ option
* selected people of interest, coloured them light blue by using the bypass setting in the left window
* Created a pink background by using the network mode in the left window, then selecting the ânetworkâ bypass backgroung paint -> pink
* the style or this visualization: big labels
* followed âthis tutorialâ to save my style file and my network file
* uploaded both to gsit
* have my visualization complete!

