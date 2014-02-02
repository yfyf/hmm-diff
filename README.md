hmm-diff
========

Semantic diffs via hidden Markov models.

This is a toy project idea for which I will hopefully one day find time.

The idea is to improve the standard UNIX `diff` utility by trying to guess the
most likely sequence of operations which have caused the changes.

The way to implement it is to consider a HMM, where the various types of
changes are the hidden states. This includes moving a line, re-ordering words
within a line, adding / deleting words to a line, etc. Also, add a state which
just says "replace the whole line" with a very low transition probability.
Assign the biggest transition probabilities to the least disruptive types of
changes in order to get as nicely looking paths as possible (e.g. a line move
is always preferred to a delete+insert).

Finally, use something like Viterbi to find the most likely sequence of edits
which produced the total diff.

This will probably not work, but it's a fun idea to try out. The complicated
question is how to relate individual line changes to "overall changes".
Introducing a concept of a block would complicate things quite a bit. Perhaps
it's possible to get away without it.
