## Style Transfer from Non-parallel Text by Cross-Alignment

With two non-parallel corpora (compared to NMT with thousands of parallel examples)
Important implications for NLP/NLU, bc it’s much more realistic.

Style transfer is well explored in CV. 
Challenges for NLP:
* semantic Content must be preserved
* discrete tokens. not continuously optimizable

Learn latent representations, split them by style and content.

Same corpora has different content, same style.

Autoencoder:
Encoder: takes latent style, latent content, and a sentence
Generator: takes two corpora with different styles

"Discriminator causes them to be alighned"

Sentiment modification also works!

Whoa - also deciphers ciphertext.
