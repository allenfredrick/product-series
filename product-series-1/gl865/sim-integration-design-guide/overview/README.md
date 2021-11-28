# Overview

### Overview

In Telit modules there are four pins for SIM card holder connection; these lines are:

* SIMVCC (SIM Power supply)
* SIMRST (SIM Reset)
* SIMIO (SIM Data)
* SIMCLK (SIM Clock)

On the modules supporting Hot Insertion/removal of the SIM there is an additional pin for sensing SIM presence:

* SIMIN (SIM Presence/Absence)

On the modules not supporting Hot Insertion/removal of the SIM, SIM is queried at Startup.

SIM connection design must take into account these general rules:

1. Data Integrity: standard rules for digital layout and routing must be followed taking into consideration that SIMCLK has a frequency of 3.57 MHz and SIMIO baud rate is greater or equal than 9600Bps
2. EMI/EMC: this is a key aspect to consider designing an application based on TELIT modules with an internal antenna and/or without a proper shielded box. Some of these conditions may occur:

* The antenna picks up digital noise coming from SIM card lines
* Antenna radiated field may interfere with digital lines
* Digital lines (in particular clock) may radiate spurious in the surrounding space

To overcome all these potential problems, connection lines must be kept as short as possible and shielded and the SIM-holder position has to be as far as possible from the antenna.

Besides RF bypass capacitors (10 pF ... 33 pF) closed to SIM card SIM-holder is another good care.

When the connection is not short, insertion of 10 … 47 Ohm resistor with 10 ... 33 pF capacitor (RC filter) is a good caution to improve EMI from SIMCLK line.

On SIMRST and SIMIO lines is allowed to insert 10 ... 100 Ohm resistor with 10 ... 33 pF capacitor (RC filter) to improve the EMI measurements.

Do not insert resistors on SIMVCC, their use is not supported by SIM electrical interface.

1. ESD: take ESD caution if the application based on the TELIT module has a SIM holder with contacts reachable from the human body. Refer to chapter 5

| ![C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp](<../../../../.gitbook/assets/0 (15)>) | <p><strong>Note/Tip:</strong> SIM card is detected inserted when SIMIN line is shorted to ground.</p><p>If in the application the SIM holder doesn’t foresee the switch for the presence/absence of the SIM card, the SIMIN line can be connected to the ground or the SIM can be selected as present with the following AT command: AT#SIMDET=1.</p> |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| ![C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp](<../../../../.gitbook/assets/1 (3)>) | **Note/Tip:** On xL865 and xE866 there is no dedicated SIMIN pin. To use the feature, the SIMIN pin has to be configured with the AT command AT#SIMINCFG=\<GPIO\_pin> among the available GPIOs. Be careful because, in some products, not all GPIOs can be configured for the SIMIN function; you can find the suitable GPIOs in the Hardware User Guide of the single devices or their Global Form Factor application note. |
| --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| ![C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp](<../../../../.gitbook/assets/2 (11)>) | **Note/Tip:** On GL865-QUAD V4 and GE310-GNSS there is no dedicated SIMIN pin. Hot Insertion/removal of the SIM is not supported. |
| ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
