
# Target Concurrency

run FAKE Targets using concurrency to speed up execution.

This library does route finding and path optimization to enable the grouping of targets that can run in parallel.

`
open Bedu
`

`
open TargetConcurrency
`

`
Target "_A" DoNothing ; Target "_B" DoNothing ; Target "_C" DoNothing
`

`
Target "_D" DoNothing ; Target "_E" DoNothing ; Target "_F" DoNothing
`

`
Target "_G" DoNothing ; Target "_H" DoNothing
`

`
"_A" ==> "_B" ; "_A" ==> "_C"
`

`
"_B" ==> "_D" ; "_C" ==> "_D"
`

`
"_D" ==> "_E" ; "_D" ?=> "_G" ; "_F" ?=> "_G"
`

`
"_E" ==> "_H" ; "_G" ==> "_H"
`

`
runTargetConcurrent "_H"
`

A

/\

B , C

\/

D | F

/\? /?

E , G

\/

H
