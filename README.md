NLP bash oneliners for markov chain, uni/bi/tri-gram frequency etc.

##### Markov chain
###### Trigram as default; use `cut -d ' ' -f 2` for unigram and `cut -d ' ' -f 2,3` for bigram.

```sh
m () { read 1; echo $1 | cut -d ' ' -f1 | grep . && grep -io "$1\s.*" speeches.txt | cut -d ' ' -f2,3,4 | shuf -n 1 | m }; echo "nice" | m | tr '\n' ' '

nice to Christie but he really hit me today. Chris Christie. I mean, I made an unbelievable deal...
```

##### Term frequency
###### unigram

```sh
cat speeches.txt | awk '{for (i=1; i<NF; i++) print $i}' | sort | uniq -c | sort -rn | head

5178 the
5138 to
4794 I
...
```

###### bigram

```sh
cat speeches.txt | awk '{for (i=1; i<NF; i++) print $i, $(i+1)}' | sort | uniq -c | sort -rn | head

1744 going to
 580 of the
 556 to be
...
```

###### trigram

```sh
cat speeches.txt | awk '{for (i=1; i<NF; i++) print $i, $(i+1), $(i+2)}' | sort | uniq -c | sort -rn | head

 296 going to be
 277 we’re going to
 265 We’re going to
...
```
