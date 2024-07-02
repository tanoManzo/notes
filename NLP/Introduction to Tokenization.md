Split text into meaningful fundamental units:
- Tokens are tricky. (raw text)
- Tokens are tricky . (words)
- Token s _ are _ trick _ y . (morphemes)
- t oʊ k ə n z _ ɑː _ ˈt r ɪ k i. (phonemes, for STT)
- T o k e n s _ a r e _ t r i c k y . (character)

In SentencePiece unicode characters are grouped together using either a unigram language model or BPE, byte-pair encoding.

## BPE Algorithm

Example data
```
Beginners BBQ Class Taking Place in Missoula!
Do you want to get better at making delicious BBQ? You will have the opportunity, put this on your calendar now. Thursday, September 22nd join World Class BBQ Champion, Tony Balay from Lonestar Smoke Rangers. He will be teaching a beginner level class for everyone who wants to get better with their culinary skills.
He will teach you everything you need to know to compete in a KCBS BBQ competition, including techniques, recipes, timelines, meat selection and trimming, plus smoker and fire information.
The cost to be in the class is $35 per person, and for spectators it is free. Included in the cost will be either a t-shirt or apron and you will be tasting samples of each meat that is prepared.
```

```
show_vocab(vocab)

Output:
▁ B e g i n n e r s: 1
▁ B B Q: 3
▁ C l a s s: 2
▁ T a k i n g: 1
▁ P l a c e: 1
▁ i n: 15
▁ M i s s o u l a !: 1
▁ D o: 1
▁ y o u: 13
▁ w a n t: 1
▁ t o: 33
▁ g e t: 2
▁ b e t t e r: 2
▁ a t: 1
▁ m a k i n g: 2
▁ d e l i c i o u s: 1
▁ B B Q ?: 1
▁ Y o u: 1
▁ w i l l: 6
▁ h a v e: 4
▁ t h e: 31

```
It takes in the current vocab word-frequency dictionary and the fraction, frac_merges, of the total vocab_size to merge characters in the words of the dictionary, num_merges times. Then for each merge operation it get_stats on how many of each pair of character sequences there are. It gets the most frequent pair of symbols as the best pair. Then it merges that pair of symbols (removes the space between them) in each word in the vocab that contains this best (= pair). Consequently, merge_vocab creates a new vocab, v_out. This process is repeated num_merges times and the result is the set of SentencePieces (keys of the final sp_vocab).

```
# encode: text => id
print(sp.encode_as_pieces(s0))
print(sp.encode_as_ids(s0))

# decode: id => text
print(sp.decode_pieces(sp.encode_as_pieces(s0)))
print(sp.decode_ids([12847, 277]))

Output:
['▁Beginn', 'ers', '▁BBQ', '▁Class', '▁', 'Taking', '▁Place', '▁in', '▁Miss', 'oul', 'a', '!']
[12847, 277, 15068, 4501, 3, 12297, 3399, 16, 5964, 7115, 9, 55]
Beginners BBQ Class Taking Place in Missoula!
Beginners

```