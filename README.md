# 𝓜𝓪𝓻𝓴𝓸

> A markdown parser with high extensibility.

[![PyPI](https://img.shields.io/pypi/v/marko.svg?logo=python&logoColor=white)](https://pypi.org/project/marko/)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/marko.svg?logo=python&logoColor=white)](https://pypi.org/project/marko/)
[![Documentation Status](https://img.shields.io/readthedocs/marko-py.svg?logo=readthedocs)](https://marko-py.readthedocs.io/en/latest/?badge=latest)
[![CommonMark Spec](https://img.shields.io/badge/CommonMark-0.29-blue.svg)][spec]

![Build Status](https://github.com/python-poetry/poetry/workflows/Tests/badge.svg)
[![codecov](https://codecov.io/gh/frostming/marko/branch/master/graph/badge.svg)](https://codecov.io/gh/frostming/marko)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/b785f5b3fa7c4d93a02372d31b3f73b1)](https://www.codacy.com/app/frostming/marko?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=frostming/marko&amp;utm_campaign=Badge_Grade)

Marko is a markdown parser written in pure Python that complies [CommonMark's spec v0.29][spec].
It is designed to be highly extensible, see [Extend Marko](#extend-marko) for details.

Marko requires Python2.7, Python 3.5 or higher.

## Why Marko

Among all implementations of Python's markdown parser, it is a common issue that user can't easily extend it to add his own features. Furthermore, [Python-Markdown][pymd] and [mistune][mistune] don't comply CommonMark's spec. It is a good reason for me to develop a new markdown parser.

Respecting that Marko complies CommonMark's spec at the same time, which is a super complicated spec, Marko's performance will be affected. However, using a parser
which doesn't comply the CommonMark spec may give you unexpected rendered results from time to time.
A benchmark result shows that Marko is 3 times slower than [Python-Markdown][pymd], but a bit faster than [Commonmark-py][cmpy], much slower than [mistune][mistune]. If performance is a bigger concern to you than spec compliance, you'd better choose another parser.

[spec]: https://spec.commonmark.org/0.29/
[pymd]: https://github.com/waylan/Python-Markdown
[mistune]: https://github.com/lepture/mistune
[cmpy]: https://github.com/rtfd/CommonMark-py

## Use Marko

The installation is very simple:

    $ pip install marko

And to use it:

```python
import marko

print(marko.convert(text))
```

Marko also provides a simple CLI, for example, to render a document and output to a html file:

    $ cat my_article.md | marko > my_article.html

## Extensions

It is super easy to use an extension:

```python
from marko import Markdown
from marko.ext.footnote import FootnoteExtension
# Add footnote extension
markdown = Markdown(extensions=[FootnoteExtension])
# Alternatively you can register an extension later
markdown.use(FootnoteExtension)
```
Marko is shipped with 3 extensions: `marko.ext.toc.TocExtension`, `marko.ext.footnote.FootnoteExtension`,
`marko.ext.pangu.PanguExtension`. They are not included in CommonMark's spec but are common in other markdown parsers.

Marko also provides a Github flavored markdown parser which can be found at `marko.ext.gfm.gfm`.

Please refer to [Extend Marko](https://marko-py.readthedocs.io/en/latest/extend.html) about how to
write your own extension.

## License

Marko is released under [MIT License](LICENSE)

## [Change Log](CHANGELOG.md)
