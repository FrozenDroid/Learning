# Communication protocols

## SPI

### General info

SPI stands for "Serial Peripheral Interface", that is primarily used in embedded systems.
It was developed by Motorola in the late 1980s and it has been used in SD cards and LCD displays.

### Wires

Usually, it uses 4 wires, but can be used with as few as 2 in certain configurations.

The usual arrangement:

* SCLK: Serial clock (from the master)
* MOSI: Master output slave input, or also known as Master out slave in (data output from the master)
* MISO: Master input slave output, or also known as master in slave out (data output from the slave)
* SS: Slave select (often low, output from the master)

Sometimes these have alternative names:

* SCLK: SCK
* MOSI: SIMO, SDO, DI, DIN, SI, MTSR
* MISO: SOMI, SDI, DO, DOUT, SO, MRST
* SS: S̅S̅, SSEL, CS, C̅S̅, CE, nSS, /SS, SS#

When there is only a single slave device, the SS can be left out if the slave allows it.



