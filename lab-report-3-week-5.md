# Lab Report 3

## grep -r

**grep -r "fbi" technical/*/*.txt**

    brandonbreeze@brandons-air skill-demo1 % grep -r "fbi" technical/*/*.txt
    technical/911report/chapter-13.3.txt:                FBI" (online at www.fbi.gov/libref/historic/history/historymain.htm); the FBI's
    technical/911report/chapter-13.3.txt:                updated June 18, 2003 (online at www.fas.org/irp/agency/doj/fbi/fbi_hist.htm). For
    technical/biomed/1471-2121-2-12.txt:        p14 Arfgene [ 2]. p14 Arfbinds to and sequesters mdm2,
    technical/biomed/1471-2164-4-6.txt:        http://www.cstl.nist.gov/biotech/strbase/fbicore.htm.

- For this example I chose to use -r on a very  intreesting looking path that uses the * to expand out each directory and file.  It seems iteresting to using because -r already searches recursivly.  This is useful to search through all directories

**grep -r "fbi"**

    brandonbreeze@brandons-air skill-demo1 % grep -r "fbi"      
    ./technical/biomed/1471-2121-2-12.txt:        p14 Arfgene [ 2]. p14 Arfbinds to and sequesters mdm2,
    ./technical/biomed/1471-2164-4-6.txt:        http://www.cstl.nist.gov/biotech/strbase/fbicore.htm.
    ./technical/911report/chapter-13.3.txt:                FBI" (online at www.fbi.gov/libref/historic/history/historymain.htm); the FBI's
    ./technical/911report/chapter-13.3.txt:                updated June 18, 2003 (online at www.fas.org/irp/agency/doj/fbi/fbi_hist.htm). For

- For this example I wanted to show that that -r does the same thing as the last example when it is not given a path.  What I think is interesting is that it does that same thing but in reverse.  This again shows how -r is useful to search through files and directories recursively.

**grep -r "slay" technical/**

    brandonbreeze@brandons-air skill-demo1 % grep -r "slay" technical/
    technical//biomed/gb-2002-3-12-research0079.txt:            between neighboring BACs using pslayout (LBNL) a
    technical//911report/chapter-12.txt:                thus given the picture of an omnipotent, unslayable hydra of destruction. This image

- For this example I wanted to show what -r does when given the current working directory. Furthermore, this has shown how -r can help search through all files without expanding paths.

## grep -i

**grep -i 'clev' technical/biomed/*.txt**

    brandonbreeze@brandons-air skill-demo1 % grep -i 'clev' technical/biomed/*.txt
    technical/biomed/1471-2105-2-8.txt:        more clever algorithmic strategy than straightforward
    technical/biomed/1471-2105-3-18.txt:        clever heuristics, such as using a precalculation of
    technical/biomed/1471-2121-3-10.txt:          system (US Biochemicals, Cleveland, OH).
    technical/biomed/1471-2180-1-8.txt:          (Amersham Life Science, Cleveland, OH) protocol as
    technical/biomed/1471-2199-2-12.txt:          Sequencing kit (Amersham, Cleveland, OH) using T3 and T7
    technical/biomed/1471-2199-3-11.txt:          Stark (Cleveland Clinic Foundation, Cleveland, OH). The
    technical/biomed/1471-2334-2-27.txt:          (B. F. Goodrich, Cleveland, OH). Poloxamer {an
    technical/biomed/1471-2407-1-19.txt:          University Hospital of Cleveland, Case Western Reserve
    technical/biomed/1471-2407-1-19.txt:          University, Cleveland, OH [ 23 ] . NRP-152 cells were
    technical/biomed/1471-2407-2-12.txt:          protocols approved by the Cleveland Clinic Foundation's
    technical/biomed/1471-2407-3-4.txt:          Sequenase, USB Corporation, Cleveland, OH) (Figure 1). 
    technical/biomed/1471-2466-2-4.txt:          University and University Hospitals of Cleveland. All
    technical/biomed/1471-2474-3-23.txt:        cage (DePuy-Acromed Corporation, Cleveland, Ohio) or
    technical/biomed/1472-6750-3-11.txt:          Biochemicals, Cleveland, OH), and 0.5 μM Cy3- or
    technical/biomed/1472-6793-1-12.txt:          pressure recorder (Gould, Cleveland, Ohio) for
    technical/biomed/1472-6874-2-8.txt:          Co, Cleveland, OH) or subcloned into a TA cloning vector
    technical/biomed/1475-2867-3-3.txt:          Biochemicals, Cleveland, OH. Imperial brand (Sugarland,
    technical/biomed/ar118.txt:          Medical Center in Cleveland. In addition, 30 healthy
    technical/biomed/ar118.txt:          Medical Center in Cleveland. In addition, 30 healthy
    technical/biomed/cc4.txt:          1000 recorder (Gould Instruments, Cleveland, OH)
    technical/biomed/gb-2002-3-11-research0060.txt:          is sampled unless a clever sampling strategy is used. All
    technical/biomed/rr196.txt:          Biochemicals, Cleveland, Ohio) at 25 units per 100 g body

- This example shows how -i helps with searching while ignoring the case. This helps by allowing the user to search for something without knowing the case

**grep -i 'CLEV' technical/biomed/*.txt**

    brandonbreeze@brandons-air skill-demo1 % grep -i 'CLEV' technical/biomed/*.txt
    technical/biomed/1471-2105-2-8.txt:        more clever algorithmic strategy than straightforward
    technical/biomed/1471-2105-3-18.txt:        clever heuristics, such as using a precalculation of
    technical/biomed/1471-2121-3-10.txt:          system (US Biochemicals, Cleveland, OH).
    technical/biomed/1471-2180-1-8.txt:          (Amersham Life Science, Cleveland, OH) protocol as
    technical/biomed/1471-2199-2-12.txt:          Sequencing kit (Amersham, Cleveland, OH) using T3 and T7
    technical/biomed/1471-2199-3-11.txt:          Stark (Cleveland Clinic Foundation, Cleveland, OH). The
    technical/biomed/1471-2334-2-27.txt:          (B. F. Goodrich, Cleveland, OH). Poloxamer {an
    technical/biomed/1471-2407-1-19.txt:          University Hospital of Cleveland, Case Western Reserve
    technical/biomed/1471-2407-1-19.txt:          University, Cleveland, OH [ 23 ] . NRP-152 cells were
    technical/biomed/1471-2407-2-12.txt:          protocols approved by the Cleveland Clinic Foundation's
    technical/biomed/1471-2407-3-4.txt:          Sequenase, USB Corporation, Cleveland, OH) (Figure 1). 
    technical/biomed/1471-2466-2-4.txt:          University and University Hospitals of Cleveland. All
    technical/biomed/1471-2474-3-23.txt:        cage (DePuy-Acromed Corporation, Cleveland, Ohio) or
    technical/biomed/1472-6750-3-11.txt:          Biochemicals, Cleveland, OH), and 0.5 μM Cy3- or
    technical/biomed/1472-6793-1-12.txt:          pressure recorder (Gould, Cleveland, Ohio) for
    technical/biomed/1472-6874-2-8.txt:          Co, Cleveland, OH) or subcloned into a TA cloning vector
    technical/biomed/1475-2867-3-3.txt:          Biochemicals, Cleveland, OH. Imperial brand (Sugarland,
    technical/biomed/ar118.txt:          Medical Center in Cleveland. In addition, 30 healthy
    technical/biomed/ar118.txt:          Medical Center in Cleveland. In addition, 30 healthy
    technical/biomed/cc4.txt:          1000 recorder (Gould Instruments, Cleveland, OH)
    technical/biomed/gb-2002-3-11-research0060.txt:          is sampled unless a clever sampling strategy is used. All
    technical/biomed/rr196.txt:          Biochemicals, Cleveland, Ohio) at 25 units per 100 g body

- This example shows how again the case doesn't matter when using -i.

**grep -i pm50  technical/biomed/*.txt**

    brandonbreeze@brandons-air skill-demo1 % grep -i pm50  technical/biomed/*.txt
    technical/biomed/1471-2229-3-3.txt:        highest number of alleles was found using primer pair PM50,
    technical/biomed/1471-2229-3-3.txt:        were identified at PM50 locus when 48 genotypes were
    technical/biomed/1471-2229-3-3.txt:        grapevine and tomato [ 34 ] . The locus PM50 contains only
    technical/biomed/1471-2229-3-3.txt:        primer pairs, such as PM36, PM 42, PM45, PM50, PM53, and

- This again shows how we are able to search for expressions in files with knowing the exact case.

## grep -c

**grep -c bio plos/pmed.0020232.txt**

    brandonbreeze@brandons-air technical % grep -c bio plos/pmed.0020232.txt
    33

- This example shows how we can use -c to count how many times the expression is in the file.  This can be helpful because it allows us to see how many times an expression appears in a files without getting the full output.

**grep -c bio plos/*2.txt**

    brandonbreeze@brandons-air technical % grep -c bio plos/*2.txt          
    plos/journal.pbio.0020012.txt:8
    plos/journal.pbio.0020042.txt:14
    plos/journal.pbio.0020052.txt:0
    plos/journal.pbio.0020112.txt:2
    plos/journal.pbio.0020172.txt:1
    plos/journal.pbio.0020232.txt:3
    plos/journal.pbio.0020262.txt:1
    plos/journal.pbio.0020272.txt:7
    plos/journal.pbio.0020302.txt:30
    plos/journal.pbio.0030032.txt:3
    plos/journal.pbio.0030062.txt:4
    plos/journal.pbio.0030102.txt:31
    plos/pmed.0010022.txt:0
    plos/pmed.0010042.txt:3
    plos/pmed.0010052.txt:9
    plos/pmed.0010062.txt:1
    plos/pmed.0020002.txt:1
    plos/pmed.0020022.txt:0
    plos/pmed.0020062.txt:0
    plos/pmed.0020082.txt:0
    plos/pmed.0020102.txt:0
    plos/pmed.0020162.txt:9
    plos/pmed.0020182.txt:3
    plos/pmed.0020192.txt:1
    plos/pmed.0020212.txt:5
    plos/pmed.0020232.txt:33
    plos/pmed.0020242.txt:0
    plos/pmed.0020272.txt:0

- this example shows how we can use -c to count how many expressions appear in multiple files. This can help is find how many file an expression appears

**grep -c bio plos/*2.txt | wc**

    brandonbreeze@brandons-air technical % grep -c bio plos/*2.txt | wc
        28      28     772

- In this example I was able to show how many files had an expression in them. This a really helpful way to count how many files have the thing you are looking for.