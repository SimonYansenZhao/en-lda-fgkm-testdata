# Test Data for EN-LDA-FGKM #

## Data Source ##

* D1--D4 (d1-d4.rda) are derived from
  [20 Newsgroups](http://qwone.com/~jason/20Newsgroups/)

* R3 (r3.rda) and R7 (r7.rda) are derived from
  [Reuters-21578](http://www.daviddlewis.com/resources/testcollections/reuters21578/)

* RCV1 (rcv1.rda) is derived from
  [RCV1-v2](http://www.ai.mit.edu/projects/jmlr/papers/volume5/lewis04a/lyrl2004_rcv1v2_README.htm)


## Data Summary ##

| Data Set | Categories                     | No. of Documents | No. of Words |
|:--------:|:-------------------------------|-----------------:|-------------:|
| D1       | comp.sys.ibm.pc.hardware       | 558              | 2285         |
|          | comp.sys.mac.hardware          | 537              |              |
|          | comp.windows.x                 | 555              |              |
| D2       | comp.graphics                  | 546              | 2120         |
|          | comp.os.ms-windows.misc        | 534              |              |
|          | comp.sys.ibm.pc.hardware       | 556              |              |
| D3       | talk.politics.guns             | 537              | 3122         |
|          | talk.politics.mideast          | 538              |              |
| D4       | sci.electronics                | 551              | 4349         |
|          | sci.med                        | 572              |              |
|          | sci.space                      | 578              |              |
|          | soc.religion.christian         | 579              |              |
| R3       | earn                           | 2787             | 2807         |
|          | acq                            | 2092             |              |
|          | crude                          | 354              |              |
| R7       | earn                           | 2787             | 3460         |
|          | acq                            | 2088             |              |
|          | crude                          | 355              |              |
|          | trade                          | 332              |              |
|          | money-fx                       | 249              |              |
|          | interest                       | 198              |              |
|          | ship                           | 154              |              |
| RCV1     | C17 (Funding/Capital)          | 551              | 3086         |
|          | E21 (Government Finance)       | 610              |              |
|          | GCRIM (Crime, Law Enforcement) | 317              |              |
|          | GDIP (International Relations) | 291              |              |
|          | GPOL (Domestic Politics)       | 323              |              |
|          | GVIO (War, Civil War)          | 375              |              |
|          | M12 (Bond Markets)             | 449              |              |


## Data Format & Usage ##

All data sets are processed and stored using [R](https://www.r-project.org/).

```R
> load("d1.rda")
> ls()
[1] "d1"
> class(d1)
[1] "list"
> length(d1)
[1] 3
> names(d1)
[1] "corpus" "label"  "vocab"
> length(d1$corpus)
[1] 1650
> length(d1$label)
[1] 1650
> table(d1$label)

  4   5   6
  558 537 555
> length(d1$vocab)
[1] 2285
> head(d1$vocab)
       0        1        2        3        4        5
"series"   "card"    "edu"     "cs"     "ve"   "told"
> d1$corpus[[1]]
     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12] [,13] [,14]
[1,]    0    1    2    3    4    5    6    7    8     9    10    11    12    13
[2,]    1    1    1    1    1    1    3    1    1     1     1     2     1     1
     [,15]
[1,]    14
[2,]     1
> d1$corpus[[1]][, 1]
[1] 0 1
```

Every data set is a list of **corpus**, **label** and **vocab**.  A
element in **corpus** represents a document.  The category a document
belongs to is given in **label**.  **vocab** lists all the unique
words in **corpus**.  A document in **corpus** is represented as a
two-row matrix, where a column represents a unique word in the
document.  The first row is the index of the word in **vocab**, and
the second row is the *tf* (term frequency) of the word.  For example,
`d1$corpus[[1]][, 1]` tells the word "series" occurs once in the first
document.
