# A Comparison of Text Selection Algorithms for Sequence-to-Sequence Neural TTS

*By [Stefan Taubert](https://github.com/stefantaubert), [Jasmin Sternkopf](https://github.com/jasminsternkopf), [Stefan Kahl](https://github.com/kahst) and Maximilian Eibl*

## Introduction

In this repository, supplementary material to our paper can be found:

- nine audio examples for each model
- detailed results which were presented in the figures and tables
- experimental setup

## Audio examples

We included nine audio examples for each experiment to have the possibility to subjectively compare them to their corresponding MCD and PEN results.
For this purpose, we first manually preselected all complete sentences from the validation set. Then, we applied three *Greedy* epochs to these sentences to cover all symbols several times, and obtained these nine sentences:

- 632
  - waj nɑt ɹɪliv nuɡejt baj dɹɔɪŋ mɔɹ lɑɹdʒli əpɑn ðə supɪɹiɹ̩ əkɑmədejʃən wɪtʃ mɪlbæŋk ɔfɹ̩d?
  - Why not relieve Newgate by drawing more largely upon the superior accommodation which Millbank offered?
- 1474
  - kɹajz ʌv mɹ̩dɹ̩! mɹ̩dɹ̩! wɹ̩ naw ɹejzd, ænd ædəd ɡɹejtli tə ðə hɔɹɹ̩z ʌv ðə sin.
  - Cries of Murder! murder! were now raised, and added greatly to the horrors of the scene.
- 1541
  - dʒʌdʒɪz ɑn əsajz wɹ̩ sætəsfajd wɪð sɪmpli ɹəkɔɹdɪŋ ə sɛntəns ʌv dɛθ əɡɛnst əfɛndɹ̩z hum ðej dɪd nɑt θɪŋk dɪzɹ̩vd ðə ɪkstɹim pɛnəlti.
  - Judges on assize were satisfied with simply recording a sentence of death against offenders whom they did not think deserved the extreme penalty.
- 1640
  - bʌt waj ʃʊd aj ɹɪpit ðə howl?
  - But why should I repeat the whole?
- 1670
  - bʌt wʌt ɑɹ ðə filɪŋz ʌv ðowz hu tejk pɑɹt ɪn ɪt?
  - But what are the feelings of those who take part in it?
- 1846
  - bʌt ðej pɹəsidəd ɪn ɔl sɪɹiəsnəs, ænd wʊd hæv ʃɹʌŋk fɹʌm now awtɹejdʒ ɔɹ ətɹɑsəti ɪn fɹ̩θɹ̩əns ʌv ðɛɹ fulhɑɹdi ɛntɹ̩pɹajz.
  - But they proceeded in all seriousness, and would have shrunk from no outrage or atrocity in furtherance of their foolhardy enterprise.
- 1969
  - hi wɛnt fɹʌm nuɡejt fɹ̩st tə bɛθlɪhɛm, fɹʌm wɪtʃ hi wɑz ɹimuvd tə bɹɔdmʊɹ ɑn ðə owpənɪŋ ʌv ðə ɡɹejt kɹɪmənəl lunətɪk əsajləm æt ðæt plejs.
  - He went from Newgate first to Bethlehem, from which he was removed to Broadmoor on the opening of the great criminal lunatic asylum at that place.
- 2808
  - æftɹ̩ dʒʌdʒmənt wɑz pæst ʃi ɹɪpitɪdli kɹajd awt ʃejm!
  - After judgment was passed she repeatedly cried out Shame!
- 7262
  - sɪməlɹ̩li, vɹ̩dʒɪnjə dejvəs hæd nɑt bɪn ʃown pɪktʃɹ̩z ʌv ɛniwʌn pɹajɹ̩ tə ðə lajnʌp ænd hæd nɑt sin iðɹ̩ tɛləvɪʒən ɔɹ ðə nuzpejpɹ̩z dʊɹɪŋ ðə æftɹ̩nun.
  - Similarly, Virginia Davis had not been shown pictures of anyone prior to the lineup and had not seen either television or the newspapers during the afternoon.

For each model, we took the evaluation results for the best iteration (i.e., the one which obtained the lowest median MCD) and picked for each of the nine utterances the inference seeds which achieved the lowest sum of MCD and PEN. Then, we used Tacotron to synthesize each utterance with its respective seed into mel spectrograms. Subsequently, these mel spectrograms were synthesized into audio files with WaveGlow (Models audio).

We have categorized the audio files as follows:

- **Models audio**: The synthesized audio files for each model can be found in the folder [`audio_examples/models_waveglow/`](audio_examples/models_waveglow/). We included a file named `log.txt` which contains the selected seeds and the respective MCD and PEN.
- **Original audio**: The original audio files (i.e., the ones on which Tacotron was trained) are in the folder [`audio_examples/original/`](audio_examples/original/).
- **Original audio (synthesized)**: We extracted the mel spectrograms from the original audio files and synthesized them with Waveglow. These audio files can be considered as a reference for what can be achieved with Waveglow at best. The files can be found in the folder [`audio_examples/original_waveglow/`](audio_examples/original_waveglow/).

## Detailed results

We included detailed results which were presented in the each figure and table:

- The raw data for the symbol distribution for the total set can be found under [`results/symbol_distr.csv`](results/symbol_distr.csv) (column: `TOTAL_OCCURRENCES_DISTRIBUTION_PERCENT`).
- The raw data of the linguistic coverage can be found under [`results/coverage/`](results/coverage/).
- The raw data of the MCD/PEN boxplots can be found under [`results/boxplots/`](results/boxplots/).
- The raw data of the significance test can be found under [`results/t_test.csv`](results/t_test.csv).

## Miscellaneous

The validation set can be found in [`misc/valset.csv`](misc/valset.csv).

In [`appendix.pdf`](appendix.pdf) training parameters and our experimental setup can be found.

## Acknowledgments

Funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) – Project-ID 416228727 – CRC 1410
