---
title: Neural formant synthesis with differentiable resonant filters
description: Framework for controllable speech synthesis using phonetically meaningful speech parameters.
permalink: /DDSPneuralformants
---
# Neural formant synthesis with differentiable resonant filters

##### [Pablo Pérez Zarazaga][pablo_profile], [Zofia Malisz][zofia_profile], [Gustav Eje Henter][gustav_profile], [Lauri Juvela][lauri_profile]

<head> 
<link rel="apple-touch-icon" sizes="180x180" href="favicon/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="favicon/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="favicon/favicon-16x16.png">
<link rel="manifest" href="/site.webmanifest">
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">
</head>

<!--[NF_link]: https://github.com/perezpoz/NeuralFormants
[WN_link]: https://github.com/ljuvela/GlotNet
[paper_link]: https://arxiv.org/abs/2303.07442
-->
[NF_link]: https://perezpoz.github.io/404
[WN_link]: https://perezpoz.github.io/404
[paper_link]: http://arxiv.org/abs/2306.01957
[gustav_profile]: https://people.kth.se/~ghe/
[pablo_profile]: https://www.kth.se/profile/pablopz
[zofia_profile]: https://www.kth.se/profile/malisz
[lauri_profile]: https://research.aalto.fi/en/persons/lauri-juvela

[hifi_link]: https://github.com/jik876/hifi-gan
[GN_link]: https://github.com/ljuvela/GlotNet

## Summary

The goal of this work is to develop a speaker-independent speech synthesis system driven by a small set of phonetically meaningful speech parameters.

The system is built with a similar structure to the source-filter model, allowing us to independently inspect and manipulate the spectral envelope and glottal excitation.

The system provides a controllable environment where it is possible to manipulate the different individual speech parameters to generate a realistic speech signal.

## Visual overview

![Neural formant pipeline follwing the source-filter model architectrue](./images/NeuralFormants_Diagram.pdf "Neural formant pipeline follwing the source-filter model architectrue.")