# SANER'18 review tree

This is a version of the project tree sanitized for review.

- References to author names and URLs have been removed or anonymized
- Parts of the source that are not pertinent to this project have been
  removed, as long as it was reasonably easy to do so.
- Other parts are vestigial and in need of a cleanup, which we would
  gladly do for a post-publication release of the source.

- Building this set of tools is not entirely straightforward as this
  version of BAP is written in OCaml 3.12, which the OCaml ecosystem
  has moved away from. We intend to provide a Dockerfile for easy
  deployment.

## Binaries
`kamino` is the program which implements the advanced
normalizations. The equivalence comparison by minimal normalization is
done by `trivial-equiv`.

## Walkthrough:

- The code is lifted and sent through a pipeline of transformation
  passes in summary.ml.

- The transformation passes are either implemented in analysis_pass.ml
  or referenced from that file. Our extensions to BAP are in the
  accompanying patch.

- The transfer functions are captured in the ssa_ext* files.

- The core of the equivalence comparison algorithm can be found in
  comparator.ml.

- The callgraph analysis is not needed for this project - call
  side-effect summarization has been removed or disabled.
