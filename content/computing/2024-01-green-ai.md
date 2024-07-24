---
title: toward sustainable AI?
date: 2024-03-01 23:00:00
description: |
  Artificial intelligence (AI) promises revolutionary advancements across various sectors,
  such as healthcare, finance, and environmental science.
  AI's capacity to analyze complex datasets and perform
  **early cancer detection** in healthcare, **predict stock market trends**
  in high-frequency trading, or **optimize energy consumption** in
  large data centers showcases this transformative potential.
---

Artificial intelligence (AI) promises revolutionary advancements across various sectors,
such as healthcare, finance, and environmental science.
AI's capacity to analyze complex datasets and perform
**early cancer detection** in healthcare, **predict stock market trends**
in high-frequency trading, or **optimize energy consumption** in
large data centers showcases this transformative potential.



However, **a critical yet overlooked issue** lies beneath this mask:
**the significant environmental impact of training large AI models**.
The training process uses **expansive datasets** and
**increasingly complex algorithms**, which
**require immense computational power**.

![
  A data center in _Odense_, Denmark.
](odense-data-center.webp){centered}

This issue highlights the multifaceted problem of unsustainable energy
[consumption and a layer of inequality when only a few companies can
afford to train such large models.](https://aclanthology.org/P16-2096/)
This dichotomy between the promise of AI and its environmental impact
calls for a critical reassessment of our current approaches to developing
AI models. It highlights a need to set up regulations to ensure long-term
sustainability. This essay explores the nuances around this issue and
motivates the needed actions.

## The Environmental Cost of AI Progress

**The sheer scale of the amount of energy needed to train large AI models
such as Generative Pretrained Transformers (GPT) is astounding**.
It is estimated that **training a single model can emit as much carbon as five cars**
in their entire lifetimes[^five-cars]. GPT-3, the predecessor to GPT-4,
emitted an estimated 126 cars’ worth of carbon during its training phase,
yet it pales compared to GPT-4, a model with nearly a thousand times more parameters.
The progression from GPT-3 to GPT-4 exemplifies how **rapid advancements** in AI capabilities
**correspond with escalations in environmental costs**. Unsurprisingly, Sam Altman,
OpenAI’s CEO, recently expressed his intent to raise trillions of dollars
to procure more computational power for training AI models[^chips-chips-chips].

![
  OpenAI CEO, Sam Altman,
  wants to raise trillions of dollars
  for training AI models.
](sama.webp){centered}

The University of Massachusetts at Amherst conducted a study which found that that
**training a single AI model could consume** more than 626,000 **kWh**
of electricity, equivalent to **nearly five times the annual electricity
consumption of an average American household**[^energy-policy].
**We need to emphasize these financial and environmental factors**
and actively push for more energy-efficient AI research and development approaches.

## Parallels to Other Industries: Missing Pieces

The environmental implications of AI progress echo historical
challenges in other industries, such as the automotive industry,
which faced similar concerns when the number of personal
cars used worldwide increased in the 1950s and early 1960s.
In 1965, the state of California imposed emission standards on
all automotive vehicles in an attempt to control the situation[^watson].

In the years since, advances in engineering led to the development of
more fuel-efficient and, eventually, electric vehicles. At the same time,
international agreements and national regulations, such as the Kyoto Protocol
and the European Union’s emission standards[^gdpr], further incentivized
reductions in carbon emissions. This transformation was driven by
governmental policies, shifting consumer preferences toward more
environmentally friendly vehicles, and intentioned innovations
in green transportation methods such as Tesla in recent years.

Similarly, a combination of technological advancements,
such as the development of more efficient computing architectures and algorithms,
paired with more robust regulatory frameworks and
improved awareness among consumers and developers about the environmental impacts
of AI, could catalyze a shift toward more sustainable AI.
Companies including Google, Apple, and OpenAI have made commitments
to power all their operations with renewable energy and
reduce the carbon footprints of their AI models.

However, who is holding them accountable? Much of the regulatory framework
is nonexistent, which needs to change.

## The AI Industry’s “Not My Problem” Stance

![
  Karen Hao, AI reporter,
  <br>
  Hao calls for better energy sustainability in AI.
](karen-hao.jpeg){inline style="width: 40%; float: right; margin: 2em;"}

Worse yet, the AI industry prioritizes short-term gains in model performance
(accuracy) over environmental sustainability, adopting a "not my problem"
stance that ignores broader implications. This attitude ignores the
interconnectedness of environmental challenges, downplaying the carbon
emissions accompanying the development and training of large models.
Schwartz et al. point out that even the minification of existing
models&mdash;such as Google’s recent reengineering of its [Gemini][gemini]
model to [Gemma][gemma], a model with fewer parameters, hence
less computational costs[^gemma]&mdash;tends to be motivated by the need to have models be more accessible on smaller computational devices such as personal computers and phones, not the need to have them be more energy efficient[^green-ai]. Hovy and Spruit identify this lack of ethical awareness and discourse as concerning[^nlp-social-impact].

## Multi-Faceted Solutions to an Industry-Wide Issue

Prompt action is needed. First, governmental regulation must catch up with the status quo in the AI industry. However, this poses a unique challenge for state and federal governments: many big AI companies have international operations. Global bodies such as the UN could be better suited to set up regulatory frameworks. The European Union’s General Data Protection Regulation (GDPR) could be a good precedent for setting and enforcing such regulations. Nevertheless, the EU has faced difficulties in managing multinational tech giants like Meta, illustrating the complexity of enforcing standards across borders [^stochastic-parrots].

Furthermore, the AI sector must embrace "Green AI," advocating for research that achieves novel results without escalating computational costs, thereby reducing the carbon footprint. This shift towards including energy efficiency as a primary evaluation criterion, alongside accuracy, would ensure that the energy conversation does not get overshadowed by vanity metrics such as a few extra percentage points on an accuracy benchmark, especially when such an improvement comes with a disproportionate reduction in energy efficiency[^green-ai].

![
  The European Union has faced unique challenges in trying to enforce
  regulations across borders.
  <br>
  Any regulatory body will likely face similar issues.
](gdpr.jpeg){centered}

The transition to efficient AI also hinges on technological innovation: companies must intentionally seek to create more efficient models, not just more accurate ones. This very closely links to consumer influence. If the user only cares about a model’s accuracy, companies will do their best to improve it. However, users caring about other metrics, such as energy efficiency would force companies to attend to their performance on those other metrics.

## Conclusion

The AI industry must urgently balance its pursuit of technological advancement
with environmental responsibility.
The drive for more powerful AI models results in significant energy consumption and carbon emissions, raising critical ethical concerns. The sector must adopt sustainable practices to ensure that the development of AI technologies does not come at the expense of our planet's health. Action and perspective shifts are needed from all involved: companies, consumers, and regulators.

[^gemma]: Banks, Jeanine.
  [Gemma: Introducing New State-of-the-Art Open Models](https://blog.google/technology/developers/gemma-open-models/).  
  Google, 21 Feb. 2024.

[^stochastic-parrots]: Bender, E. M., Gebru, T. (2021).
  [On the Dangers of Stochastic Parrots: Can Language Models Be Too Big? :parrot:](https://www.turing.ac.uk/events/dangers-stochastic-parrots)

[^chips-chips-chips]: Cheng, Michelle.
  [Sam Altman’s 7-Trillion AI Chip Project Might Not Be Very
  Realistic](https://qz.com/openai-sam-altman-ai-chip-ambitions-1851261305).”  
  Quartz, 18 Feb. 2024.

[^five-cars]: Hao, Karen. “[Training a Single AI Model
  Can Emit as Much Carbon as
  Five Cars in Their Lifetimes](https://www.technologyreview.com/2019/06/06/239031/training-a-single-ai-model-can-emit-as-much-carbon-as-five-cars-in-their-lifetimes/.).”  
  MIT Technology Review, 6 June 2019.

[^nlp-social-impact]: Hovy, Dirk, and Shannon L. Spruit.
  [The Social Impact of Natural Language Processing](https://aclanthology.org/P16-2096/).  
  Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics, 2016.

[^green-ai]: Schwartz, R., Dodge, J., Smith, N. A., & Etzioni, O. (2019). Green AI.
  arXiv preprint arXiv:1907.10597.

[^energy-policy]: Strubell, E., Ganesh, A., & McCallum, A. (2019).
  Energy and Policy Considerations for Deep Learning in NLP.

[^gdpr]: The European Union. [General Data Protection Regulation (GDPR) &mdash;
  Official Legal Text](https://gdpr-info.eu/). 13 July 2016.

[^watson]: Watson, Ann Y., et al. [Automotive
  Emissions](https://www.ncbi.nlm.nih.gov/books/NBK218144/). NCBI Bookshelf, 1 Jan. 1988.

[gemini]: https://deepmind.google/technologies/gemini/#introduction
[gemma]: https://blog.google/technology/developers/gemma-open-models
