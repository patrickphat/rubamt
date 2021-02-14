<div align="center">

# RUBY: Universal Rule-Based Machine Translation toolkit 
**A tool for translating text from source grammar to target grammar (context-free) with corresponding dictionary.**

*Why not translate it yourself when Google Translate cannot satisfy you❓*

[![CircleCI](https://circleci.com/gh/nlp-ruby/ruby/tree/master.svg?style=svg)](https://circleci.com/gh/nlp-ruby/ruby/tree/master)
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/b4937f1f9fe0477b9fc557cbedf92b24)](https://www.codacy.com/gh/nlp-ruby/ruby?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=nlp-ruby/ruby&amp;utm_campaign=Badge_Grade)
[![Codacy Badge](https://app.codacy.com/project/badge/Coverage/b4937f1f9fe0477b9fc557cbedf92b24)](https://www.codacy.com/gh/nlp-ruby/ruby?utm_source=github.com&utm_medium=referral&utm_content=nlp-ruby/ruby&utm_campaign=Badge_Coverage)
[![PyPI version](https://badge.fury.io/py/ruby.svg)](https://badge.fury.io/py/ruby)
[![GitHub release](https://img.shields.io/github/release/nlp-ruby/ruby.svg)](https://GitHub.com/nlp-ruby/ruby/releases/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/nlp-ruby/ruby/graphs/commit-activity)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/nlp-ruby/ruby/blob/master/LICENSE)

</div>

## ⚙️ Installation
```bash
pip install ruby
```

## ✨ What is good about RUBY?
- Rule-based, deterministic translation; unlike Google Translate - giving only 1 non-deterministic result
- Using NLTK parsing interface and is built on top of already-efficient NLTK backend
- Can be used for data augmentation

## 📖 Usage
```python
from ruby import Translator

# Source sentence to be translated
src_sentences = ["I love good dogs", "I hate bad dogs"]

# Source grammar in nltk parsing style
src_grammar = """
                S -> NP VP
                NP -> PRP
                VP -> VB NP
                NP -> JJ NN
                PRP -> 'I'
                VB -> 'love' | 'hate'
                JJ -> 'good' | 'bad'
                NN -> 'dogs'
                """

# Some edit within source grammar to target grammar
src_to_target_grammar =  {
    "NP -> JJ NN": "NP -> NN JJ" # in Vietnamese NN goes before JJ
}

# Word-by-word dictionary from source language to target language
en_to_vi_dict = {
    "I":"tôi",
    "love":"yêu",
    "hate":"ghét",
    "dogs":"những chú_chó",
    "good":"ngoan",
    "bad":"hư"
    }

translator = Translator(src_grammar = src_grammar,
                        src_to_tgt_grammar = src_to_target_grammar,
                        src_to_tgt_dictionary = en_to_vi_dict)

trans_sentences = translator.translate(src_sentences) 
# This should returns ['tôi yêu những chú_chó ngoan', 'tôi ghét những chú_chó hư']
```

## ⚖️ License
This repository is using the Apache 2.0 license that is listed in the repo. Please take a look at [`LICENSE`](https://github.com/nlp-ruby/ruby/blob/master/LICENSE) as you wish.

## ✍️ BibTeX
If you wish to cite the framework feel free to use this (but only if you loved it 😊):
```bibtex
@misc{phat2020ruby,
  author = {Truong-Phat Nguyen},
  title = {RUBY: Universal Rule-Based Machine Translation NLP toolkit},
  year = {2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/nlp-ruby/ruby}},
}
```

## Contributors:
- Patrick Phat Nguyen
