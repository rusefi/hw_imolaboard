Analog Inputs
=============
_NB: this refers to general purpose analog inputs for things like CLT, TPS, MAP, etc.  High-speed inputs like triggers and knock have their own pages at [trigger](docs/design/trigger.md) and [knock](docs/design/knock.md)_

## What do the analog inputs support? ##
- 16 channels
- 0-5v input
- No input protection, other than 1k series resistor

## How do the analog inputs work? ##
- 16 channels are managed by 4 MCP6004 quad op-amps.
- 1k + 1nf RC filter input to opamp non-inverting input.  This gives approximately 160khz of bandwidth.  If a lower knee is desired, additional circuitry can be added (series resistor, or another RC, etc) to the vehicle adapter.
- Dual 1.5k resistor divider on the output, scaling 0-5v input to 0-2.5v output.  The input impedance of the STM32's ADC is on the order of 6k, so the exact value chosen does not appreciably alter the response of the system.

## What do the analog inputs NOT do? ##
- Input protection: this is highly pin specific, and may not be wanted if the signal is coming from the vehicle adapter board.  Appropriate larger series resistor and TVS diodes recommended.
