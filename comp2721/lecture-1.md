Performance Issues
==

# Designing for Performance
Computing costs drop while performance and capacity rise, 
laptops now match th epower of passt IBM mainframes,
and microprocessors are inexpensive and widely available.

We are now aple to use high-power desktop applications
(e.g. image processing, 3D rendeting, speech recognition, etc.).
Powerful servers replace old mainframes for transactions and databases.
Cloud providers support high-volume, high transaction rate applications.

# Microprocessor Speed
Techniques built into contemporary processors include:
* Pipelining
    - Instructions ran in parallel with different stages (fetch/decode).
* Branch prediction
    - Condition like an if-else.
* Superscalar execution
* Data flow analysis
    - Linking instructions to determine execution sequence/condition.
* Speculative execution
    - Uses likelihood to determine what comes next.

# Improvements in Chip Organisation and Architecture
* Increased hardware speed of processor
    - Fundamentaly due to shrinking logic gate size.
      More gates are packed more tightly, increasing clock rate.
      Then, the propagation time for signals are reduced.
* Increased size and speed of caches
    - Dedicating parts of a processor chip, which reduces cache access times.
* Changed processor organisation and arch.
    - Increased effective speed of instruction execution, like parallelism.

# Problems with Clock Speed and Logic Density
* Power: More power density of logic and clock speed means more heat dissipated.
* RC (Resistance-Capacitance) delay: Current is limited by the RC of metal wires connecting them.
 the Delay increases as teh RC product increases.
 As the components get smaller, resistance and capacitance increases.
* Memory latency

# Many Integrated Core (MIC) and Graphics Processing Unit (GPU)
MIC: The multicore and MIC strategy involves a homogenous collection of general-purpose processors on a single chip.
GPU: Core designed to perform parallel operations on graphics data.
Traditionally found on a plug0in graphics card, it is used to encode and render 2D and 3D graphics as well as process video.
Used as vector processor for a variety of applications that require repetitive computations.

# Basic Measures of Computer Performance
1. Throughput: Number of tasks or instructions completed per unit of time.
Basically how much load the system can take in a certain period of time.
2. Latency (Response time): How much time it takes to complete a single task from start to finish.
3. Clock speed: the frequency at which a CPU executes instructions, measured in Hertz.
4. Cycles Per Instruction (CPI): Averegae number of clock cycles needed to execute one instruction. 
5. Millions of Instructions Per Second: measure of the number of instructions a processor can do per second.
6. Floating Point Operations per Second.
7. Efficiency
8. Speedup: ratio of execution time of a task on a single processor to the time on multiple processors. Uses parallelisation.
9. Instruction Execution Time: CPI * clock cycle.

## Calculating the Mean
1. Arithmetic mean
2. Geometric mean
3. Harmonic mean

Why does it matter?
This makes it easier to decide whether we need or more components when designing processors.

# Benchmark Principles
1. Written in a high-level language
2. representative of a particular kind of domain
3. easily measured

# Exercises

