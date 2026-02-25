To avoid circuits with with cyclic paths, we can break these cyclic paths by inserting registers somewhere in the path. This transforms the circuit into a collection of combinational logic 
and registers. The registers contain the state of the system which changes only at clock edge, we so say the state is synchronized to the clock. Adopting this technique of always
using registers in the feedback path leads us to the formal definition of a synchronous sequential circuit.

A sequential circuit has a finite set of discrete states {S0, S1, S2, ..., Sk - 1}. A synchronous sequential circuit has a clock input, whos rising edges indicate a sequence of times at which state
transitions occur.

We have a current state, then a next state that will be transitioned to on the next clock edge

Rules of synchronized sequential circuits:

1. every circuit element is either a register or combinational circuit
