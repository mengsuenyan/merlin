<img
 width="33%"
 align="right"
 src="https://upload.wikimedia.org/wikipedia/commons/7/79/Arthur-Pyle_The_Enchanter_Merlin.JPG"/>
 
## Merlin: composable proof transcripts for public-coin arguments of knowledge

Merlin is a [STROBE][strobe]-based construction of a proof transcript which
applies the Fiat-Shamir transform to an interactive public-coin
argument of knowledge.  This allows implementing protocols as if they
were interactive, committing messages to the proof transcript and
obtaining challenges bound to all previous messages.

In comparison to using a hash function directly, this design provides
support for:

* multi-round protocols with alternating commit and
challenge phases;

* natural domain separation, ensuring challenges are
bound to the statements to be proved;

* automatic message framing, preventing ambiguous encoding of commitment data;

* and protocol composition, by using a common transcript for multiple protocols.

In addition, Merlin provides a transcript-based `rand_core::RngCore` instance
for use by the prover.  This provides synthetic randomness derived from
the entire public transcript, as well as the prover's witness data,
and an auxiliary input from an external RNG.

## Features

The `nightly` feature is passed to `clear_on_drop`; it may be replaced
with a no-op in the future (since `clear_on_drop` is an implementation
detail).

The `debug-transcript` feature prints an annotated proof transcript to
`stdout`; it is only suitable for development and testing purposes,
should not be used in released crates, and should not be considered stable.

An example of an annotated transcript for a Bulletproof rangeproof can
be [found here][bp_transcript].

## About

Merlin is authored by Henry de Valence, with design input from Isis
Lovecruft and Oleg Andreev.  Thanks also to Trevor Perrin and Mike
Hamburg for helpful discussions.  Merlin is named in reference to
[Arthur-Merlin protocols][am_wiki] which introduced the notion of
public coin arguments.

This project is licensed under the MIT license; see `LICENSE.txt` for
details.

[strobe]: https://strobe.sourceforge.io/
[am_wiki]: https://en.wikipedia.org/wiki/Arthur%E2%80%93Merlin_protocol
[bp_transcript]: https://gist.github.com/hdevalence/9db3997cc275597eeae1ec2461b8e2a1
