# 📘 EDC Sessional 2 — Master Reference README

### Units 3, 4 & 5 | BJTs, MOSFETs, IC Amplifiers & Frequency Response

> **How to use this file**
>
> * [1. Constants & Key Parameters](#1-constants--key-parameters)
>
> * [2. Formula Sheet](#2-formula-sheet)
>
> * [3. Derivations](#3-derivations)
>
> * [4. Long Answer Theory](#4-long-answer-theory)
>
> * [5. Short Answer Q&A](#5-short-answer-qa)
>
> * [6. Comprehensive Glossary](#6-comprehensive-glossary)

## 1. Constants & Key Parameters

| Symbol | Name | Typical Context / Value | Units | 
| ----- | ----- | ----- | ----- | 
| $V_T$ | Thermal Voltage (at 300 K) | $25 \text{ to } 26$ | mV | 
| $I_S$ | Saturation / Scale Current | $10^{-15} \text{ to } 10^{-13}$ | A | 
| $V_A$ | Early Voltage | $10 \text{ to } 100$ | V | 
| $\mu_n$ | Electron Mobility (Si) | $\approx 1350$ (Exceeds hole mobility by 2-4x) | cm²/(V·s) | 
| $\mu_p$ | Hole Mobility (Si) | $\approx 480$ | cm²/(V·s) | 
| $\epsilon_{ox}$ | Oxide Permittivity (SiO₂) | $3.9 \epsilon_0 \approx 3.45 \times 10^{-11}$ | F/m | 
| $t_{ox}$ | Oxide Thickness | $1 \text{ to } 10$ | nm | 
| $k_n'$ | Process Transconductance Parameter | $\mu_n C_{ox}$ | A/V² | 

## 2. Formula Sheet

### 2.1 Bipolar Junction Transistor (BJT)

| Formula Name | Equation | Variables | Units | 
| ----- | ----- | ----- | ----- | 
| Collector Current (Active) | $i_C = I_S e^{v_{BE}/V_T}$ | $I_S$: Saturation current, $v_{BE}$: Base-emitter voltage | A | 
| Saturation Scale Current | $I_S = \dfrac{A_E q D_n n_i^2}{N_A W}$ | $A_E$: EBJ area, $W$: Base width, $N_A$: Base doping | A | 
| Base & Emitter Currents | $i_B = \dfrac{i_C}{\beta}, \quad i_E = \dfrac{i_C}{\alpha}$ | $\beta$: CE current gain, $\alpha$: CB current gain | A | 
| Gain Relationships | $\alpha = \dfrac{\beta}{\beta + 1}, \quad \beta = \dfrac{\alpha}{1 - \alpha}$ | $\alpha < 1$; $\beta$ typically $50 \text{ to } 200$ | Unitless | 
| Transconductance | $g_m = \dfrac{I_C}{V_T}$ | $I_C$: DC Collector bias current | A/V |
| Base Input Resistance | $r_\pi = \dfrac{V_T}{I_B} = \dfrac{\beta}{g_m}$ | Resistance looking into the base | Ω |
| Emitter Input Resistance | $r_e = \dfrac{V_T}{I_E} = \dfrac{\alpha}{g_m} \approx \dfrac{1}{g_m}$ | Resistance looking into the emitter | Ω |
| Current with Early Effect | $i_C = I_S e^{v_{BE}/V_T} \left(1 + \dfrac{v_{CE}}{V_A}\right)$ | $V_A$: Early Voltage, $v_{CE}$: Collector-emitter voltage | A | 
| Output Resistance | $r_o = \dfrac{V_A + V_{CE}}{I_C} \approx \dfrac{V_A}{I_C'}$ | $I_C'$: Collector current without Early effect | Ω | 
| Forced Beta (Saturation) | $\beta_{\text{forced}} \equiv \left.\dfrac{i_C}{i_B}\right\vert{}_{\text{sat}} \le \beta$ | $\beta_{\text{forced}}$: Effective gain in saturation | Unitless | 

### 2.2 MOS Field-Effect Transistor (MOSFET)

| Formula Name | Equation | Variables | Units | 
| ----- | ----- | ----- | ----- | 
| Oxide Capacitance | $C_{ox} = \dfrac{\epsilon_{ox}}{t_{ox}}$ | $\epsilon_{ox}$: Oxide permittivity, $t_{ox}$: Oxide thickness | F/m² | 
| Overdrive Voltage | $v_{OV} = v_{GS} - V_t$ | $V_t$: Threshold voltage | V | 
| Drain Current (Triode) | $i_D = k_n' \left(\dfrac{W}{L}\right) \left[ v_{OV} v_{DS} - \dfrac{1}{2} v_{DS}^2 \right]$ | $v_{DS} < v_{OV}$ | A | 
| Drain Current (Saturation) | $i_D = \dfrac{1}{2} k_n' \left(\dfrac{W}{L}\right) v_{OV}^2$ | $v_{DS} \ge v_{OV}$ | A | 
| Transconductance | $g_m = \mu_n C_{ox} \dfrac{W}{L} V_{OV} = \dfrac{2 I_D}{V_{OV}}$ | $I_D$: DC Drain current | A/V | 
| Output Resistance | $r_o = \dfrac{1}{\lambda I_D} = \dfrac{V_A' L}{I_D}$ | $\lambda$: Channel length modulation param | Ω | 

### 2.3 High-Frequency & IC Amplifiers

| Formula Name | Equation | Variables | Units | 
| ----- | ----- | ----- | ----- | 
| Resistance-Reflection (BJT) | $R_{in} = (\beta + 1)(r_e + R_e)$ | $R_e$: Emitter degeneration resistance | Ω |
| Intrinsic Gain (BJT) | $A_0 = g_m r_o = \dfrac{V_A}{V_T}$ | Max theoretical gain of a single transistor | V/V | 
| Intrinsic Gain (MOS) | $A_0 = g_m r_o = \dfrac{2 V_A' L}{V_{OV}}$ | Max gain, inversely proportional to $V_{OV}$ | V/V | 
| CS Gain (with $R_S$) | $A_v = -\dfrac{g_m R_D}{1 + g_m R_s}$ | $R_s$: Source degeneration resistance | V/V |
| Miller Equivalent Cap. | $C_{eq} = C_{gd} (1 + g_m R_L')$ | $C_{gd}$: Feedback cap., $R_L'$: Effective load res. | F | 
| Unity-Gain Freq. ($f_T$) | $f_T = \dfrac{g_m}{2\pi(C_{gs} + C_{gd})}$ | Freq. where short-circuit current gain is 1 | Hz | 
| Upper 3dB Frequency | $f_H = \dfrac{1}{2\pi C_{in} R_{sig}'}$ | $C_{in} = C_{gs} + C_{eq}$ | Hz | 
| Depletion Capacitance | $C_j = \dfrac{C_{j0}}{\left(1 + \dfrac{V_R}{V_0}\right)^m} = \dfrac{\epsilon A}{W}$ | $V_R$: Reverse bias, $W$: Depletion width | F | 

## 3. Derivations

### 3.1 BJT: Collector Current ($i_C$) and Scale Current ($I_S$)

**Objective:** Establish the exponential relationship between $v_{BE}$ and $i_C$.

1. **Boundary Conditions:** Forward biasing the EBJ sets the minority electron concentration at the base edge ($x = 0$):
   
   $$
   n_p(0) = n_{p0} e^{v_{BE}/V_T}
   $$
   
   At the CBJ edge ($x = W$), the reverse bias sweeps all carriers into the collector, so $n_p(W) = 0$.

2. **Diffusion Current:** The steady-state concentration profile $n_p(x)$ is linear due to the thin base. Diffusion current magnitude is:
   
   $$
   I_n = A_E q D_n \frac{d n_p(x)}{dx} = - A_E q D_n \left( \frac{n_p(0)}{W} \right)
   $$

3. **Collector Current:** Assuming negligible recombination, $i_C = \vert{}I_n\vert{}$:
   
   $$
   i_C = A_E q D_n \frac{n_p(0)}{W} = \left( \frac{A_E q D_n n_{p0}}{W} \right) e^{v_{BE}/V_T}
   $$

4. **Define Saturation Current (**$I_S$**):** Using $n_{p0} = n_i^2 / N_A$:
   
   $$
   I_S \equiv \frac{A_E q D_n n_i^2}{N_A W} \quad \implies \quad \boxed{i_C = I_S e^{v_{BE}/V_T}}
   $$

### 3.2 MOSFET: Drain Current ($I_D$) in Triode and Saturation

**Objective:** Derive $I_D$ using fundamental electrostatics and drift velocity.

1. **Charge Profile:** Induced channel charge per unit area at position $x$:
   
   $$
   Q(x) = C_{ox} [ V_{GS} - V(x) - V_t ]
   $$

2. **Differential Current:** Current $I_D = dq(x)/d\tau$. Substituting $dq(x) = W \cdot Q(x) dx$ and drift time $d\tau = dx/(\mu_n dV/dx)$:
   
   $$
   I_D = W C_{ox} \mu_n [ V_{GS} - V(x) - V_t ] \frac{dV}{dx}
   $$

3. **Triode Region Integration:** Integrate spatially from $x=0$ to $x=L$ and potential $V(0)=0$ to $V(L)=V_{DS}$:
   
   $$
   \int_0^L I_D \, dx = \int_0^{V_{DS}} \mu_n C_{ox} W [ V_{GS} - V_t - V(x) ] \, dV
   $$
   $$
   \boxed{I_D = \mu_n C_{ox} \frac{W}{L} \left[ (V_{GS} - V_t) V_{DS} - \frac{V_{DS}^2}{2} \right]}
   $$

4. **Saturation Pinch-off:** Saturation occurs when $V_{DS} \ge V_{OV}$. Substitute $V_{DS} = (V_{GS} - V_t)$ into the triode equation:
   
   $$
   I_D = \mu_n C_{ox} \frac{W}{L} \left[ (V_{GS} - V_t)^2 - \frac{(V_{GS} - V_t)^2}{2} \right]
   $$
   $$
   \boxed{I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_t)^2}
   $$

### 3.3 High-Frequency: Transition Frequency ($f_T$)

**Objective:** Derive the frequency where MOSFET short-circuit current gain drops to unity.

1. **Short-Circuit Output Current (**$I_o$**):** Ground the drain ($V_o = 0$). Because $g_m \gg s C_{gd}$:
   
   $$
   I_o \approx g_m V_{gs}
   $$

2. **Total Input Current (**$I_i$**):** Current enters parallel gate capacitors $C_{gs}$ and $C_{gd}$:
   
   $$
   I_i = s (C_{gs} + C_{gd}) V_{gs}
   $$

3. **Current Gain (**$A_{is}$**):**
   
   $$
   \frac{I_o}{I_i} = \frac{g_m}{s (C_{gs} + C_{gd})}
   $$

4. **Unity-Gain Condition:** Set magnitude to 1 at $s = j\omega_T$:
   
   $$
   1 = \frac{g_m}{\omega_T (C_{gs} + C_{gd})} \quad \implies \quad \omega_T = \frac{g_m}{C_{gs} + C_{gd}}
   $$
   $$
   \boxed{f_T = \frac{g_m}{2\pi (C_{gs} + C_{gd})}}
   $$

## 4. Long Answer Theory

### Q: Compare the physical transport mechanisms of minority carriers through the base region of an npn BJT in active mode versus saturation mode.

**Active Mode:** The emitter-base junction (EBJ) is forward-biased, and the collector-base junction (CBJ) is reverse-biased. A steep, linear minority carrier concentration gradient forms across the base width $W$, starting high at the EBJ ($n_p(0) = n_{p0}e^{v_{BE}/V_T}$) and dropping to nearly zero at the CBJ ($n_p(W) = 0$). Carriers are swept efficiently into the collector, allowing high linear amplification.
**Saturation Mode:** Both the EBJ and CBJ are forward-biased. The forward-biased CBJ injects holes from the base into the collector and electrons from the collector back into the base. This raises the carrier concentration at $n_p(W)$ above zero, severely flattening the concentration gradient. Consequently, the net collector current drops, base current spikes, and the effective gain ($\beta_{\text{forced}}$) plummets below normal $\beta$.

### Q: Discuss BJT Small-Signal Models. When should you use the Hybrid-$\pi$ Model vs. the T-Model, and what is the Resistance-Reflection Rule?

**Models:** Both models are mathematically equivalent. The **Hybrid-$\pi$ Model** treats the BJT as a voltage-controlled current source (with $r_\pi$ looking into the base). The **T-Model** is often drawn as a current-controlled current source (with $r_e$ looking into the emitter). 
**Usage:** The Hybrid-$\pi$ model is typically best for circuits where the emitter is grounded (like standard Common-Emitter). The T-Model provides a much simpler analysis whenever there is a resistance placed in series with the emitter (Common-Base or CE with emitter degeneration).
**Resistance-Reflection Rule:** When analyzing a circuit with an emitter resistor $R_e$ from the base perspective, the total resistance seen looking into the base is $R_{in} = (\beta + 1)(r_e + R_e)$. The factor $(\beta + 1)$ arises because the base current is $1/(\beta+1)$ times the emitter current, effectively "reflecting" the emitter resistance up by this large factor.

### Q: Discuss MOSFET Biasing. Why is fixing $V_{GS}$ a poor technique, and how does Source Degeneration resolve it?

**Fixing $V_{GS}$:** Simply applying a constant voltage to the gate is a poor biasing strategy. MOSFET parameters like threshold voltage ($V_t$), oxide capacitance ($C_{ox}$), and aspect ratio ($W/L$) vary widely due to manufacturing tolerances and temperature shifts. A fixed $V_{GS}$ across different devices will result in drastically different drain currents ($I_D$), leading to poor Q-point stability.
**Source Degeneration ($R_S$):** A better method is biasing by fixing the gate voltage ($V_G$) and adding a resistor ($R_S$) at the source. This introduces **negative feedback**. If $I_D$ tries to increase (due to temperature or device variation), the voltage drop across $R_S$ increases ($V_S = I_D R_S$). This forces $V_{GS} = V_G - V_S$ to decrease, which inherently reduces $I_D$ back down. This "degeneration" stabilizes the operating point. 

### Q: How do transistor breakdown and temperature effects impact the BJT?

**Breakdown:** Avalanche breakdown occurs at the reverse-biased CBJ. The breakdown voltage depends on the circuit configuration. **$BV_{CBO}$** is the breakdown voltage in common-base mode (emitter open) and is typically >50V. **$BV_{CEO}$** is the breakdown voltage in common-emitter mode (base open), which is much lower (about half of $BV_{CBO}$) and is often called the sustaining voltage.
**Temperature:** At a constant current, $v_{BE}$ drops by approximately 2 mV per 1°C rise. The scale current $I_S$ doubles every 5°C, and leakage $I_{CBO}$ doubles every 10°C. Furthermore, the current gain $\beta$ increases with temperature, but peaks at moderate $I_C$ and falls off at very high or very low currents.

### Q: Compare the performance characteristics of the three basic MOSFET amplifier configurations (CS, CG, CD).

*   **Common Source (CS):** Offers infinite input resistance and high open-circuit voltage gain ($A_{vo} = -g_m R_D$). It is the best configuration for the bulk of voltage amplification in a cascaded system.
*   **Common Gate (CG):** Has a very low input resistance ($R_{in} = 1/g_m$). It provides non-inverting voltage gain ($A_{vo} = g_m R_D$). Its low input impedance makes it poor as a standalone voltage amplifier, but it has excellent high-frequency response, making it ideal to pair with a CS stage in a Cascode amplifier.
*   **Common Drain (CD) / Source Follower:** Offers infinite input resistance and low output resistance ($R_o = 1/g_m$). Its voltage gain is nearly unity ($A_{vo} \approx 1$). It is primarily used as a voltage buffer to connect high-resistance sources to low-resistance loads, or as an output stage in multistage amplifiers.

## 5. Short Answer Q&A

**Q: What is the fundamental operational difference between an enhancement-mode and a depletion-mode MOSFET?**
**A:** An enhancement-mode device is "normally OFF" and requires an applied gate voltage ($V_{GS} > V_t$) to induce a conductive channel. A depletion-mode device is "normally ON" as it is fabricated with an existing physical channel that can be enhanced or depleted.

**Q: Why cannot an actual BJT be operated symmetrically by swapping the collector and emitter terminals?**
**A:** The BJT is physically asymmetric. The collector area is significantly larger than the emitter area to maximize carrier collection efficiency. Swapping them (Reverse-Active mode) results in extremely poor carrier collection and abysmally low current gains ($\alpha_R, \beta_R$).

**Q: Why is NMOS preferred over PMOS in VLSI integration?**
**A:** Electron mobility ($\mu_n$) in NMOS is 2 to 4 times greater than hole mobility ($\mu_p$) in PMOS. Therefore, NMOS devices provide higher transconductance and faster switching speeds for the exact same physical dimensions.

**Q: What defines the unity-gain frequency (**$f_T$**) of a transistor?**
**A:** $f_T$ is the frequency at which the short-circuit small-signal current gain drops to unity (0 dB). It serves as a fundamental benchmark for the high-frequency capabilities of the device.

**Q: Explain the Miller effect in a common-source amplifier.**
**A:** The high-frequency feedback capacitance ($C_{gd}$) connecting the input and output is multiplied by $(1 + \text{Voltage Gain})$. This creates a massive equivalent input capacitance ($C_{eq}$), forming a low-frequency dominant pole that restricts the amplifier's overall bandwidth.

**Q: What happens to a MOSFET channel at the pinch-off point?**
**A:** When $v_{DS} \ge v_{OV}$, the gate-to-drain voltage drops to $V_t$ ($v_{GD} \le V_t$). The continuous induced inversion layer tapers off and reaches zero depth exactly at the drain junction, pushing the device into saturation.

**Q: What is the purpose of cascoding in IC amplifiers?**
**A:** Cascoding stacks a common-gate (or common-base) transistor on top of a common-source (or common-emitter) transistor. This massively increases the output resistance and mitigates the Miller effect, boosting voltage gain without sacrificing bandwidth.

**Q: Identify the two internal components of base current (**$i_B$**) in an active npn BJT.**
**A:** 1. Holes injected directly from the p-type base into the n-type emitter ($i_{B1}$). 2. Holes supplied externally to replace those lost to electron-hole recombination within the base volume ($i_{B2}$).

**Q: What is the Subthreshold Region in a MOSFET?**
**A:** It is the region where $V_{GS} < V_t$. While ideally cutoff, a very small drain current actually flows and depends exponentially on $V_{GS}$ (similar to a BJT). This region is heavily utilized in ultra-low-power IC designs.

## 6. Comprehensive Glossary

| Term | Definition | 
| ----- | ----- | 
| **Active Mode** | BJT mode where EBJ is forward-biased and CBJ is reverse-biased; used for linear amplification. | 
| **Active Load** | Utilizing a transistor biased as a constant-current source to act as a high-resistance load, maximizing gain in a compact IC footprint. | 
| **Base-Width Modulation** | Variation of effective base width $W$ caused by changes in CBJ reverse bias (Early Effect), creating finite output resistance. | 
| **BiCMOS** | IC technology combining BJTs (high current drive) and MOSFETs (high input impedance/low power) on a single chip. | 
| **Cascode Amplifier** | Two-transistor stack (CS followed by CG) designed to vastly increase output resistance and reduce Miller capacitance. | 
| **Channel Pinch-Off** | Operational point where $v_{GD} \le V_t$, causing the MOSFET channel depth at the drain junction to drop to zero (saturation onset). | 
| **CMOS** | Complementary MOS; integrates NMOS and PMOS on a single substrate, offering high noise immunity and near-zero static power consumption. | 
| **Depletion Region** | Area stripped of mobile charge carriers, leaving immobile donor/acceptor ions (creates Junction Capacitance $C_j$). | 
| **Diffusion Capacitance (**$C_D$**)** | Small-signal capacitance from minority carrier charge storage/recombination across a forward-biased p-n junction. | 
| **Dominant Pole** | A system pole at a significantly lower frequency than all others, primarily dictating the 3 dB cutoff bandwidth. | 
| **Early Voltage (**$V_A$**)** | Positive voltage intercept on the negative $v_{CE}$ axis when extrapolating active-mode $i_C - v_{CE}$ curves. | 
| **Forced Beta (**$\beta_{\text{forced}}$**)** | The reduced $i_C / i_B$ ratio observed when a BJT is driven into saturation ($\beta_{\text{forced}} \le \beta$). | 
| **Intrinsic Gain (**$A_0$**)** | Theoretical max voltage gain of a single transistor with an infinite-resistance load ($A_0 = g_m r_o$). | 
| **Miller Effect** | Multiplication of feedback capacitance ($C_{gd}$) by the stage's voltage gain, greatly increasing effective input capacitance. | 
| **Overdrive Voltage (**$V_{OV}$**)** | Net voltage exceeding threshold applied to a MOSFET gate ($V_{GS} - V_t$), dictating inversion density and current. | 
| **Process Transconductance (**$k_n'$**)** | Technology factor equal to electron mobility times oxide capacitance ($\mu_n C_{ox}$), measured in A/V². | 
| **Resistance-Reflection Rule** | Looking into the base of a BJT, the resistance in the emitter leg is multiplied by $(\beta + 1)$. |
| **Transition Frequency (**$f_T$**)** | Frequency at which the short-circuit small-signal current gain of a transistor drops to unity (0 dB). | 
