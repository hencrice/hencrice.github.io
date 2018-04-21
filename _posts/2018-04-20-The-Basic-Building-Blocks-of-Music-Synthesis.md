---
layout: post
title: The Basic Building Blocks of Music Synthesis
tags: Coursera Music
---
This is a short writeup of the things I learned regarding music synthesis while browsing [Berklee Music - Creating Sounds for Electronic Music](https://www.coursera.org/learn/music-synthesizer/)

## 1. Oscillators (VCOs)

These are the sources of sound, also called VCOs (voltage-controlled oscillators). The oscillators generate sound based on pre-defined waveforms.

Quite often the pitch can be modulated. For example, by pressing different keys on a keypad.

### Qualities of Different Waveforms

Square wave: Sounds hallow compared to sawtooth waves (because it's missing the even harmonics in the frequency spectrum)
Sawtooth wave: sounds bright, harsh and full (because it contains all the harmonics).

### Relation Between a WaveForm and How A Sound Is Generated

The waveform is actually related to how a sound is initially created.

For example, clarinet sound can be synthesized from square waves because it's played through a reed, which opens up and closes down very quickly.

Another example is to synthesize string sounds. We'll started with sawtooth waves because strings are usually played using a bow and it pulls against the string until the tension on the string is strong enough so that it snaps back (“slip and stick” motion).

## 2. Filters (VCFs)

Low-pass filters are probably the most important types of filters because many types of oscillators generates high-frequency harmonics that can sound very harsh.

<img src="https://lh3.googleusercontent.com/VvJIBX9HISon3lkpvX_QeOuyMP6ZNuG33tU5mRWBI8T9cWP2WZDPkIOH1B94Ps5wZA0SEdxUsq8cOifJtNyloAEPTKOhRx7RlIhh_z2Z1JzMkQCueCKOpw-tw_5vPQFSSzdFKTcpgORW3PQHVLP1xnCyN2hI8nW5qCKaYLtyaybLSPFj0lcOkbJLJLoAfAP6DY2c5tQ_hddPayN8U_ta2LMs4_w-FU7OB6iVLLX_8QMpC0bdY663pA_0tsNzwwRkER5djyovRxOHOjkJ-wkKRvOSR9OMNGHUL4eDqW14et6wcPoU_h08FXH2fPnSr3Knn0LLJhySmXZDpJfCL7Cjcjru7mmmLNVi3tcyk1n6DuXzzALXV4O4_EFDpGWmNSbFZ8AyptoYxtgSB0Qf4YP4PQ5Z2dR1nKcdEFv0z04gaf1LiMbxOOfC-7zOgdv1DqL09U7aL1R38Y1Z4jTX9VXnD85IpCb0l4uGnsEdplzmnaJPZZzq08YW6tkL-U_qXKcpVUNHCNVV_-Gp-mZP-w4wvgakM20jSFn4LrT5FSiLf2Byjk1vrEuRTXtBM5MHQSjeJEX42o6qU0qwr7OsD5xshsk9-9uBOVmWoKq4Cc9CDmNWMyq6T6Dspozpf6ZiW5hkibIVnHvZTiJmuA0idLM9xS2n2VSDvFsGgw=w1428-h615-no" width="75%">

Since the filters operate on the frequency spectrum, we can use them to change the timbre of the sound from bright/harsh to dull.

> The most useful thing to remember is: If you use a patch and it's too bright/dull, try to change the cutoff frequency knob.


Due to the existence of the resonance, filters can actually boost signals in certain frequency and the “sound” of filters plays an important role in synthesizer. However, it doesn't mean that you have to emphasize certain frequencies for all patches. A lot of them work fine without it.

It's also possible to modulate (i.e. changes it over time) the cutoff frequency by LFOs or other envelopes.

## 3. LFOs (Low-frequency oscillators)
<img src="https://lh3.googleusercontent.com/iBjGjiUN5fIEp0FHw51hcnZC8soK7kIFeVQaUxQmjC7IFzEAw5l8SRx0DfwwWRi0TVIr-KF8vsSWwdDvrwb2uOlCTRoE3DSZLVQZ0p7F1E6u32KaXtBW0LiV4vGzuoDIFRXuFS3iN4DdTkIw3LueWNp3-YxmcfY14Z_ubqHcEsa5DPRPE0LcmBPs38k_FqZ1P1eaaL9-KC1StmRohHYuKHfPz71I0TGcuJDMp4u1cjUo9TFScDsvo5zs02BHBqZClnG8vUZpL0yD5zQaNNToI7W4VtIZVzkbZ3E0bKQQTsDHWoUQ9oxmZE40vKt1mYEFo8fZNT3owBxyBQw0Toj104JCIS0AyxZQBG0YegOvLTbhWxDNpwudWwUQ0TTnGuFFpqDYuYbtE-AksxbrUWr9ptTM2ReVCzECuqUkIqM7fC5TS_Rxafk8L_xpdMXOMfau3mmkW-QnleEAjD8wHevKepZykVUt7VTtILkJyJBthHbl6Lb4sO4z3Cq55NytP8QnDYwaW0_ZRLZa80VVVcp3fEsSsLHXPnTlj2jy1yMmZZ9qa4Jzkisic41kTTkDyBsZqCnMN6w33xsEn2w8uH8WXTaHAbbe_ooqG_dqll6EohqJ6XWnF_N44T68mlNVPckTlahnJcSKlq6hT1Flylgw92OfxKX6yYklTA=w721-h220-no" width="75%">

It's a type of modulator designed to control another parameter within a synthesizer.

The “low” in LFO means that the frequency is below the range of human hearing (<20Hz). However, you can still select different types of waveforms, just like in an oscillator.

### The 3 critical aspects for a modulation:

1. The source of modulation. For example, in this case a LFO.
2. The destination of modulation. For example, frequency of an oscillator.
3. The amount of modulation.

Quite often, this is in a form of matrix to convey the 3 pieces of information above (sometimes it can even be just hard-wired).

**Note that the relationship between a modulation source and a destination does not need to be 1-1**. For example, one LFO might control multiple destinations with different amount of modulation.

## 4. Amplifiers

There's always a specific modulator, envelope, attached to an amplifier.

<img src="https://lh3.googleusercontent.com/sJgnCh1sP_ZVddq5Uv7ypVndpI2oIeTJ0T7YS5MEd0eN4PRTZdmvv7FwRsWAGLt6Krq-UFc9ltfz-CfMsz8A6tWBZFkI-Reb2Vfklydt8WdBk2Mx4DB7sqpSISBh7CLafUQ2EcYEFqjQ99kdfe7OxzK89oVOMd8WngpUTLxIbibe2eajNeysSqZPgS9IDsXT-2ADnXnYBjNQMZTGZ4uAipmTlp3wbCafbVEuqAyPRFXUtDTshYQq7Bk3Y8nRTMFE_mdoYsldxv0GjsjJgR9YIibDOa0p9K-PdEEE56DA4UgUmL_Yx_eIvqhq01uxm8FDVfegssGA-D34E2jcKizISH1LRTF7C-dHcu70hAquQUcUbP3mqfitd92Uar1qnE4MPoeXErsaQgIgh89RG-6PWGp6ZTCoJA7pky3dMp0fWSAiisk9NkCCkQGGwy_hv8eJc1gqEeWBC2SXdH__WnncSbEUHZVDvg5q3l04mSno_mWMKkcbE6L5MNrb0uM3H47U-YLMimV4dRw4hukCiYCfWOcVnSCmfbY51qqDz-YLn5aAb_avMDfCSVlbffJ3VpwXHkRT0PkIpICRq5tls4CH9zS8PhXVRVot3yZYkToR1voBJmPnksXN-GAtVcfv7Pv8nmIyk7qm1rIY1JuUx4LRcQy0JyqDx5AgOw=w720-h388-no" width="75%">

This envelope runs every time a key is pressed, from left to right.

4 most common controls: “ADSR”, namely, “Attack time”, “Decay time”, “Sustain **level**” and “Release time”.


* In synthesizers, high attack time actually translates to a sound taking longer to be audible.
* The attack in the diagram above is linear. However, there might be other types. For example, attack might increase exponentially. This is true for release/decay.

### How ADSR is best Used To Synthesize Sounds

1. Envelope with sustain level configured. This is good for emulating instruments like strings or brass. Basically, things that can hold the note or add more energy as the note is held.
    1. More specifically, it's common to see a sustaining envelope with a strong attack. This is applicable to instruments like a trumpet, where a large burst of initial energy, then it dwindles down to a sustain level.
2. If the sound is generated by a pluck or hit, then sustain level should be 0 and decay time can be used to control the length of a note.

## References

1. [Berklee Music - Introduction to Music Production](https://www.coursera.org/learn/music-production)



