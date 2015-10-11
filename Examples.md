Two early examples of analysis:

jphysiol_80_3_1042.png see https://bitbucket.org/petermr/diagramanalyzer/src/e837eb25c124f05483e0a95d9c8ef1947b00a849/src/test/resources/org/xmlcml/diagrams/neuro/jphysiol_80_3_1042.png?raw=true 
This is a voltage-current trace with all the characters (axes, etc.) stripped off. 
DiagramAnalyzer has a class `NeuroAnalyzer` which reads this pixel map and extracts the two lines from it. (The quality is poor - breaks - so there are artefacts in the result). The processing is in https://bitbucket.org/petermr/diagramanalyzer/src/e837eb25c124f05483e0a95d9c8ef1947b00a849/src/test/java/org/xmlcml/diagrams/neuro/TraceTest.java?at=default&fileviewer=file-view-default which:

* reads the image
* thins the lines to single pixels
* scans with constant x-raster slices to estimate the y-value at each x
* records these in to a CSV file
* joins y into lines
* draws lines to represent the traces.







