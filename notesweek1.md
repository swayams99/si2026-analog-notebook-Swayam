Title: Simple resistor voltage divider with a pulse input
Description:
A SPICE netlist that simulates a 1:1 resistor voltage divider driven by a pulsed voltage source. The input is a 0→5 V pulse (0.5 µs period, 50% duty) with finite rise/fall times. The simulation performs a transient analysis and plots the output node across the lower resistor.

Netlist (example)

text
* Simple resistor voltage divider with pulse input

R1      vin     vout    1k
R2      vout    0       1k

Vpulse  vin     0       PULSE 0 5 0.5u 10n 10n 0.5u 1u

.TRAN 0.1u 1.5u

.control
RUN
PLOT v(vout)
.endc

.end

Explanation of each line

    * Simple resistor voltage divider with pulse input

        Comment line. Lines beginning with * are ignored by SPICE and used for human-readable notes.

    R1 vin vout 1k

        Resistor R1 connects node vin to node vout, value 1 kΩ.

    R2 vout 0 1k

        Resistor R2 connects node vout to ground (node 0), value 1 kΩ.

        Together R1 and R2 form a voltage divider. With equal resistances the steady-state output equals half the input voltage.

    Vpulse vin 0 PULSE 0 5 0.5u 10n 10n 0.5u 1u

        Voltage source named Vpulse between node vin and ground.

        Uses the PULSE specification: PULSE(v1 v2 td tr tf pw per)

            v1 = 0 — low level (0 V).

            v2 = 5 — high level (5 V).

            td = 0.5u — delay before the first transition (0.5 µs).

            tr = 10n — rise time (10 ns).

            tf = 10n — fall time (10 ns).

            pw = 0.5u — pulse width (0.5 µs high time).

            per = 1u — period (1 µs). This produces a 50% duty cycle square wave after the initial delay.

        Note: Some SPICE variants accept V/vpulse naming differences and tolerate whitespace; ensure your simulator’s PULSE syntax matches.

    .TRAN 0.1u 1.5u

        Run a transient analysis.

        0.1u is the output (maximum) time step (100 ns); helps control plot resolution.

        1.5u is the total simulation time (1.5 µs), covering several pulse cycles and the initial delay.

    .control / RUN / PLOT v(vout) / .endc

        Control block for simulators like NGSPICE. RUN starts the simulation, PLOT v(vout) plots the voltage at node vout.

        If your simulator uses a different control syntax (e.g., SPICE3, LTspice), adapt accordingly (LTspice plots automatically; use .op/.tran and the waveform viewer).

    .end

        End of netlist marker.

Expected behavior and observations

    DC/steady-state: When the input is at 5 V long enough, the ideal divider produces vout ≈ 2.5 V because R1 = R2.

    With the pulsed input, vout will follow a square-ish waveform between 0 V and ~2.5 V.

    Finite rise/fall times (10 ns) cause short transition periods where vout transitions smoothly rather than instant steps.

    The initial delay td = 0.5 µs means the first rising edge appears at 0.5 µs; simulate beyond that to see repeated cycles (we used 1.5 µs).

Quick checks and tips

    If you see node name warnings, ensure you use 0 for ground (common node).

    To capture faster edges, reduce the .TRAN step size (e.g., .TRAN 1n 1.5u) or allow adaptive stepping by omitting the fixed step.

    For output file data (instead of plotting interactively), use .save v(vout) or the simulator’s export commands.

    To include initial conditions or start-up behavior, consider adding .ic lines or running longer simulation time.

Variants and experiments

    Change resistor ratio (R1 != R2) to get different voltage division ratios.

    Add a load resistor at vout to test loading effects.

    Replace ideal pulse with a source that includes series resistance or add capacitance at vout to see RC filtering and transient smoothing.

    Sweep pulse frequency or duty cycle to study dynamic response and bandwidth.
