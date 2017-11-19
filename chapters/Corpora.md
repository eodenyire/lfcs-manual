## Corpora

Here are the corpora (plural of "corpus") currently available on {{ book.server }}.

* Metu Turkish Corpus
* _Milliyet_ Corpus
* Boun Corpus

To see where they are stored, check the environment variable `CORPORA_PATH`:

```
echo ${CORPORA_PATH}
```

To see the details, change to their directories and have a look at the `README` files. In this tutorial we will use Metu Turkish Corpus. You will find different formats (html, token per line, sentence per line) and encodings (ASCII, UTF-8).


The best way to work on a corpus is to create a symbolic link to the files you want to work on. Assume I will do some search on Metu Turkish Corpus. To check which versions are under which files,

```
cat ${CORPORA_PATH}/MetuTurkishCorpus/README
```

This will show the available files and brief descriptions of their contents. Assume, I want to work on the sentence-per-line format with UTF-8 encoding. I do,

```
ln -s ${CORPORA_PATH}/MetuTurkishCorpus/mtc-spl-UTF-8.txt  corpus 
```

You can provide any name you like instead of `corpus`. You may check the count of words, lines and characters in the corpus by the `wc` tool:


```
wc corpus
```

To see the first 10 lines, do 

```
head corpus
```

All NLP-resources, including the corpora, are write-protected, you cannot change their contents. This is a precaution for accidental changes to the common resources available for every user in the system. So you do not need to worry about the files you linked to. After you're done, you can delete the link you've created, nothing will happen to the corpus file you linked to.


### Searching

The most straightforward way to search corpora is to use `grep`; the following command searches for lines that contain verbs where the so-called past tense marker `-DI` follows the so-called conditional marker `-sA` in Turkish.

```
egrep '\w+s[ea]yd[iı]' corpus
```

Note that we had `egrep`, which is shorthand for `grep -E`.  The matched parts should get highlighted, if they don't, use the option `--color=always`. You can also get some context before and/or after the matched line with `-A 2 -B 2`, etc.

If you want to be able to inspect the output by scrolling up and down, pipe the output of `egrep` to `less`; all in action would look like: 

```
egrep --color=always -A 2 -B 2 '\w+s[ea]yd[iı]' corpus | less -r
```

To have your results stored in a file, switch of the color and divert to output to a file:

```
egrep --color=never -A 2 -B 2 '\w+s[ea]yd[iı]' corpus > my_results.txt
```

To use `grep` effectively, spend an hour or so on a tutorial. [Here](http://opensourceforu.com/2012/06/beginners-guide-gnu-grep-basics-regular-expressions/) is one that looks useful; or just do `man grep`. 
