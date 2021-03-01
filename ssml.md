# SSML

Quick cheatsheet on the SSML used in Amazon Polly.

## <speak>

Base element.


## <break>

A pause in the audio rendering.

* `strength`:
    * `none` — remove a normal pause
    * `medium` — short pause, such as after a comma
    * `strong` — longer pause, such as after a sentence
    * `x-strong` — longest pause, such as after a paragraph
    * `NNms` — pause in milliseconds
    * `NNs` — pause in seconds


## <emphasis>

Changes the speaking to rate and volume.

* `level`:
    * `strong` — slower rate, increased volume
    * `moderate` — slower rate, increased volume
    * `reduced` — speeded rate, decreased volume


## <lang>


## <mark>

Place a custom tag.


## <p>

Pause between paragraphs.


## <phoneme>



## <prosody>

Control volume, rate, or pitch.

* `volume`:
    * `default`
    * `silent`, `x-soft`, `soft`, `medium`, `loud`, `x-loud`
    * `+NNdB`, `-NNdB`
* `rate`:
    * `x-slow`, `slow`, `medium`, `fast`, `x-fast`
    * `NN%`
* `pitch`:
    * `default`
    * `x-low`, `low`, `medium`, `high`, `x-high`
    * `+NN%`, `-NN%`
* `amazon:max-duration`
    * `NNms`, `NNs`


## <s>

Pause between sentences.


## <say-as>

* `interpret-as`:
    * `characters`, `spell-out`
    * `cardinal`, `number`
    * `ordinal`
    * `digits`
    * `fraction`
    * `unit`
    * `date`
    * `time`
    * `address`
    * `expletive`
    * `telephone`


## <w>

Customise the pronunciation of indiviual words.

* `role`:
    * `amazon:VB` — verb
    * `amazon:VBD` — past-tense verb
    * `amazon:DT` — determiner
    * `amazon:IN` — proposition
    * `amazon:JJ` — adjective
    * `amazon:NN` — noun
    * `amazon:DEFAULT` - default sense of the word (eg bass the guitar)
    * `amazon:SENSE_1` — alternative sense (eg bass the fish)


## <amazon:breath>

* `duration`:
    * default, x-short, short, medium, long, x-long
* `volume`:
    * default, x-soft, soft, medium, loud, x-loud


## <amazon:auto-breaths>


