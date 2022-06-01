```python
print("Hello World")
```

    Hello World


print() is a function, and "Hello World" is an argument 


```python
# lines of code can be commented too with a hash 
```


```python
# purposeful error code 
print(hello world)
```


      Input In [2]
        print(hello world)
                    ^
    SyntaxError: invalid syntax




```python
# another purposeful error 
pint("hello world")
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Input In [3], in <cell line: 2>()
          1 # another purposeful error 
    ----> 2 pint("hello world")


    NameError: name 'pint' is not defined



```python
# print phrase with line break 
print("hello\nworld")
```

    hello
    world



```python
# store a short DNA sequence 
DNA_Seq = "AAGTCGT"
```


```python
# print that sequence 
print(DNA_Seq)
```

    AAGTCGT



```python
# try to find the length of the sequence 
len(DNA_Seq)
```




    7




```python
# what if I want to turn the length of the sequence into a string instead of a number?
length_DNA = len(DNA_Seq)
print("The length of my sequence is " + str(length_DNA))
```

    The length of my sequence is 7



```python
# using a method > like a function but only for a particular type of thing 
print(DNA_Seq.lower())
# write the variable first, then a period, then the method, followed 
# by parentheses including arguments (if any)
# method does not change the variable (DNA_Seq)
```

    aagtcgt



```python
# using the replace method 
protein = "vlspadktnv"
# replace l with t
print(protein.replace("l", "t"))
```

    vtspadktnv



```python
# print a portion, or a substring, of the protein sequence 
print(protein[2:4])
# notice that the "1st" position is actually 0
# also notice that the first position gets included, but the stop position is not included
```

    sp



```python
# count how many Vs in the protein sequence 
V_counts = protein.count("v")
print("number of Vs: " + str(V_counts))
```

    number of Vs: 2



```python
# also find the position of a protein in the sequence 
protein.find("a")
```




    4




```python
# or 
print("a is in position " + str(protein.find("a")))
```

    a is in position 4


Exercises

1 Calculating AT content


```python
# find the AT content of this sequence 
#  ACTGATCGATTACGTATAGTATTTGCTATCATACATATATATCGATGCGTTCAT
# first make it into a variable 
sequence = "ACTGATCGATTACGTATAGTATTTGCTATCATACATATATATCGATGCGTTCAT"
```


```python
# now I want to count how many As and Ts 
A_counts = sequence.count("A")
T_counts = sequence.count("T")
```


```python
# now to add those numbers up 
AT_count = A_counts + T_counts
```


```python
# what is this number?
print(AT_count)
```

    37



```python
# usually AT content is presented as a percentage, so I need to know how long the sequence is too 
length_sequence = len(sequence)
print(length_sequence)
```

    54



```python
# ok now I know the total number of bases and how many ATs 
AT_proportion = 37 / 54
print(AT_percentage)
```

    0.6851851851851852



```python
# this can be made into a percent by multiplying by 100 
AT_percentage = AT_proportion * 100
print (AT_percentage)
```

    68.51851851851852



```python
# and I can get GC content too 
GC_percentage = 100 - AT_percentage
print(GC_percentage)
```

    31.48148148148148


2 Complementing DNA


```python
# what is the reverse compliment of this sequence? 
# ACTGATCGATTACGTATAGTATTTGCTATCATACATATATATCGATGCGTTCAT
# this is the same sequence as before so I don't need to make another variable 
```


```python
# I need to replace each letter with its compliment, without double replacing...
print(sequence.replace("A" "T" "G" "C", "T" "A" "C" "G"))
```

    ACTGATCGATTACGTATAGTATTTGCTATCATACATATATATCGTACGGTTCAT



```python
# That doesn't work
# I went into the solutions to figure this one out because I didn't have any ideas 
```


```python
# You can replace each with a lowercase, then make them all upper case
replace_1 = sequence.replace("A", "t")
replace_2 = replace_1.replace("T", "a")
replace_3 = replace_2.replace("C", "g")
replace_4 = replace_3.replace("G", "c")
# check the string
print(replace_4)
```

    tgactagctaatgcatatcataaacgatagtatgtatatatagctacgcaagta



```python
# ok that seems right, now to make it uppercase 
sequence_compliment = replace_4.upper()
print(sequence_compliment)
```

    TGACTAGCTAATGCATATCATAAACGATAGTATGTATATATAGCTACGCAAGTA


Restriction fragment lengths


```python
# calculate the length of the fragments in my sequence when cut by EcoRI 
# which cuts here: G*AATTC
```


```python
# I need to find where GAATTC is in the sequence 
sequence.find("GAATTC")
```




    -1




```python
# hmmm this says it doesn't exist
# let me make sure the sequence is the right one 
sequence_2 = "ACTGATCGATTACGTATAGTAGAATTCTATCATACATATATATCGATGCGTTCAT"
```


```python
# now does my find work?
sequence_2.find("GAATTC")
```




    21




```python
# great, my mistake
# ok so my guess is that the G is position 21, so I'll actually want to break it up after the G 
# this can be done by makeing a substring 
fragment_1 = sequence_2[0:22]
# does this preseve the G?
print(fragment_1)
```

    ACTGATCGATTACGTATAGTAG



```python
# yes! great, now to print the other fragment 
fragment_2 = sequence_2[23:100]
# the 100 is not the real end, but it is just a place holder 
print(fragment_2)
```

    ATTCTATCATACATATATATCGATGCGTTCAT



```python
# hmmm not quite, just missing an A 
fragment_2 = sequence_2[22:100]
print(fragment_2)
```

    AATTCTATCATACATATATATCGATGCGTTCAT



```python
# perfect!
```

Splicing out introns, part one


```python
# separate out coding exons from this sequence:
# ATCGATCGATCGATCGACTGACTAGTCATAGCTATGCATGTAGCTACTCGATCGATCGATCGATCGATCGATCGATCGATCGATCATGCTATCATCGATCGATATCGATGCATCGACTACTAT
```


```python
sequence_3 = "ATCGATCGATCGATCGACTGACTAGTCATAGCTATGCATGTAGCTACTCGATCGATCGATCGATCGATCGATCGATCGATCGATCATGCTATCATCGATCGATATCGATGCATCGACTACTAT"
print(sequence_3)
```

    ATCGATCGATCGATCGACTGACTAGTCATAGCTATGCATGTAGCTACTCGATCGATCGATCGATCGATCGATCGATCGATCGATCATGCTATCATCGATCGATATCGATGCATCGACTACTAT



```python
# first exon is from the first character to the 63rd 
first_exon = sequence_3[0:64]
print(first_exon)
```

    ATCGATCGATCGATCGACTGACTAGTCATAGCTATGCATGTAGCTACTCGATCGATCGATCGAT



```python
# I am pretty sure that is right, but not completely sure 
# second exon is from the 91st character to the end 
second_exon = sequence_3[93:200]
print(second_exon)
```

    ATCGATCGATATCGATGCATCGACTACTAT


Splicing out introns, part two


```python
# using that same sequence and coding/non-coding, what is the percentage of both?
# length of full sequence 
seq_len = len(sequence_3)
print(seq_len)
```

    123



```python
# length of exons 
exon_1_len = len(first_exon)
exon_2_len = len(second_exon)
# combine lengths 
exon_total_len = exon_1_len + exon_2_len
print(exon_total_len)
```

    94



```python
# calculate the proportion exon 
prop_exon = 94 / 123
# calculate percentage exon 
percent_exon = prop_exon * 100
print(percent_exon)
```

    76.42276422764228


Splicing out introns, part three


```python
# I need to make all the exons as uppercase, and introns as lowercase
# separate out the intron
intron = sequence_3[64:93]
intron_lower = intron.lower()
print(intron_lower)
```

    cgatcgatcgatcgatcgatcatgctatc



```python
# check that this is the right length 
len(intron_lower)
```




    29




```python
94 + 29
```




    123




```python
# good 
# now combine the sequences and print them 
print(first_exon + intron_lower + second_exon)

```

    ATCGATCGATCGATCGACTGACTAGTCATAGCTATGCATGTAGCTACTCGATCGATCGATCGATcgatcgatcgatcgatcgatcatgctatcATCGATCGATATCGATGCATCGACTACTAT

