

# Longest Prefix Matching Word Tokenization
This repository is inspired by my old project named super-awesome-word-segmentation in the *CSS432: Information Retrieval* course. At that time group members are me, Isada Sukprapa, Naruson Srivaro, and Panthakan Maisopa.

[Notebook](https://github.com/sadanalog/word-tokenization-using-lpm/blob/initial-commit/lpm.ipynb)

### How algorithm work?

-   This is a Thai word segmentation by using the longest prefix matching.
-   It finds the longest word from the left and isolates each word into an array.
-   If the end of the sentence is reached and the current string in the buffer doesn’t have meaning, the algorithm looks back at the previous word and find the longest sub word within that word (longest word in string n in which its length is less than the size of n) replace that word with that sub-word and continue the algorithm.


### Procedures

-   Loading the NECTEC Thai corpus named as `THAI_CORPUS` (latest update of this [corpus](https://www.nectec.or.th/corpus/index.php?league=la))
    
-   Create the `CORPUS_INDEX` following the first character in the corpus (corpus is already arranged).
    
-   Checking that first character of `input_string`  match with `CORPUS_INDEX` whether or not?
    
-   If the entire word matches,  `isWord(input_word, corpus, corpus_index)`  will return  True. Otherwise, False.
-  For `plm_tokenizer(input_string, corpus, corpus_index)`, I have pointer `st` and `end` for current word, and `post_st`, `post_end` for the last word. When found the longest word of a sentence, it will save that word into a `word_list`, set new pointers.
    
- In a condition that the appended word is not correct (mean that it make the rest cannot fit). `go_back` feature will consider the second prefix longest word using prior pointers, and load the`check_point` -> repeat until all are satisfied.

### Performance

Does it work correctly?
-  It works correctly for separating terms, but not work accurately. This is the drawback of the pure longest matching algorithm.

There is any restriction?
- Yes, when it consists of a misspelling word (not in the corpus), the tokenizer will halt. So, let's assume that the corpus has covered every word in the language and the `input_string` needs to be correct.

Time-complexity?
- Creating the corpus index counts as `n`. For each word checking, `nlogn`. Therefore, `isWord` function -> time-complexity is `n^2`. Unfortunately, the time-complexity of `plm_tokenize`  is depended on a system input.

---
