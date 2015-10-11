# neuro
Neurophysiology, especially voltage traces Primarily to scrape images of voltage/current plots and analyze them semantically.

The whole project is run as Open NotebookScience https://en.wikipedia.org/wiki/Open_notebook_science and everything should either be in this repo or accessible from it. 

* Raw data will be stored in this repo. (Copyrighted material may be omitted).
* IPython (Jupyter) will be used as the primary recording mechanism
* analysis software (e.g `diagramanalyzer` will be modified to create log files which will be posted alongside the computed data


Currently the analysis software is in https://bitbucket.org/petermr/diagramanalyzer/ - see NeuroAnalyzerTest for the latest prototype.

There is a scraper for J. Neuroscience in jneuro.json . First you need to create a list of URLs. @blah404 will create a `quickcrawl` but until then:

enter a search in J.Neurophysiology using Firefox (because the HTML will be different elsewhere - this is a temporary hack until `quickcrawl`). Typical:
```
http://www.jneurosci.org/search?fulltext=CA1+and+pyramidal+and+clamp&submit=yes&x=9&y=10&hits=200
```
This will run the search for "CA1" and "pyramidal" and "clamp" and output <= 200 hits in a single HTML file. To extract the URLs on a UNIX commandline:
```grep -i "Full Text<" | sed -i -e 's/.*http/http/' | sed -i -e 's/\?.*//' > urls.txt
```
This should create `urls.txt` (else find a UNIX guru and buy them a drink).

To run the scraper:
```
quickscrape --urllist urls.txt --scraper ../../journal-scrapers/scrapers/jneuro.json --output ca1 --loglevel verbose
```
where `ca1` should be renamed to your output directory (`CProject`) and the logging level can be reduced.


