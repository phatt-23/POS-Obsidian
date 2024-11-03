[prez1-1](https://lms.vsb.cz/pluginfile.php/2310316/course/section/2805839/basicPrinciples.pdf)
## BroadBand Transmission (long distance communication, modulation)
- carrier signal (continuous periodic signal - sine wave) chosen, not carrying any meaning
$$s(t) = A \sin(\omega t + \phi)$$
- we modify its parameters - amplitude ($A$), phase ($\phi$), frequency ($\omega$)

> instead of infinite possible values in traditional analog (continuous) signal (vinyl player, radio, walkie-talkie, film-tapes, analog cameras) we have only a finite set of values the signal can represent we can send (discrete)

- PSK (Phase-Shift Keying) - phase modulation
- QAM (Quadrature Amplitude Modulatin) 
	- combines amplitude modulation and phase shifting modulation

*note*: Transfer Rate (bits per second, bps) x Modulation Rate (changes in the signal per second, Bd bauds)

## BaseBand Transmission (limited to smaller geo ranges - LAN, WAN - encodings)
- stream is not modulated 
- bits being transmitted stay in the original f band
- phase sync mechanism (clock sync) of this type of transmission is data encoding
- hard time reading long sequences of 1s or 0s
    - we need frequent changes in the carrier signal
- NRZ (Non-Return to Zero) 
    - logical, just like as we see our bit stream
    - long seq od 1s or 0s are troublesome
    - not used
- Manchester, Differential Manchester (frequent signal changing from high to low and vice versa)
    - manchester 
	    - 1..high to low (` -_ `) in middle of period
        - 0..low to high (` _- `) in middle of period
        - changes in the start of a period as needed
    - diff. manchester 
	    - 0..sig. change at start of a period
        - 1..unchanged
        - always transition in the middle as necessary
	- used by Ethernet
- RZ (Return to Zero, three signal levels for 0, -1 and +1)
    - -1..0 bit
    - +1..1 bit
    - always 0 in the second half of a period
- NRZI (Non-Return to Zero Inverted, two levels)
    - change    ..1 bit
    - stays same..0 bit
- AMI (Alternate Mark Inversion, 0, -1, +1)
    - 0    ..bin 0 (problem maintaing long sqs of 0s)
    - -1,+1..bin 1
- HDB3 (High Density Bipolar Order 3, Modified AMI) 
    - after 3 zeros inserts 1
- CMI (Code Mark Inversion, AMI/HDB3 over optical cables)
    - light/dark (only 2 bits to work with)
    - maps 2 bits to the 3 signals in AMI/HDB3 (1 option unused)
- 4B5B (4 bits to 5 bits) (5B6B, 6B7B, ...)
    - maps 4 bits to 5 bits 
    - works because long sequences of 0s or 1s are not desirable 
         (11111, 00000, 11000, ...) are not used
    - used by Fast Ethernet (FE)
- 2B1Q (2 bits to quaternary)
    - maps 2 bits to 4 voltage levels
    - used by Integrated Services Digital Network (ISDN)