# Final bioinformatics code snippets using Biopython

Also see: [Full Biopython documentation](http://biopython.org/DIST/docs/tutorial/Tutorial.html)

Examining your sequence data using bioPython will simplify a lot of our issues in trying to read a binary (.ab1) file: 

### Getting sequence from the ab1 trace file

```python
# import SeqIO from the Bio library/module
# SeqIO lets us handle the file (open and read from it)
from Bio import SeqIO
 
# specify the path of the file
file_path = "/foo/bar/file.ab1"
 
sequence_object = SeqIO.read(open(file_path,"rb"),"abi")    
sequence = sequence_object.format("fasta")
print sequence 
 
# get the quality scores for each base
quals = sequence_object.letter_annotations['phred_quality']
print "type of qual is %s" % type(quals)
```

### Blasting a sequence and returning results

```python
from Bio.Blast import NCBIWWW
from Bio.Blast import NCBIXML

#blast the sequence result using blastn, against the
#nr database, evalue of 0.0001, return top 5 hits
blast_result = NCBIWWW.qblast('blastn','nt',sequence, expect = 0.0001, hitlist_size=5) 

blast_record = NCBIXML.read(blast_result)

# print the blast hit results

for records in blast_record.alignments:
    print records

```
