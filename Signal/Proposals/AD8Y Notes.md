# Notes on proposed ionospheric sounding signals
David Kazdan AD8Y
18 June 2026, ed. 7 November 2026

### Summary

Radio beacons have a long history as propagation indicators and research tools.  Government-run utility stations have high accuracy and precision through atomic clock oscillators; they are intended for time and frequency dissemination.  Amateur radio beacons are of lower specification but are strategically placed to aid in communications path determination.  Few in either category have been designed and implemented specifically for the purpose of ionospheric sounding.  In neither groups have modulations been intended for ionospheric data collection.

Design of beacon station modulation for ionospheric sounding is discussed here.  One context is US Department of Commerce National Institute of Standards and Technology stations WWV and WWVH and inclusion of modulation during otherwise quiet parts of their broadcast schedules.  A second is the more open design of modulation for transmitters deployed specifically for the ionosphere research purpose.

Signals are discussed as they aid in measuring signal path quality, time of flight, and Doppler shift, along with characterization of channel noise.  They are sorted into the overlapping categories of which are best transmitted with carrier signals and which without, and which may be received with minimal, inexpensive equipment and which require more sophisticated signal processing.

The signals presented include short pulses similar to WWV/H second ticks and sustained tones, again similar to WWV/H presentations.  Also included are the maximal-autocorrelation signals of Barker codes, Costas array spread-spectrum transmission, and maximal-length sequence binary phase-shift coding.

## Introduction

Various radio beacon systems have been in use for ionospheric sounding for decades.  The US Department of Commerce’s transmitting stations have been in use for that since 1919, although they operate without a formal charge for facilitation of research. The physics, amateur radio, shortwave listener, and atmospherics communities have used US and other government stations for various sounding purposes as transmitters were installed over the twentieth century.  The amateur radio beacon network organized by the Northern California DX Association and the International Amateur Radio Union exemplifies non-government beacon provision.[^1]

The use of beacons for propagation studies falls into two broad categories.  For most amateur radio applications, the existence of a known signal transmitted from a known location provides indication of a communications path to that region of the world.  Beacons constructed for that purpose maintain published schedules, identify in some form (usually Morse code).  Many have a schedule of power reduction so that loss of signal in noise may be identified.  Most have only frequency and timing accuracy adequate for amateur radio communications purposes.

Beacons that are useful for ionospheric sounding are more complicated and mostly are signals from time-and-frequency utility stations run by governments.  Some commercial broadcast stations have been identified as having adequate frequency accuracy for sounding purposes.[^2]  The utility station transmitters are maintained and operated for purposes such as time and frequency dissemination, and their signals reflect those purposes.  Their use and utility as propagation and sounding beacons is a matter of happenstance.

A first experiment in using a utility station for scientific measurement purposes was graciously provided by USDC’s NIST through their stations WWV and WWVH.  A purpose-designed modulation has occupied one minute of each hour in those stations’ broadcast schedules for several years; the programming is meant to facilitate characterization of the transmitters and then to suggest signals that are optimized for ionospheric measurements.[^3]

## Design goals for ionospheric research signals

With a transmitted signal generated of known engineering parameters and with transmitting antennas at a known location, reception may be done for its own sake (reports from WWV engineers indicate that a surprising number of people simply like listening to the broadcast, as witnessed by telephone calls and reception report cards mailed in). Perhaps more commonly, reception is planned for the stations’ stated and designed purpose of synchronizing timepieces and oscillators to international standards.  Research use is incidental but also appears to be common.[^4]  The various communities interested in ionospheric sounding may benefit from purpose-designed additions to the modulation schedule, and pooled data may be presented on internet sites as a new service.  The information thus supplied will have its own consumers, including communicators, power and communications systems operators, and research scientists.

Data to be gathered fall into overlapping groups:

 - Received signal strength at various locations, and received signal over noise
 - Signal time of flight at those and other locations
 - Signal Doppler shift, also geographically distributed.


Interested parties fall into their own overlapping groups:

 - Those primarily interested in propagation paths, as noted above.
 - Those interested in making records for ionospheric sounding use, including
 - Those with only simple equipment such as an AM shortwave broadcast receiver
 - Those with frequency-disciplined product detection (single-sideband)
 - Those with time-disciplined receiving equipment, either AM or single-sideband
 - Those with both frequency- and time-disciplined equipment
 - Those interested in consuming the collected data.

Communications users needing signal-above-noise information will mostly be using their regular radio receivers.  They need accurate schedule information for whatever signals are broadcast.

Signals prepared for overlap on existing transmitters such as WWV must not interfere with existing modulation; other users’ use of the signals must not be damaged.


## Use of current WWV/H modulations

In the current signal structures, the existing WWV and WWVH second tick and steady tone modulations are of greatest use in ionospheric sounding.  The station carrier signals are with some exceptions of limited utility because of multiple stations transmitting on identical frequencies.  The digital time code sent on a 100 Hz subcarrier is also seemingly of limited utility but perhaps is only understudied for time-of-flight measurement.

The WWV/H second ticks are of primary use in time of flight measurement.  They also have low total energy and so are useful in crude signal over noise measurement with the signal’s carrier controlling receiver automatic gain control if present.  Both of these measurements may be made with inexpensive diode-detector AM shortwave broadcast receivers, such as those used in the CHU eclipse along-path project.  Accurate measurements require distinguishing WWV’s 1000 Hz tick from WWVH’s 1200 Hz one.  The measurements are facilitated by the guard silences surrounding the ticks.  Adding a GNSS receiver’s pulse-per-second timing discipline to the AM receiver permits adding time of flight measurement to that of the signal amplitude.  The time of flight measurement has been done with matched-filter autocorrelation measurements and that may be the best approach with which to continue.

The steady modulation tones are of primary use in Doppler measurement.  The frequency change of the modulated sidebands, like that of the carrier, may be made only with a product-detector receiver that is frequency disciplined to a degree better than the expected smallest measurable frequency variation of the signal in channel noise.  The sidebands contain less energy than the carrier but are still useful for the purpose.  They may also be used for signal strength determination.  Since WWV and WWVH’s tone schedules are nonoverlapping, measurements may be made simultaneously from the two (different from measurements of the carriers, which of course do overlap).  The frequency estimation from the demodulated tones has been done with various methods including discrete Fourier transform with bin interpolation, zero-crossing measurement, and Tsui-Rosenthal recursive estimation.  As this approach is revisited, more contemporary frequency estimation approaches such as matrix pencil methods should be examined.  The measurement and estimation are complicated by the second-tick guard intervals; even though the tones are sent over a 40 second interval, they are interrupted every second.  An estimation approach that anticipates this should be used.

The existing modulation includes the second ticks 57 seconds out of each minute, with silence on the 29th and 59th seconds and an extended top-of-minute tone on the zeroth second of each minute. That last tone is sent at 1500 Hz, the same for both transmitters but different from either’s second tick tone.  There is no special tone sent to mark the beginning of each UTC day, but the 440 Hz tone sent on the 1st minute of each hour for WWVH and the second minute of each hour for WWV are omitted during the zeroth hour.  The silent periods including those limited to the second tick time slot may be used for channel noise estimation.

## Design of signals to be added to WWV/H

Any signal added to WWV/H for the specific purpose of ionospheric sounding should be chosen to improve upon and add to the measurements already possible.  Such signals should be chosen to add redundancy to measurements and therefore reduce errors through comparison of results obtained by varying methods, or to improve measurement precision when compared with and averaged with existing measurements.  Such errors and losses of precision might be caused by noise or signal processing algorithm failures, for example.  A first consideration should be addition of extended pulses in the form of Barker codes and of spread-spectrum[^5] sequences in the form of Costas arrays.

These signals may be added to WWV/H quiet times without disturbing current schedules or users.  Maintaining a few of the quiet times without modulation would, however, help in data collection by permitting channel noise characterization.

Several seconds of each transmitter minute are currently scheduled silent after the second tick.  Costas array spread-spectrum modulation has the theoretical optimal cross-correlation for simultaneous time of flight and frequency estimation, considerably better than frequency sweep either continuous or discrete.  Modulating one of the available seconds with a Costas spread-spectrum sequence may be viewed as providing a sequence of second ticks for time-of-flight examination, while simultaneously permitting Doppler shift examination.  These measurements would require time and frequency discipline at the receiver with fairly sophisticated signal processing, but all of those are well within scope for this project.  With anticipated signal to noise ratios of 10 dB, desired timing precision of 10 microseconds, and desired frequency estimation precision of 10 millihertz, Costas arrays of order 20 to 24 that fill the voice communications channel of 300 to 2700 Hertz are optimal.  The popular amateur radio communications mode FT8 uses an order 7 array for time and frequency synchronization of radio stations.  Experiments with the FT8-sized array suggest that it is of adequate precision for signals of low error but collapses into a cyclic ambiguity state with signals of higher but still plausible shifts.

Experiments during the European eclipse of August 2026 using a 21 element Costas array were encouraging if not fantastically so.  Doppler shift was difficult to measure because neither the transmitting station in Valence nor the receiving stations in northern Spain or in Iceland were tightly frequency-disciplined.  Time of flight was more promising because all three stations used GPS timing in transmission and recording, but the ionosphere seemed unusually stable and very little time of flight variation was recorded during or around the eclipse.  The Costas method was very useful in recording received signal strength, however:  The receivers had capacity for shutting off automatic gain control, and the software analysis included estimating and averaging noise in all twenty unoccupied frequency slots during each of the 21 time slots each second.

Also noted during the eclipse was the utility of the CW (radiotelegraph) station identification.  It was accurately timed from Valencia and provided confirmation of the Costas time of flight measurement.  A CW beacon station in Thailand was, by chance, within the reception passband of both receiving stations and was able to be identified, confirmed, and used for amplitude measurement. In retrospect, a well-placed CW beacon station across the eclipse path from the receiving stations would have provided another interesting data source.

The Costas spread-spectrum signals are not difficult to generate with either direct digital synthesis techniques or with programmable arbitrary-waveform function generators, either of which may be GNSS-PPS disciplined.  The time of flight measurement is possible with an AM detector and local PPS providing timing common view; including Doppler shift analysis requires a product detector and both PPS and frequency discipline.  The signal energy would be about a factor of 100 greater than that for the second tick alone and would thus be predicted to give much higher precision for time of flight measurements with the same inexpensive hardware.

Another one-second modulation stream is a Barker code.  This is the one-dimensional (single-frequency) equivalent of Costas spread-spectrum and provides theoretical maximum autocorrelation for time of flight estimation.  Barker codes are keyed with constant frequency (as opposed to the Costas spread-spectrum approach of filling frequency space).  They may use either on/off keying or phase-shift keying. The longest known Barker code involves phase-shift keying with 13 elements; this is an easy signal to produce with the same techniques, time discipline, and hardware as described for the spread-spectrum signals.  It provides an improvement in timing accuracy compared with single-pulse measurements, commensurate with its additional signal energy.  The improvement is expected to be on the order of 22 dB.  Reception would optimally be by diode detector AM or phase-locked loop AM as with second-tick measurements, avoiding the complexity of Doppler shift determination and compensation.  Signal processing for estimation of time of flight is again well within the scope of this project using fully developed methods.  These are available prepackaged in Matlab’s communications and signal processing toolkits and are facilitated by several Python libraries.

A third possibility to explore primarily for multipath detection is a bandwidth-filling maximum length sequence, realized in the form of binary phase-shift keying.  These sequences promise autocorrelations similar to those of Barker codes.  The audio bandwidth of 300-3000 Hz, in appropriate time between second tick guard intervals of 0.5 to 0.8 seconds, could be conveniently filled with a 1500 Hz carrier, 1500 chips/second, 1023 chips total.  An expected detection sensitivity in low noise might be a 20 dB difference in primary and secondary signals with a 2 ms delay.  The interpretation of the resulting correlations would be more difficult in realistic HF noise. 2 ms corresponds to a 600 km difference in path length; the measurement may not be sensitive enough for proposed purposes.

These signals, implemented during one scheduled quiet second each minute, would facilitate improved Doppler and time-of-flight estimation without disturbing any current use.  The signals left undisturbed include the second/minute/hour ticks, scheduled tones, IRIG time code, and voice announcements.  Once per minute estimation is frequent enough for much of the current work in ionospheric sounding.  It would increase the scientific utility of WWV/H quite considerably.

## Design of signals for purpose-built transmitters

Signals designed for amateur radio transmission or for modulation of other dedicated radio transmitters might include several of these modulations in sequence.  A decision point would be if the signals are full-carrier AM, full-carrier single-sideband (à la CHU) or single-sideband suppressed carrier.  The first of those might chosen for simplicity and for facilitating measurements by lowest-cost receiving stations; the last for greatest signal-to-noise ratio for a given available transmitting power but at the expense of transmitter complexity and receiver requirements.  The middle method constitutes a difficult to generate signal but of reduced total bandwidth.

Such a transmitting station could be designed for broad deployment.  Even at amateur power levels of one kilowatt down to 100 milliwatts, meaningful measurements could be made of all the parameters discussed above. 

A published sequence of modulations might include second ticks on a schedule similar to WWV/H, and then in rotation by second

 - Silence for product detector noise analysis
 - Costas spread-spectrum, USB, for combined time of flight and Doppler (could be AM)
 - Steady tone, USB, for Doppler (could be AM)
 - Barker code AM for time of flight
 - Maximum-length sequence
 - Silence for AM detector noise analysis
 - Data burst for station identification, station power level, etc.

A periodic radiotelegraphy ID could be made, perhaps occupying one transmitting minute out of each ten for FCC and other national regulatory compliance.  The Morse code ID could itself be used as a measurable signal, especially for time-of-flight.  An autocorrelation matched filter could be implemented as part of the overall decoding and data reporting system.  We use every part of the signal except the heterodyne squeal.

This schedule would provide the span of signals for distributed small-instrument receivers providing a continuous stream of information available for central repository interpretation, graphing and storage.

An IRIG code could be added at 100 Hz, identical to WWV/H codes.  This code might provide yet another matched-filter coding or simply provide time and date information for those wanting “most accurate” automatically set clocks.

## Conclusions

Without damaging any of NIST’s functions and directives in disseminating time and frequency information via medium- and shortwave radio, a new added functionality of ionospheric sounding could be added.  While this would not change NIST’s distribution of measurement standards, it could facilitate a commercial function of space weather forecasting.  This in turn could improve data distribution to users needing such knowledge, especially electric power and telecommunications industries.  Amateur radio experimentation prior to and in parallel with deployment on utility transmitters and commercial transmitters is quite in keeping with 47 C.F.R. § 97.1.


[^1]: [https://www.ncdxf.org/beacon/intro.html]
[^2]: Motivations vary.  WBBM (780 AM) in Chicago and KNX (1070 AM) in Los Angeles use tight frequency control to suppress co-channel beat interference. while WFAN (660 AM) in New York City and KFI (640 AM) in Los Angeles appear simply to have implemented frequency accuracy for its own sake.  See S. Smith, J. Moore, “A Precision, Low-Cost GPS-Based Transmitter Synchronization Scheme for Improved AM Reception”, IEEE Transactions on Broadcasting, 55: 1, March 2009
[^3]: https://www.nist.gov/pml/time-and-frequency-division/time-services/wwvwwvh-scientific-modulation-working-group
[^4]: NSF searches on funded research using WWV/H signals have found several hundred projects, plus amateur use for communications channel propagation information.
[^5]: The term “spread-spectrum” is used here to indicate a signal that fills the regular channel bandwidth with short bandlimited signals.  It is not being used in the sense of spread spectrum communication, which spreads the communications channel over a wider bandwidth than the channel itself occupies.
