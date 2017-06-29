# datacleaning
For datacleaning course

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