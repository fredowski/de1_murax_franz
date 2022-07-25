RISCV de1_murax_franz
========================

Der fabelhafte RISCV Softcore auf dem Terasic DE1 Board! Für Franz.

### Murax Plattform mit RISCV Prozessor aus SpinalHDL

  * 50 MHz Taktfrequenz
  * UART mit 115200 Baud
  * GPIO an den Roten LEDs
  * Timer

### VHDL aus SpinalHDL

```
cd VexRiscV
sbt "runMain vexriscv.demo.de1_murax_franz"
cp ./de1_murax_franz.vhd ../src/
```

### VHDL Simulation des Prozessors

UART sendet 'A' und LEDs wechseln nach 1 Sekunde...

```
cd sim
cd de1_murax_franz
make sim
```

### FPGA Synthese und Download

```
cd pnr
cd de1_murax_franz
make prog
```

### Software Build mit gcc

```
cd VexRiscvSocSoftware/projects/murax/demo
make
cp ./build/demo.hex ../../../../VexRiscv/src/main/ressource/hex/muraxDemo.hex
```

Dann nochmal VexRiscV bauen und nochmal FPGA Synthese. Der Code landet via VHDL im
FPGA.

### UART anschliessen an MAC

Die UART läuft mit 115200 Baud. Mit einem FTDI USB UART Adapter kann man die UART vom DE1 Board anschliessen. Es wird eine Nachricht gesendet und die Eingaben kommen zurück. Auf MacOS:

```
screen /dev/tty.usbserial-FTALDMJL 115200
```
