This repository contains source code and data for the optical network model.

## Running a simulation for a specific channel

python parsetables.py <channel_frequency>

For example: python parsetables.py 193.5

You can also run the simulation for a specific span using the shell scripts. For example:

```bash
./32-albgain.sh
```

simulates all channels propogatinig between NYC and ALB. Or:

```bash
./alb-syr.sh
```

simulates all channels propogating between ALB and SYR. There are also scripts for the reverse of these paths.

## Running the optimizer for the network (this will run on the 193.5 THz channel by default)

python network_optimizer.py


## Definitions for amplifiers and the network

The network is defined in the JSON files inside gnpy/nysernet/ ending in "gain" and "optimize". The files are separated by section. For example, 32-albgain.json defines the span between NYC and ALB, while alb-syrgain.json defines the span between ALB and SYR. The JSON files contain the gain targets, VOA settings, tilt settings, fiber span length, and ROADMs of the network. The optimized values are files which end in "optimize".

The amplifiers, fiber specs, ROADM specs, and span specs are defined inside gnpy/nysernet/eqpt_config_gain.json. The amplifiers are defined by their model type and we provide the max/min gain, max/min noise figure, max input power and other details. 

The channels propogating through the network are defined in the JSON files inside gnpy/nysernet/ ending in "spectrum". The channel center frequencies are defined in the JSON files, as well as the baud rate, transmit OSNR, and roll off. The spectrum of frequencies are the same in both directions of a span. For example, syr-albspectrum.json defines the channel frequencies propogating from SYR to ALB and also from ALB to SYR, while alb-32spectrum.json defines the channel frequencies propogating from ALB to NYC and also from NYC to ALB.