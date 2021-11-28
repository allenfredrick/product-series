# SIM

### SIM-ON-CHIP

In the M2M applications, there are several cases where the SIM Card will never be changed once installed, also it would be preferable if it shouldn’t be possible to remove it at all; furthermore, the SIM Card is required to work in a more harsh environment to standard mobile phones SIM Cards. To address these kinds of application the SIM On-Chip have been developed; they are a special SIM Card chip packaged as a surface mount assembly device that is then assembled with the modem at the factory and will be never removed from the application.

This approach results in a great advantage in terms of long-term reliability because the contracting issues that can arise due to moisture, vibrations, and harsh environmental conditions with standard SIM holders are avoided by design since the SIM On Chip is soldered on the application PCB.

The Telit modules support the usage of M2M SIM-On-Chip and their usage is the same as for conventional SIM Cards.

SIM On-Chip is interfaced with the same lines as for standard SIM:

* SIMVCC
* SIMIO
* SIMRST
* SIMCLK

and shall be connected and decoupled in the same way as the standard SIM Cardholder as shown in chapter 3.1. An example of SIM On-Chip connection is shown in the following schematic:

![](<../../../.gitbook/assets/0 (12)>)

Figure 6‑1 SIM On-Chip connection

Since the SIM On-Chip is not removable, it is possible to tie SIMIN to GND and eventually use the AT command AT#SIMDET to simulate insertion/removal.

Furthermore, if the SIM On Chip is shielded inside the application box and cannot be subject to ESD discharges, the ESD protection can be omitted.

If there is the need to have both a SIM On-Chip and a backup SIM Holder, then a dual SIM approach can be followed and the connections shall be the same as for chapter 5.
