
# Unix command-line tools: groove on your data like it's 1971

### Get the data: 
* https://drive.google.com/file/d/0B4bLNvQWJ3-9dmc0M0w1dHVMbkE/view?usp=sharing

### Get the command-line tools:

#### OS X and Linux :
* Already installed, just open a terminal

#### Windows :
* Install Gow : https://github.com/bmatzelle/gow/wiki
* Open the Command Prompt (search `cmd.exe` from the Start menu)

## 1. Navigate between directories

### `pwd` (*print working directory*)

Where are we? Let's print the current working directory:


    !pwd

    /Users/arnaudrenaudfullsix/Google Drive/command-line-basics


### <code>cd</code> (<i>change directory</i>)

Now let's change our working directory to the one that contains the data:


    cd wikipedia_dataset

    /Users/arnaudrenaudfullsix/Google Drive/command-line-basics/wikipedia_dataset


### <code>ls</code> (<i>list directory contents</i>)

This command prints the list of the files and directories contained in the current working directory:


    !ls

    doi_and_pubmed_citations.enwiki_20150112.tsv doi_isbn_and_pubmed.enwiki_20150205.tsv
    doi_and_pubmed_citations.enwiki_20150205.tsv pubmed_citations.enwiki_20150112.tsv


Same thing in detail below:


    !ls -l

    total 962392
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101337899 Feb  9 17:29 doi_and_pubmed_citations.enwiki_20150112.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101763529 Mar  9 16:02 doi_and_pubmed_citations.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  252046963 Apr  6 18:03 doi_isbn_and_pubmed.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   37589923 Feb  3 00:28 pubmed_citations.enwiki_20150112.tsv


There are four files. Let's take a quick look at what's inside.

## 2. Actual data manipulation commands

### <code>head</code> and <code>tail</code>

`head` is going to print the first ten lines of the specified file:


    !head doi_and_pubmed_citations.enwiki_20150112.tsv

    page_id	page_title	rev_id	timestamp	type	id
    1015863	Contingent valuation	609087410	2014-05-18T12:33:42Z	doi	10.1257/jep.8.4.45
    1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/S0012-821X(97)00109-X
    1081235	Lava dome	518505477	2012-10-18T12:56:13Z	doi	10.1038/46950
    1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/0377-0273(83)90064-1
    1677742	Wu Jingzi	214641213	2008-05-24T15:20:40Z	doi	10.2307/2652696
    1934322	Kamerlingh Onnes (crater)	614821029	2014-06-29T00:02:07Z	doi	10.1007/BF00171763
    1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033/metrics
    1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033
    1081285	Point set triangulation	560066307	2013-06-15T20:38:51Z	doi	10.1109/SFCS.1991.185400


Similarly, we can print the last ten lines with `tail`:


    !tail doi_and_pubmed_citations.enwiki_20150112.tsv

    892865	Essential thrombocythaemia	608184756	2014-05-12T06:44:17Z	pmid	23668666
    892865	Essential thrombocythaemia	608184756	2014-05-12T06:44:17Z	pmid	19357394
    892865	Essential thrombocythaemia	608184756	2014-05-12T06:44:17Z	pmid	19636672
    892899	Parsing expression grammar	376288420	2010-07-30T17:03:03Z	doi	10.1145/964001.964011
    892899	Parsing expression grammar	292019066	2009-05-24T14:40:07Z	doi	10.1145/1408681.1408683
    893037	Road rage	567468999	2013-08-06T23:58:24Z	pmc	2922361
    893073	Kermadec Islands	522898545	2012-11-13T22:41:32Z	doi	10.1080/03014223.2003.9518348
    893073	Kermadec Islands	522898545	2012-11-13T22:41:32Z	doi	10.1017/S1464793102006061
    893122	Extreme physical information	591171539	2014-01-17T20:37:14Z	doi	10.1103/PhysRevE.88.042144
    893122	Extreme physical information	59688501	2006-06-20T20:48:48Z	doi	10.1016/j.ecolmodel.2003.12.045


### <code>wc</code> (<i>word, line, character, and byte count</i>)

Count the number of lines in a file (without providing the option `-l`, `wc` will not only count lines, but also words and characters):


    !wc -l doi_and_pubmed_citations.enwiki_20150112.tsv

     1291573 doi_and_pubmed_citations.enwiki_20150112.tsv


Using a wildcard, it is possible to apply a command to multiple files (here, `*` will match all the files in the working directory):


    !wc -l *

     1291573 doi_and_pubmed_citations.enwiki_20150112.tsv
     1296282 doi_and_pubmed_citations.enwiki_20150205.tsv
     3273255 doi_isbn_and_pubmed.enwiki_20150205.tsv
      549098 pubmed_citations.enwiki_20150112.tsv
     6410208 total


The same wildcard syntax can be applied to `head`. This will print the head of all the TSV files in the working directory:


    !head *.tsv

    ==> doi_and_pubmed_citations.enwiki_20150112.tsv <==
    page_id	page_title	rev_id	timestamp	type	id
    1015863	Contingent valuation	609087410	2014-05-18T12:33:42Z	doi	10.1257/jep.8.4.45
    1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/S0012-821X(97)00109-X
    1081235	Lava dome	518505477	2012-10-18T12:56:13Z	doi	10.1038/46950
    1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/0377-0273(83)90064-1
    1677742	Wu Jingzi	214641213	2008-05-24T15:20:40Z	doi	10.2307/2652696
    1934322	Kamerlingh Onnes (crater)	614821029	2014-06-29T00:02:07Z	doi	10.1007/BF00171763
    1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033/metrics
    1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033
    1081285	Point set triangulation	560066307	2013-06-15T20:38:51Z	doi	10.1109/SFCS.1991.185400
    
    ==> doi_and_pubmed_citations.enwiki_20150205.tsv <==
    page_id	page_title	rev_id	timestamp	type	id
    1086263	Robert Wedderburn (radical)	376446551	2010-07-31T16:51:45Z	doi	10.1080/01440398608574906
    1431727	Trần Thiện Khiêm	609491089	2014-05-21T07:40:19Z	doi	10.2307/2757066
    1431727	Trần Thiện Khiêm	592364629	2014-01-25T19:24:09Z	doi	10.1017/S0026749X04001295
    1431727	Trần Thiện Khiêm	610778568	2014-05-30T11:48:51Z	doi	10.1017/s0026749x07002855
    1017807	Gällivare	247665625	2008-10-25T23:05:33Z	pmid	16768023
    1512013	Wald's equation	214602293	2008-05-24T10:10:39Z	doi	10.1214/aoms/1177731235
    1512013	Wald's equation	281232642	2009-04-02T05:18:53Z	doi	10.1214/074921706000001067
    1512013	Wald's equation	590000681	2014-01-10T00:08:15Z	doi	10.1007/0-387-29548-8_2
    1512013	Wald's equation	394825096	2010-11-04T17:57:50Z	doi	10.1214/aoms/1177731092
    
    ==> doi_isbn_and_pubmed.enwiki_20150205.tsv <==
    page_id	page_title	rev_id	timestamp	type	id
    972037	Fireflash	416710586	2011-03-02T09:44:39Z	isbn	1576073459
    1086263	Robert Wedderburn (radical)	376445172	2010-07-31T16:41:42Z	isbn	0521307554
    1086263	Robert Wedderburn (radical)	376628944	2010-08-01T18:49:23Z	isbn	0814794564
    1086263	Robert Wedderburn (radical)	376446551	2010-07-31T16:51:45Z	doi	10.1080/01440398608574906
    972038	De Havilland Firestreak	408580981	2011-01-18T13:14:43Z	isbn	9781857802580
    972038	De Havilland Firestreak	416708979	2011-03-02T09:24:23Z	isbn	1852605413
    972038	De Havilland Firestreak	416708979	2011-03-02T09:24:23Z	isbn	1576073459
    1512005	John Kovalic	578333656	2013-10-22T23:42:21Z	isbn	9781907702587
    1512005	John Kovalic	639125373	2014-12-22T02:23:19Z	isbn	9781932442960
    
    ==> pubmed_citations.enwiki_20150112.tsv <==
    page_id	page_title	rev_id	timestamp	type	id
    1325125	Club cell	282470030	2009-04-08T01:52:20Z	pmid	18179694
    1325125	Club cell	385367462	2010-09-17T15:05:47Z	pmid	20223917
    1325125	Club cell	552727110	2013-04-29T14:05:24Z	pmid	23276834
    1325125	Club cell	352567087	2010-03-28T17:30:02Z	pmc	1456166
    1325125	Club cell	552727110	2013-04-29T14:05:24Z	pmid	22790912
    1325125	Club cell	282470417	2009-04-08T01:54:54Z	pmc	33880
    1325125	Club cell	282470417	2009-04-08T01:54:54Z	pmid	9707539
    1325125	Club cell	282470030	2009-04-08T01:52:20Z	pmc	2249579
    1325125	Club cell	352567087	2010-03-28T17:30:02Z	pmid	16157679


All four files have the same columns, including a `timestamp` column.

**Let's extract the year from the timestamp and split the data into as many files as there are years. We will first concatenate all files into one before splitting it into distinct years.**

### <code>sed</code> (<i>stream editor</i>)

Before concatenating the files, let's remove their header:


    # On Linux or OS X
    !sed -i '.original' '1d' *.tsv

`1d` stands for "delete line number 1", `-i` for "in-place". The arbitrary `.original` extension is appended to the original files.


    # On Windows (not possible to specify a specific filename to append to the copies of the original files)
    !sed -i "1d" *.tsv

Let's check the list of the files in our working directory:


    !ls -l

    total 1924784
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101337855 Apr 10 18:05 doi_and_pubmed_citations.enwiki_20150112.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101337899 Feb  9 17:29 doi_and_pubmed_citations.enwiki_20150112.tsv.original
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101763529 Apr 10 18:05 doi_and_pubmed_citations.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101763529 Mar  9 16:02 doi_and_pubmed_citations.enwiki_20150205.tsv.original
    -rw-r--r--  1 arnaudrenaudfullsix  staff  252046964 Apr 10 18:05 doi_isbn_and_pubmed.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  252046963 Apr  6 18:03 doi_isbn_and_pubmed.enwiki_20150205.tsv.original
    -rw-r--r--  1 arnaudrenaudfullsix  staff   37589923 Apr 10 18:05 pubmed_citations.enwiki_20150112.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   37589923 Feb  3 00:28 pubmed_citations.enwiki_20150112.tsv.original


We can notice the first row has been removed from this file:


    !head doi_and_pubmed_citations.enwiki_20150112.tsv

    1015863	Contingent valuation	609087410	2014-05-18T12:33:42Z	doi	10.1257/jep.8.4.45
    1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/S0012-821X(97)00109-X
    1081235	Lava dome	518505477	2012-10-18T12:56:13Z	doi	10.1038/46950
    1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/0377-0273(83)90064-1
    1677742	Wu Jingzi	214641213	2008-05-24T15:20:40Z	doi	10.2307/2652696
    1934322	Kamerlingh Onnes (crater)	614821029	2014-06-29T00:02:07Z	doi	10.1007/BF00171763
    1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033/metrics
    1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033
    1081285	Point set triangulation	560066307	2013-06-15T20:38:51Z	doi	10.1109/SFCS.1991.185400
    1081285	Point set triangulation	632378841	2014-11-04T04:57:19Z	doi	10.1137/0913058


### <code>cat</code> (<i>concatenate and print files</i>)

Let's concatenate all our TSV files into one:


    !cat *.tsv > all_doi_and_pubmed_citations.tsv

This is it. We can check the list of the TSV files and notice the newly created `all_doi_and_pubmed_citations.tsv` weighs indeed the same as the sum of the other files:


    !ls -l *.tsv

    -rw-r--r--  1 arnaudrenaudfullsix  staff  492738271 Apr 10 18:06 all_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101337855 Apr 10 18:05 doi_and_pubmed_citations.enwiki_20150112.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101763529 Apr 10 18:05 doi_and_pubmed_citations.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  252046964 Apr 10 18:05 doi_isbn_and_pubmed.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   37589923 Apr 10 18:05 pubmed_citations.enwiki_20150112.tsv


We now need to add a column containing the year of each record, based on the timestamp.

### <code>cut</code> (<i>cut out selected portions of each line of a file</i>)

Extracting the year and writing it as a column is going to take three steps:
- first, let's get the fourth column of our concatenated table (which is the `timestamp` column)
- then, let's pipe this result into `grep`, which will extract the year from the timestamp
- finally, we direct the result to a file that we call `years.txt`

It still fits in one line, though:


    # On Linux or OS X (extended regular expression)
    !cut -f4 all_doi_and_pubmed_citations.tsv | grep -E -o ^[0-9]{4} > years.txt


    # On Windows (basic regular expression)
    !cut -f4 all_doi_and_pubmed_citations.tsv | grep -o ^[0-9]\{4\} > years.txt

What does this `years.txt` file look like? 


    !head years.txt

    2014
    2008
    2012
    2008
    2008
    2014
    2012
    2012
    2013
    2014



    !wc -l years.txt all_doi_and_pubmed_citations.tsv

     6410205 years.txt
     6410208 all_doi_and_pubmed_citations.tsv
     12820413 total


Looks good. Each line contains a year and there appears to be as many lines as in the complete dataset.

### `sort` (*sort lines of text files*)
### `uniq` (*report or filter out repeated lines in a file*)

Before splitting our dataset into years, let's digress and check the years in presence in the dataset. The `uniq` command is quite self-explanatory; it only need a sorted file to drop all duplicates.


    !sort years.txt | uniq

    2001
    2002
    2003
    2004
    2005
    2006
    2007
    2008
    2009
    2010
    2011
    2012
    2013
    2014
    2015


Back to work now.

### `paste` (*merge corresponding or subsequent lines of files*)

Let's add the columns containing the years to our dataset (just like pasting a column in a spreadsheet, only writing it to a new file):


    !paste years.txt all_doi_and_pubmed_citations.tsv > years_all_doi_and_pubmed_citations.tsv

What does this newly created file look like?


    !head years_all_doi_and_pubmed_citations.tsv

    2014	1015863	Contingent valuation	609087410	2014-05-18T12:33:42Z	doi	10.1257/jep.8.4.45
    2008	1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/S0012-821X(97)00109-X
    2012	1081235	Lava dome	518505477	2012-10-18T12:56:13Z	doi	10.1038/46950
    2008	1081235	Lava dome	215463764	2008-05-28T09:21:09Z	doi	10.1016/0377-0273(83)90064-1
    2008	1677742	Wu Jingzi	214641213	2008-05-24T15:20:40Z	doi	10.2307/2652696
    2014	1934322	Kamerlingh Onnes (crater)	614821029	2014-06-29T00:02:07Z	doi	10.1007/BF00171763
    2012	1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033/metrics
    2012	1232227	Cannabivarin	513693453	2012-09-20T11:53:09Z	doi	10.1002/jps.2600641033
    2013	1081285	Point set triangulation	560066307	2013-06-15T20:38:51Z	doi	10.1109/SFCS.1991.185400
    2014	1081285	Point set triangulation	632378841	2014-11-04T04:57:19Z	doi	10.1137/0913058


### <code>awk</code> (<i>pattern-directed scanning and processing language</i>)

We're all set to split the dataset into as many files as there are distinct years.
Let's prefix each output file with the corresponding year.

We also need to indicate to the command `awk` which separator it needs to look for in our file (here, `\t`).


    # Unix
    !awk -F '\t' '{output=$1"_doi_and_pubmed_citations.tsv"; print $0 > output}' years_all_doi_and_pubmed_citations.tsv


    # Windows (replacing single quotes by double quotes and escaping double quotes)
    !awk -F "\t" "{output=$1\"_doi_and_pubmed_citations.tsv\"; print $0 > output}" years_all_doi_and_pubmed_citations.tsv

Slick one-liner and a powerful command. `$1` means we're splitting the file based on the value found in the first column (the year).

We can now make sure each distinct year has its own file:


    !ls -l *.tsv

    -rw-r--r--  1 arnaudrenaudfullsix  staff        289 Apr 10 16:24 2001_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff      33127 Apr 10 16:24 2002_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff     186850 Apr 10 16:24 2003_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff     858487 Apr 10 16:24 2004_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff    3103338 Apr 10 16:24 2005_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff    9323519 Apr 10 16:24 2006_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   56274704 Apr 10 16:24 2007_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   62579395 Apr 10 16:24 2008_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   58793636 Apr 10 16:24 2009_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   73809600 Apr 10 16:24 2010_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   56291954 Apr 10 16:24 2011_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   56779735 Apr 10 16:24 2012_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   63142523 Apr 10 16:24 2013_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   78538096 Apr 10 16:24 2014_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff    5073825 Apr 10 16:24 2015_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff        221 Apr 10 16:24 _doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  492738271 Apr 10 16:03 all_doi_and_pubmed_citations.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101337855 Apr 10 16:03 doi_and_pubmed_citations.enwiki_20150112.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  101763529 Apr 10 16:03 doi_and_pubmed_citations.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  252046964 Apr 10 16:03 doi_isbn_and_pubmed.enwiki_20150205.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff   37589923 Apr 10 16:03 pubmed_citations.enwiki_20150112.tsv
    -rw-r--r--  1 arnaudrenaudfullsix  staff  524789299 Apr 10 16:22 years_all_doi_and_pubmed_citations.tsv


### <code>grep</code> (<i>globally search regular expression and print</i>)

What about looking for all records that match a certain pattern? We want to print all the records containing "Serbia" from the 2012 dataset.


    !grep Serbia 2012_doi_and_pubmed_citations.tsv

    2012	4478927	White Serbia	505988534	2012-08-06T00:17:15Z	doi	10.2307/2841974
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	doi	10.2298/ZRVI1047055K
    2012	236637	Stephen Uroš IV Dušan of Serbia	470927105	2012-01-12T06:40:41Z	doi	10.2298/ZRVI0744381P
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	doi	10.2298/ZRVI1047055K
    2012	1471751	Serbian rock	304159392	2009-07-25T18:29:50Z	isbn	9788690531714
    2012	1729377	Časlav of Serbia	437839897	2011-07-05T08:55:12Z	isbn	0472081497
    2012	1729377	Časlav of Serbia	437839897	2011-07-05T08:55:12Z	isbn	8617137541
    2012	1753822	Patriarch Pavle of Serbia	491768586	2012-05-10T10:07:19Z	isbn	0520216628
    2012	1753822	Patriarch Pavle of Serbia	491768586	2012-05-10T10:07:19Z	isbn	0773522166
    2012	1753822	Patriarch Pavle of Serbia	491768586	2012-05-10T10:07:19Z	isbn	0195174291
    2012	1753822	Patriarch Pavle of Serbia	491768586	2012-05-10T10:07:19Z	isbn	1850653674
    2012	3005163	Višeslav of Serbia	437265123	2011-07-01T18:02:38Z	isbn	0631204717
    2012	2843257	Serbia in the Middle Ages	261782641	2009-01-03T23:45:52Z	isbn	0472081497
    2012	3538626	Serbian Volunteer Corps (World War II)	618149726	2014-07-23T17:23:23Z	isbn	9780804736152
    2012	4478927	White Serbia	545619274	2013-03-20T06:44:45Z	isbn	0631204717
    2012	5046294	Petar of Serbia	400312210	2010-12-03T14:00:31Z	isbn	0472081497
    2012	5046294	Petar of Serbia	437111777	2011-06-30T20:39:27Z	isbn	8617137541
    2012	5046294	Petar of Serbia	400312210	2010-12-03T14:00:31Z	isbn	9780521894524
    2012	4976079	Territory of the Military Commander in Serbia	542577947	2013-03-07T13:00:57Z	isbn	9780804708579
    2012	4976079	Territory of the Military Commander in Serbia	542577947	2013-03-07T13:00:57Z	isbn	9781850658955
    2012	4976079	Territory of the Military Commander in Serbia	507530175	2012-08-15T13:19:21Z	isbn	9788672743883
    2012	4976079	Territory of the Military Commander in Serbia	416473362	2011-03-01T00:35:07Z	isbn	0822319977
    2012	4976079	Territory of the Military Commander in Serbia	485463268	2012-04-04T06:17:15Z	isbn	9780393090109
    2012	4976079	Territory of the Military Commander in Serbia	486232396	2012-04-08T09:56:17Z	isbn	9780198228875
    2012	4976079	Territory of the Military Commander in Serbia	485871226	2012-04-06T10:00:01Z	isbn	9780803259799
    2012	4976079	Territory of the Military Commander in Serbia	489450400	2012-04-27T10:38:03Z	isbn	9780807820667
    2012	4976079	Territory of the Military Commander in Serbia	542577947	2013-03-07T13:00:57Z	isbn	9781584779018
    2012	4976079	Territory of the Military Commander in Serbia	486237399	2012-04-08T10:44:15Z	isbn	9780761836476
    2012	4976079	Territory of the Military Commander in Serbia	603050482	2014-04-06T20:04:25Z	isbn	9781400825509
    2012	4976079	Territory of the Military Commander in Serbia	485850073	2012-04-06T06:39:52Z	isbn	9780783557199
    2012	4976079	Territory of the Military Commander in Serbia	542577947	2013-03-07T13:00:57Z	isbn	9780253346568
    2012	4976079	Territory of the Military Commander in Serbia	486226169	2012-04-08T08:54:22Z	isbn	9781850654766
    2012	4976079	Territory of the Military Commander in Serbia	542577947	2013-03-07T13:00:57Z	doi	10.2298/IJGI1202093J
    2012	4976079	Territory of the Military Commander in Serbia	257570599	2008-12-12T21:28:46Z	isbn	0890967601
    2012	4976079	Territory of the Military Commander in Serbia	485890435	2012-04-06T12:29:03Z	isbn	9780880331395
    2012	4731980	Serbian Campaign of World War I	614768800	2014-06-28T15:31:09Z	isbn	9780330412247
    2012	4731980	Serbian Campaign of World War I	630339812	2014-10-20T06:14:43Z	isbn	9780472115570
    2012	5701105	Mutimir of Serbia	436374067	2011-06-26T18:41:27Z	isbn	0472081497
    2012	5701105	Mutimir of Serbia	436374067	2011-06-26T18:41:27Z	isbn	8617137541
    2012	5218056	Serbian State Guard	532789654	2013-01-13T01:25:15Z	isbn	9780253346568
    2012	5861152	Greece–Serbia relations	490097738	2012-05-01T09:41:57Z	isbn	9781585442263
    2012	7669071	Serbian American	622397508	2014-08-22T22:39:04Z	isbn	9781438110127
    2012	8056034	Serbian nationalism	609935706	2014-05-24T12:15:09Z	doi	10.1111/j.1469-8129.2010.00469.x
    2012	9712537	Moravian Serbia	482748197	2012-03-19T16:52:11Z	isbn	9789607309587
    2012	9712537	Moravian Serbia	482748197	2012-03-19T16:52:11Z	isbn	0472082604
    2012	9521899	Serbian Cyrillic alphabet	427992083	2011-05-07T23:12:37Z	isbn	1557534772
    2012	10911895	List of birds of Serbia	126165283	2007-04-26T16:06:55Z	isbn	0934797161
    2012	1595	Alexander I of Serbia	223723361	2008-07-05T13:21:35Z	isbn	0317050745
    2012	15192077	Helena of Serbia, Queen of Hungary	601634339	2014-03-28T10:17:15Z	isbn	9788675499213
    2012	14831835	Postage stamps and postal history of Serbia	611552915	2014-06-04T17:06:24Z	isbn	3952108316
    2012	15996489	Serbia–United States relations	488740258	2012-04-23T00:57:58Z	isbn	9780801441585
    2012	18970473	Medieval Serbian army	528051890	2012-12-14T19:14:16Z	isbn	9789607309587
    2012	18970473	Medieval Serbian army	528051890	2012-12-14T19:14:16Z	isbn	8683565017
    2012	18970473	Medieval Serbian army	528051890	2012-12-14T19:14:16Z	isbn	0472082604
    2012	18466567	Pribislav of Serbia	437260415	2011-07-01T17:27:53Z	isbn	0472081497
    2012	18466567	Pribislav of Serbia	437260415	2011-07-01T17:27:53Z	isbn	8617137541
    2012	19360790	Vrhpolje, Serbia	239073094	2008-09-17T18:10:56Z	isbn	8684433149
    2012	18883160	Romanization of Serbian	552303072	2013-04-26T17:30:17Z	isbn	9781557534774
    2012	18889535	Serbian folk astronomy	379065249	2010-08-15T16:24:48Z	isbn	8674940250
    2012	21247907	Uroš II, Grand Prince of Serbia	445971661	2011-08-21T11:06:20Z	isbn	0631204717
    2012	21247907	Uroš II, Grand Prince of Serbia	445971661	2011-08-21T11:06:20Z	isbn	0472081497
    2012	26653707	Zaharija of Serbia	437809506	2011-07-05T03:21:46Z	isbn	0472081497
    2012	26653707	Zaharija of Serbia	437809506	2011-07-05T03:21:46Z	isbn	8617137541
    2012	25062797	Uroš I, Grand Prince of Serbia	436391956	2011-06-26T20:43:18Z	isbn	0472081497
    2012	25062797	Uroš I, Grand Prince of Serbia	492094186	2012-05-11T22:51:16Z	isbn	0231040806
    2012	27453297	Klenovac, Serbia	483108033	2012-03-21T12:06:47Z	isbn	8684433009
    2012	22782527	Prehistoric sites in Serbia	294707793	2009-06-06T02:30:54Z	isbn	9780631212935
    2012	29301855	Serbian titles	486466171	2012-04-09T17:38:25Z	isbn	0748602097
    2012	29301855	Serbian titles	392181142	2010-10-22T08:35:37Z	isbn	0472082604
    2012	29301855	Serbian titles	486463872	2012-04-09T17:26:29Z	isbn	8683565017
    2012	27713885	Klokočevac, Serbia	483109952	2012-03-21T12:19:00Z	isbn	8684433009
    2012	27946361	Vrban, Serbia	483111832	2012-03-21T12:28:26Z	isbn	8684433009
    2012	25949287	Pavle of Serbia	437311305	2011-07-01T23:36:48Z	isbn	1605204218
    2012	25949287	Pavle of Serbia	437311305	2011-07-01T23:36:48Z	isbn	9780521894524
    2012	28859615	Doliće, Serbia	483121146	2012-03-21T13:15:51Z	isbn	8684433009
    2012	27308258	Gradinje, Serbia	483099096	2012-03-21T11:29:21Z	isbn	8684433009
    2012	28867117	Blaca, Serbia	483122074	2012-03-21T13:19:20Z	isbn	8684433009
    2012	28087534	Stančići, Serbia	483114023	2012-03-21T12:41:00Z	isbn	8684433009
    2012	28088171	Puhovo, Serbia	483117109	2012-03-21T12:57:00Z	isbn	8684433009
    2012	35129341	Serbian Orthodox Diocese v. Milivojevich	608363028	2014-05-13T11:17:43Z	doi	10.1093/jcs/42.2.311
    2012	28132702	Rudine, Serbia	483117775	2012-03-21T13:00:53Z	isbn	8684433009
    2012	28938683	Leva Reka, Serbia	483124448	2012-03-21T13:27:49Z	isbn	8684433009
    2012	31292300	Serbian Kovin Monastery	480267796	2012-03-05T04:36:16Z	isbn	8607004808
    2012	32323380	Axis occupation of Serbia	506571381	2012-08-09T15:23:11Z	isbn	9788674030233
    2012	32323380	Axis occupation of Serbia	506565375	2012-08-09T14:38:10Z	isbn	9789536045198
    2012	31378963	Serbian Grand Principality	439817629	2011-07-16T18:40:41Z	isbn	0520204964
    2012	31378963	Serbian Grand Principality	490601012	2012-05-04T08:18:30Z	isbn	047211414X
    2012	31378963	Serbian Grand Principality	439817629	2011-07-16T18:40:41Z	isbn	0521815304
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	1605200050
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	0521770173
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	1602062706
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	0631204717
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	9004082654
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	doi	10.2298/ZRVI1047055K
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	9781580573146
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	0472081497
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	1605204218
    2012	35482318	Historical administrative divisions of Serbia	487316633	2012-04-14T10:19:49Z	isbn	9788683883080
    2012	34347678	Association of Writers of Serbia	481058976	2012-03-09T20:29:06Z	isbn	9780253346568
    2012	32542445	Serbian nobility	450826621	2011-09-16T16:08:31Z	isbn	1113201428
    2012	33473780	Radovanje, Serbia	483135708	2012-03-21T14:14:56Z	isbn	8684433009
    2012	33475070	Zagorica, Serbia	483137340	2012-03-21T14:21:52Z	isbn	8684433009
    2012	35654237	List of strategoi of Serbia	564754052	2013-07-18T06:55:30Z	isbn	9780521815307
    2012	34746378	Serbian–Ottoman War (1876–78)	633213537	2014-11-10T10:49:33Z	isbn	9780804708869
    2012	32932741	Maria Palaiologina, Queen of Serbia	447653836	2011-08-31T13:22:36Z	isbn	9780472082605
    2012	32968906	Lukar, Serbia	483129174	2012-03-21T13:45:30Z	isbn	8684433009
    2012	41430504	St. Sava Serbian Orthodox Cathedral	587289643	2013-12-22T22:14:35Z	isbn	0870206338
    2012	41430504	St. Sava Serbian Orthodox Cathedral	587286871	2013-12-22T21:54:13Z	isbn	1598842196
    2012	34947094	Serbian Chetnik Organization	606671728	2014-05-01T19:43:39Z	isbn	9788679050441
    2012	38997321	Uprising in Serbia (1941)	548427122	2013-04-03T03:28:03Z	isbn	9781850654766
    2012	45045906	Serbian Revival	642417144	2015-01-14T06:28:10Z	isbn	9783876909851
    2012	38112882	Republika Srpska–Serbia relations	538946478	2013-02-18T22:59:02Z	isbn	9780300158267
    2012	43400128	German–Serbian dictionary (1791)	623045781	2014-08-27T16:01:31Z	isbn	9783899713251
    2012	42083267	Serbian Orthodox Seminary of Prizren	597691845	2014-03-01T17:29:05Z	isbn	8679350656
    2012	27289	Serbia and Montenegro	636666119	2014-12-04T21:41:06Z	isbn	9780300158267
    2012	27289	Serbia and Montenegro	530268143	2012-12-29T08:40:39Z	isbn	9781563243097
    2012	29265	Serbia	448403428	2011-09-04T13:16:21Z	isbn	0472081497
    2012	29265	Serbia	517551549	2012-10-13T10:33:46Z	isbn	0231700504
    2012	29265	Serbia	584688439	2013-12-05T13:51:29Z	isbn	9783540648352
    2012	184274	History of Serbia	633220297	2014-11-10T12:17:37Z	isbn	9780472081493
    2012	236637	Stephen Uroš IV Dušan of Serbia	463329134	2011-11-30T17:55:09Z	isbn	052109531X
    2012	236637	Stephen Uroš IV Dušan of Serbia	366897117	2010-06-08T23:52:13Z	isbn	8676850070
    2012	236637	Stephen Uroš IV Dušan of Serbia	473170701	2012-01-25T15:38:48Z	isbn	9780312121167
    2012	236637	Stephen Uroš IV Dušan of Serbia	632758645	2014-11-06T23:14:44Z	isbn	9781585442263
    2012	236637	Stephen Uroš IV Dušan of Serbia	632758645	2014-11-06T23:14:44Z	isbn	9781857430585
    2012	236637	Stephen Uroš IV Dušan of Serbia	473170701	2012-01-25T15:38:48Z	isbn	9783640401284
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	1605200050
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	0521770173
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	1602062706
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	0631204717
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	9004082654
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	9781580573146
    2012	276571	Principality of Serbia (medieval)	417796303	2011-03-08T15:52:53Z	isbn	1403964173
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	0472081497
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	1605204218
    2012	276571	Principality of Serbia (medieval)	483944543	2012-03-26T01:59:38Z	isbn	9788683883080
    2012	276571	Principality of Serbia (medieval)	483949462	2012-03-26T02:42:51Z	isbn	9780521074599
    2012	326125	Lazar of Serbia	482084931	2012-03-15T20:30:48Z	isbn	0472082604
    2012	326125	Lazar of Serbia	515993261	2012-10-04T17:12:56Z	isbn	9788763505048
    2012	326125	Lazar of Serbia	482084931	2012-03-15T20:30:48Z	isbn	8635504526
    2012	326125	Lazar of Serbia	515993261	2012-10-04T17:12:56Z	isbn	9789992287552
    2012	326125	Lazar of Serbia	482540576	2012-03-18T13:56:54Z	isbn	9780472114146
    2012	326125	Lazar of Serbia	482084931	2012-03-15T20:30:48Z	isbn	9789607309587
    2012	295461	Comparison of standard Bosnian, Croatian and Serbian	456328746	2011-10-19T10:07:00Z	isbn	9780521223157
    2012	295461	Comparison of standard Bosnian, Croatian and Serbian	506416621	2012-08-08T16:49:07Z	isbn	3825898911
    2012	295461	Comparison of standard Bosnian, Croatian and Serbian	57522253	2006-06-08T12:17:19Z	isbn	0415971179
    2012	417429	Socialist Party of Serbia	597532674	2014-02-28T15:33:38Z	isbn	9780765619112
    2012	417945	Greater Serbia	362603273	2010-05-17T12:33:08Z	isbn	0814755615
    2012	417945	Greater Serbia	362527780	2010-05-17T00:15:00Z	isbn	0890967601
    2012	526399	Republic of Serbian Krajina	501999472	2012-07-13T04:08:22Z	isbn	8683905055
    2012	526399	Republic of Serbian Krajina	308628815	2009-08-18T05:51:53Z	isbn	1850655251
    2012	526399	Republic of Serbian Krajina	542277049	2013-03-05T22:41:13Z	isbn	030016629X
    2012	526399	Republic of Serbian Krajina	180871142	2007-12-29T22:26:47Z	isbn	9532122494
    2012	526399	Republic of Serbian Krajina	542273823	2013-03-05T22:20:11Z	isbn	0253346568


We might as well search records about France or England (case-insensitive this time) in the whole dataset and write the results into a new file.


    !grep -i -e France -e England all_doi_and_pubmed_citations.tsv > france_england_citations.tsv


    !wc -l france_england_citations.tsv

        7835 france_england_citations.tsv

