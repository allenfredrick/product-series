# Dual SIM Selection

### Dual SIM Selection

The Telit modules can already support more than one SIM card, in the following Figure 5-1 is showed a schematic example of a dual SIM connection:

![](<../../../.gitbook/assets/0 (4)>)

Figure 5‑1 Dual SIM

SIM A is enabled using this AT command sequence:

* AT#GPIO=X,1,1
* AT#GPIO=Z,0,1
* AT#GPIO=Y,0,1
* AT#SIMDET=0 (5 seconds of pause)
* AT#SIMDET=2

SIM B is enabled using this AT command sequence:

* AT#GPIO=X,0,1
* AT#GPIO=Z,1,1
* AT#GPIO=Y,1,1
* AT#SIMDET=0 (5 seconds of pause)
* AT#SIMDET=2

If the user doesn't need SIM hot removal he can ground the SIMIN pin on the module side, in this case, the AT command sequence changes a bit because AT#SIMDET has to be set to 1 and not to 2:

SIM A is enabled using this AT command sequence:

* AT#GPIO=X,0,1
* AT#GPIO=Z,1,1
* AT#GPIO=Y,0,1
* AT#SIMDET=0
* (5 seconds of pause)
* AT#SIMDET=1

SIM B is enabled using this AT command sequence:

* AT#GPIO=X,1,1
* AT#GPIO=Z,0,1
* AT#GPIO=Y,1,1
* AT#SIMDET=0 (5 seconds of pause)
* AT#SIMDET=1

| ![C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp](<../../../.gitbook/assets/1 (7)>) | **Note/Tip:** The P-Channel MOSFETS should have a Ron typical around 0.5Ω and must never exceed 1Ω. |
| ------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |

| ![C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp](<../../../.gitbook/assets/2 (7)>) | <p><strong>Note/Tip:</strong> On xL865 and xE866 families there is no dedicated SIMIN pin and AT#SIMDET=1 is the default value. To use the configuration shown in Figure 5-1 the SIMIN pin has to be configured with: AT#SIMINCFG=&#x3C;GPIO_pin> (stored in NVM) and AT#SIMDET=2 (stored in the extended profile AT&#x26;P).</p><p>Be careful because, in some products, not all GPIOs can be configured for the SIMIN function; you can find the suitable GPIOs in the Hardware User Guide of the single devices or their Global Form Factor application note.</p> |
| ------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| ![C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp](../../../.gitbook/assets/3) | **Note/Tip:** On GL865-QUAD V4 and GE310-GNSS in the Dual SIM Selection circuit shown here, the switch IC must be controlled by an external processor, and the module shall be rebooted after SIM switching. |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

It’s also possible to use a dedicated IC switch with a low Ron channel for SIMVCC such as FSA2567:

![](<../../../.gitbook/assets/4 (3)>)

Figure 5‑2 switches with a low Ron channel for SIMVCC

SIM A is enabled using this AT command sequence:

* AT#GPIO=X,0,1
* AT#SIMDET=0 (5 seconds of pause)
* AT#SIMDET=1

SIM B is enabled using this AT command sequence:

* AT#GPIO=X,1,1
* AT#SIMDET=0 (5 seconds of pause)
* AT#SIMDET=1

| <ul><li><img src="../../../.gitbook/assets/5 (4)" alt="C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp"></li></ul> | <p><strong>Note/Tip:</strong> On xL865 and xE866 families there is no dedicated SIMIN pin and AT#SIMDET=1 is the default value. To use the configuration shown in Figure 5-1 the SIMIN pin has to be configured with: AT#SIMINCFG=&#x3C;GPIO_pin> (stored in NVM) and AT#SIMDET=2 (stored in the extended profile AT&#x26;P).</p><p>Be careful because, in some products, not all GPIOs can be configured for the SIMIN function; you can find the suitable GPIOs in the Hardware User Guide of the single devices or their Global Form Factor application note.</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| ![C:\Users\elenape\AppData\Local\Microsoft\Windows\INetCache\Content.MSO\E1800DB4.tmp](<../../../.gitbook/assets/6 (2)>) | **Note/Tip:** On GL865-QUAD V4 and GE310-GNSS in the Dual SIM Selection circuit shown here, the switch IC must be controlled by an external processor, and the module shall be rebooted after SIM switching. |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
