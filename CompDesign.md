# Computer Design

## Von Neumann Architecture

This outlines the idea of linear memory storing the program and data

Linear memory - all bytes are sequential bytes. This is true for all butes and information in memory.

The processor which executes instructions is connected to the memory through buses. Since the speed of these buses greatly influence the speed of execution, it is known as the [Von Neumann Bottleneck]()

## Memory Hierarchy

It is a challenge to develop 

Moore's law states that the transistor density doubles in approximately two years

Manufacturing costs
- Yield is critical, i.e. proportion of fully functional chips
  - Yield numbers are a guarded secret
  - Tricks are used to increase yield, including design time (e.g redudancy in memory )
  - Yield $\propto$ chip area
- Nonrecurrent (one-off) manufacturing costs for a chip have gone up:
  - e.g. mask costs for a 10nm chip are \$10m per chip design
  - must be offset against volume of sales of each chip design
- Cost of semiconductor fabrication foundries
  - TSMC's Fab15 cost \$9b in 2010

## Wire Scaling

Resistance (R)
- $R \propto L/(W *H)$

Capacitance(C)
- $C \propto W * L$

Simple wire: charge time(T)

- $T \propto R * C  \propto L^2 /H$  
To shrink down to new silicon technology, we want to reduce $H$ and $W$, but to keep the charge time small, we keep $H$ large and $W$.  

The size of the chip has not changed considerably over the years and wires don't get any faster for the same chip area.

1/2 $L$ makes the wire go 4x faster: adding buffering and repeaters helps
- often means that we cannot get data from one side of the chip to another in one clock.
## Denard Scaling
Transistor dimensions are scaled by 30% (0.7x) every generation, therefore reducing area by 50% (i.e moores law)

Reduces the delay by 30% (0.7x) and increases operating frequency by about 40% (1.4x)

To keep the electric field constant, the voltage is reduced by 30%. And therefore energy is reduced by 65% and power at (1.4x frequency) by 30%.
 