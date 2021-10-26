### Designing a datastore
Repository which outlines the article series for designing a datastore

### Objective
- Talks about the objective of the series
    - Talks about why is this series being written
    - Talks about the overall gains for the readers
    - Talks about the overall gains for the author
- Contains links of all the articles in the series

### Storage devices
- Talks about storage hierarchy
- Introduces HDD / SDD / NVMe SDD

### Working of HDD
- Explains the working of HDD
- Introduces File Operations

### Working of SDD 
### Working of NVMe SSD
### Working of Intel Optane

### File Operations
- Talks about file read and write [+ code]
- Introduces mmap [+ code]
    - explains virtual memory
    - explains how mmap works
- Touches upon the concept of buffered IO
- Introduces the concept of a page or block

### Page / Block
- Talks about Page
- Explains working of standard IO Via Kernel Page Cache through to HDD sector
- Explains working of mmap based IO (might be slight repetition of "Introduces mmap")
- Explains the fact that a file is a collection of pages
- Introduces Page Organisation

### Page Organisation
- Explains binary encoding of data [+ code]
- Explains fixed and variable length records [+ code]
- Explains how fixed length records can organised in a page (includes page header also) [+ code]
- Explains how variable length records can organised in a page (Slotted Page) + (includes page header also) [+ code]
- Talks about endianness [+ code]
- Sample code to write a "string" (variable length record) to a slotted page
- Leaves an open question - what if a value does not fit in a page, do we have something like an overflow page?

### Overflow pages
- Explains overflow pages [+ code]
- Talks about organisation of overflow pages using slotted page concept [+ code]
- Sample code to demonstrate how to build them
- Introduces various ways to access pages - Sequential / Random

### Access Patterns 
- Talks about Random READS and WRITES
- Talks about Sequential READS and WRITES
- Talks about the cost of random writes on L1 / L2 / L3 cache also
- Explains the cost of both, taking HDD (or SDD / or both) as example(s)
- Introduces RUM Conjecture
- Introduces FIO

### FIO (Flexible IO tester)
- Talks about FIO and its role in development [+Command]
- Talks about some benchmark numbers for Sequential and Random READS and WRITES on SSD
- Introduces the concept of building a read optimised data storage (R) of RUM

### BST (Binary Search Tree)
- Introduces BST [+ code]
- Explains why BST is not good as a data structure for disk
- Explains the properties that a disk data structure should possess

### B+Tree
- Introduces B+Tree [+ code snippet]
    - Explains Get visually
    - Explains Put visually
    - If update is ready then update as well
- Explains its properties
- Lays out the foundation for building a B+Tree which supports get and put
    - Introduces various components say page, page pool, freelist, tree
    - Presents a diagrammatic representation of how do these components interact
    - Presents a diagrammatic representation of all the concepts - page / slotted page / overflow page / endianness etc

### Implementing B+Tree (I)
- Picks a programming language
- Explains the reason for that language

### Implementing B+Tree (II)
- Codes a B+Tree which supports get and put
- Explains some of the possible optimisations
    - Quick path
    - Suffix truncation
- Leaves open questions
    - How to handle concurrency
        - probably a good place to introduce BW Trees and implement?
    - How to handle transactions
    - How to make writes sequential
    - WAL
- Summary
    - Talks about databases using B+Tree or its variants

### Somewhere touch upon heap file (optional probably?)

### Pending
- All open questions which should become articles later
- Some flavours of B+Tree should become articles later
- LSM should become article(s) later
- File systems and their impact on data stores (say; NFTS Vs Linux)
- Story of a database which improved its throughput and explain how it was done
