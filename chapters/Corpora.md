## Corpora

Here is a brief description and how-to's for the corpora available on {{ book.server }} 

* Metu Turkish Corpus
* _Milliyet_ Corpus
* Boun Corpus


When you want to work on a corpus and will not have to make any changes to the corpus, best is to first construct a symbolic link to the corpus file.

```
ln -s /srv/nlp-resources/corpora/<path to your file> <path of the symbolic link>
```

For example let's assume I want to work on METU Turkish Corpus, I first construct a link:

```
ln -s ...
```

All NLP-resources, including the corpora, are write-protected, you cannot change their contents. This is a precaution for accidental changes to the common resources available for every user in the system. If you want to change the contents of any resource, you need to copy it to your account. 


### Searching


```
grep ... 
```

