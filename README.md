# Anth

Anth is a simple command line interface to the [ACL anthology](https://aclanthology.coli.uni-saarland.de/), designed to conveniently look up citations and append them to your bibtex file.


# Installation

1. Copy `anth` somewhere in your PATH, e.g. `/usr/local/bin` or `~/bin`.
2. Make it executable, if it isn't already: `chmod +x /usr/local/bin/anth`.

# Usage

```
$ ls
paper.tex  references.bib
$ anth sonse entity
Found 2 .bib files:

    1	Shimaoka, Sonse and Stenetorp, Pontus and Inui, Kentaro and Riedel, Sebastian
	2017
	Neural Architectures for Fine-grained Entity Type Classification
	https://aclanthology.coli.uni-saarland.de/papers/E17-1119/e17-1119.bib

    2	Shimaoka, Sonse and Stenetorp, Pontus and Inui, Kentaro and Riedel, Sebastian
	2016
	An Attentive Neural Architecture for Fine-grained Entity Type Classification
	https://aclanthology.coli.uni-saarland.de/papers/W16-1313/w16-1313.bib

Select entry [1-2]: 1
bibkey: shimaoka2017neural

Appended to references.bib

@InProceedings{shimaoka2017neural,
author = "Shimaoka, Sonse and Stenetorp, Pontus and Inui, Kentaro and Riedel, Sebastian",
title = "Neural Architectures for Fine-grained Entity Type Classification",
booktitle = "Proceedings of the 15th Conference of the European Chapter of the Association for Computational Linguistics: Volume 1, Long Papers",
year = "2017",
publisher = "Association for Computational Linguistics",
pages = "1271--1280",
location = "Valencia, Spain",
bibkey = "E17-1119"
}
```

By default, anth will append the bib entry to the first `.bib` file found in the current directory. Alternatively, you can use the `--bibfile` argument to specify the .bib file the citation should be appended to. If you maintain a global .bib file you use for all your citations, you can also edit the `anth`` script and enter a default path:

```Python
    a.add_argument(
        "--bibfile", type=Path,
		default="/path/to/my/humongous/bibfile.bib",
		help="your bibtex file to which the .bib file found on the "
		"anthology will be appended")
```

There are a couple more options, check them with:

```
$ anth --help
```

Finally, there is `qanth` (quick anth), which, like Google's "I feel lucky" button will display the first .bib file found for the given query:

```
$ qanth sonse entity | tee -a references.bib
@InProceedings{E17-1119,
  author = 	"Shimaoka, Sonse
		and Stenetorp, Pontus
		and Inui, Kentaro
		and Riedel, Sebastian",
  title = 	"Neural Architectures for Fine-grained Entity Type Classification",
  booktitle = 	"Proceedings of the 15th Conference of the European Chapter of the Association for Computational Linguistics: Volume 1, Long Papers",
  year = 	"2017",
  publisher = 	"Association for Computational Linguistics",
  pages = 	"1271--1280",
  location = 	"Valencia, Spain",
  url = 	"http://aclweb.org/anthology/E17-1119"
}
```
