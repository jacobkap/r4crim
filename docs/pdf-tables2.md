# More Scraping tables from PDFs {#scrape-table2}

In  Chapter \@ref(scrape-table) we used the package `pdftools` to scrape tables on arrests/seizures from the United States Border Patrol that were only available in a PDF. Given the importance of PDF scraping - hopefully by the time you read this chapter more data will be available in reasonable formats and not in PDFs - in this chapter we'll continue working on scraping tables from PDFs. Here we will use the package `tabulizer` which has a number of features making it especially useful for grabbing tables from PDFs. One issue which we saw in Chapter \@ref(scrape-table) is that the table may not be the only thing on the page - the page could also have a title, page number etc. When using `pdftools` we use regular expressions and subsetting to remove all the extra lines. Using `tabulizer` we can simply say (through a handy function) that we only want a part of the page, so we only scrape the table itself.  For more info about the `tabulizer` package please see their site [here](https://docs.ropensci.org/tabulizer/). 

For this chapter we'll scrape data from the Pennsylvania Commission on Sentencing's Sentencing Guidelines (available [here](https://github.com/jacobkap/crimebythenumbers/blob/master/data/7th%20Edition%20Amendment%205%20Complete%20Manual%202020.pdf). Sentencing guidelines are basically just a simple series of conditional statements that add up (each TRUE statement is literally given a numerical value) and then judges used the guidelines based on the final number value for the defendant. As an example, per the guidelines if a person is charged with a Felony 1 offenses (i.e. the second most serious kind of felony) that is worth 7 points. If this person has a prior record of a Felony 2 crime, add 2 points to the score. Assuming nothing else in the guidelines applies to this person, they now have 9 points and score, in combination with the current offense, affects the recommended sentence they receive. 

This PDF is 100 pages and only about a quarter of that is discussing the guidelines and what criteria a person has to meet to be given a certain score.^[I recommend reading/skimming this section - or your own state's sentencing guidelines - to get a better understanding of what they entail.] After this section is about 70 pages of tables which have the crime code (e.g. 3802 (f)(2)), the crime in plain English (e.g. DUI-commercial/school vehicles & incapable of safe driving (minor occupant; 1st/2nd off)), an indicator or what level of offense (e.g. Felony 1, Felony 2, Misdemeanor 3, etc.), the number of points a person receives for being charged with this crime, and the number of points a person receives for having a prior record of this offense.    

First, open this PDF in your web browser
While this technique 

If you don't have this package installed you'll need to install it using `install.packages("tabulizer")`. 


```r
library(tabulizer)
```
