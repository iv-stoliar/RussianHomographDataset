# Russian Homograph Dataset

This repository provides a labeled dataset for training Russian homograph disambiguation models. If you use this data in your research, I would be grateful if you could share a link to this repository.

The dataset contains roughly **84,400 contexts** for **56 homograph pairs** (_за́мок – замо́к_, _бе́рег – берёг_, …) and **1 homograph triad** (_се́ла – сёла – села́_). My goal was not to cover all homographs in Russian but to create a balanced and diverse dataset for some common Russian homographs.

Contexts were extracted from the [Russian National Corpus](https://ruscorpora.ru/) (many thanks to its authors and contributors) and manually annotated. The dataset includes examples from Russian fiction, news articles, scientific publications and social media posts.

## Organization

The dataset covers following groups of homographs:

* **Lexical** (morphosyntactically congruent) homographs belong to different lexemes and have identical morphosyntactic values, e.g. _за́мок_ ‘castle (sg, nom)’ vs _замо́к_ ‘lock (sg, nom)’, _за́мка_ ‘castle (sg, gen)’ vs _замка́_ ‘lock (sg, gen)’, etc. The dataset includes 4 pairs of lexical homographs.

* **Mixed** (morphosyntactically incongruent) homographs belong to separate lexemes and have different morphosyntactic values. For the sake of convenience, this group was divided in two: noun homographs, e.g. _ду́ша_ ‘douche (sg, gen)’ vs _душа́_ ‘soul (sg, nom)’, and homographs belonging to different parts of speech, e.g. _бе́рег_ ‘shore, coast (noun, sg, nom/acc)’ vs _берёг_ ‘I/you/he protected (verb, past, sg, masc)’. The dataset contains 8 pairs of mixed noun homographs; as for mixed homographs of different POS, there are 9 pairs and 1 homograph triad (_се́ла – сёла – села́_) in the dataset.

* **Intraparadigmatic** homographs are homographic wordforms belonging to the same lexeme, i.e. having different morphosyntactic values but identical lexical meaning, e.g. _го́рода_ ‘city (sg, gen)’ vs _города́_ ‘cities (pl, nom/acc)’. Homographs of this type are grouped into 5 subgroups, each of which presents the same grammatical correlation. There are 7 pairs of homographs in each subgroup; overall, there are 35 intraparadigmatic homographs in the dataset.

A detailed description of each homograph pair is given in the file `homographs_info.tsv` (phonemic transcriptions are based on the [IPA for Russian](https://www.cambridge.org/core/journals/journal-of-the-international-phonetic-association/article/russian/55589EC639ADEF1764B5ECD0B76970FA). As for the homograph triad _се́ла – сёла – села́_, all the information is put in a separate file `села_info.tsv`.

## Data Format

The dataset comes in TSV files for each homograph pair (triad) with the following fields:

* **Index** – number of the context in this file;

* **Homograph** – the homograph word itself, in lower case, without the stress mark or the restored letter ё (which is always stressed in Russian), e.g. _замок_, _берег_, _сел_;

* **Context** – context (i.e. 1-3 sentences) including the homograph;

* **TargetWord** – homograph that is spelled in the way it is used in context, e.g. _замок_, _Замок_, _ЗАМОК_;

* **Label** – class label (target variable) for this context. In the case of mixed homographs, the label is simply the homograph with stress marked with + after the stressed vowel and/or the restored letter ё (e.g. _ду+ша_, _берё+г_, _сёл_). In the group of lexical homographs, the label refers to the lexico-semantic variant of the lexeme in question: label 1 indicates wordforms belonging to the first variant, e.g. _за́мок_, _за́мка_, _за́мку_… whereas label 2 stands for the second variant, e.g. _замо́к_, _замка́_, _замку́_… Finally, in all subgroups of intraparadigmatic homographs, the label marks the morphosyntactic value of the homographic wordform: label 1 is used with homographs in the genitive (or accusative) singular (_до́ктора_, _жены́_, _ме́ста_, …) while label 2 denotes nominative (or accusative) plural (_доктора́_, _жёны_, _места́_, …).

**P.S.** The dataset is organized in a way I found convenient for my Master’s thesis. If you use the data in your research, feel free to change it according to your needs ;) For any questions or commentaries, don't hesitate to contact me: https://t.me/jan_stoliar, stoliarov.iv@gmail.com
