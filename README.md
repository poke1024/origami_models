# What is this?

This is <a href="https://github.com/poke1024/origami">Origami</a>'s default OCR model that was trained to perform OCR of the <a href="http://zefys.staatsbibliothek-berlin.de/list/title/zdb/2436020X/">Berliner Börsen-Zeitung</a>. It was trained with about 10,000 lines of ground truth and using Origami's line extraction which produces dewarped non-binarized lines that tend to be somewhat wider than the lines extracted with other OCR pipelines - Origami scales lines only vertically but not horizontally.

The model was trained to understand **both Antiqua and Fraktur** and detect **two formatting styles**: bold text is marked with brackets `[]`, wide text (*Sperrtext*) is marked with curly brackets `{}`. The model was also trained to understand **integer fractions** (to some degree). Integer fractions are encoded as `<n/m>` where `n` is the numerator and `d` is the denominator.

Based on a limited evaluation, we found the CER to be at about 0.5% and the WER at about 1.7%.

Also see the examples below to see how style markers are encoded.

Details of the training process are described in the paper <a href="https://arxiv.org/abs/2008.02777">On the Accuracy of CRNNs for Line-Based OCR: A Multi-Parameter Evaluation</a>.

# Ground Truth

The ground truth that was used to train these models can be found under

https://www.dropbox.com/sh/mgsopnami242i8u/AAByAKVmdMACiQK72jhLLQ2Ka?dl=0

The data above contains page images, region and segmentation information (produced using <a href="https://github.com/poke1024/origami">Origami</a>) and finally an `annotations.db` with transcriptions (also for use with Origami).

To generate pairs of line image and texts you need to use Origami's export command (you can specify custom line height for export and binarization methods used). Alternatively you can use the following example export:

https://www.dropbox.com/s/0tvsgkh1a12xpxl/annotations-v19-h56.zip?dl=0

# Model Files

The Calamari model files are too large for this repository. They can be downloaded under

https://www.dropbox.com/sh/3e5y9vb41dggttj/AAAE2DrNfpWNz6ygIlICX3cMa?dl=0

# Examples

## Antiqua with wide style

![Example Line](/images/2436020X_1884-05-02_0_206_001.22.0.png)

```
Abg. {Hasenclever}: Es zeigt sich auch dies-
```

## Antiqua with bold style

![Example Line](/images/2436020X_1879-02-03_0_56_001.1.3.png)

```
[Konstantinopel], 2. Februar. (H. T. B.)
```

## Fraktur with both styles

![Example Line](/images/2436020X_1875-04-04_0_155_001.16.9.png)

```
[Dortmund], 3. April. (Privat-Depesche der}
```

## Integer Fractions

![Example Line](/images/2436020X_1872-02-19_0_83_010.25.31.png)

```
schen Gesellschaft für Eisenbahn-Betriebs-Material 1<7/8> %; die Actien der
```
