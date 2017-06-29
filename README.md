# datacleaning
For datacleaning course

Github repo for course (i.e., presentations):

https://github.com/DataScienceSpecialization/courses/tree/master/03_GettingData


## URLs

https://www.w3schools.com/xml/simple.xml

http://www.espn.com/nfl/team/_/name/bal/baltimore-ravens

## Reading XML from a URL

````
install.packages("XML")
library(XML)
````

Course says: 
> fileUrl <- "https://www.w3schools.com/xml/simple.xml"
> doc <- xmlTreeParse(fileUrl, useInternal = TRUE)

That bombs with error saying it's not an XML doc, which is a bug. Workaround is:

````
install.packages("RCurl")
library(RCurl)
xdata <- getURL(fileUrl)
doc <- xmlTreeParse(xdata, useInternalNodes = TRUE)
rootNode <- xmlRoot(doc)
xmlName(rootnode)
````

Similarly:

````
fileUrl <- "http://www.espn.com/nfl/team/_/name/bal/baltimore-ravens"
xdata <- getURL(fileUrl)
doc <- htmlTreeParse(xdata, useInternalNodes = TRUE)
````

Note That
> scores <- xpathSApply(doc, "//li[@class='team-names']",xmlValue)
> scores <- xpathSApply(doc, "//li[@class='score']",xmlValue)
> teams <- xpathSApply(doc, "//li[@class='team-names']",xmlValue)
> teams
does not work - the website has changed.

## XPath (and other xml) documentation

http://www.stat.berkeley.edu/~statcur/Workshop2/Presentations/XML.pdf

## XML Tutorials

Short: http://www.omegahat.net/RSXML/shortIntro.pdf

Long: http://www.omegahat.net/RSXML/Tour.pdf

Awesome XML package resource : http://www.stat.berkeley.edu/~statcur/Workshop2/Presentations/XML.pdf
