# squarp-pyramid-instruments




## Definition File Format:

    NAME:<Name of the Instrument>
    OUT:<Midi Output: A|B|USB>
    CHANNEL:<MIDI Channel 1…16>
    <0…127>:<CC-Target Name>
    <N0…119>: <Note Name>

Only the first 8 characters are displayed for Instrument names and CC targets, for note names only 4 characters are availble

## Pararameter Naming Conventions

The character set is rather limited, there are no lowercase characters, only a few special characters overall (11), some of which are mapped to another character, and a few symbols. See the section below for details on supported character set.

Having to work with an 8 character limit for parameter names when even a simple synth comes with 40 controllable parameters, is a challenge.

This is an approach to naming conventions that work across the synths of different manufacturers and  make effective use of the 8 characters and the available symbols.

There's no "correct" or perfect way for doing this, and consistency beats personal preference. I'll develop these naming conventions incrementally for the devices I own, since that's my use case. Until then, this documentation will change quite a bit

Since there are only uppercase characters, [Camel case](https://en.wikipedia.org/wiki/Camel_case) is not possible to separate between words without an extra character. Also many of the symbols I would have used as visual representations of building blocks of (virtual) analog synthesizers are not available here.

Here's a first draft for encoding parameter names (for all cases where encoding is necessary, i.e. if there are not enough characters available):

- Oscillator: 'O', 'O1'
- Suboscillator: 'SO'
- Noise: 'NZ'
- Filter: "F" or 'F1', or "LP"/'LPF' and 'HP'/'HPF'
- Resonance: Q
- Level: 'Lv' or 'Lvl'
- Envelope: the ramp symbol '=', '=1'
- LFO: up arrow '>', '>1'
- Depth (=Intensity): 'DPT', even better is it to use right arrow (`!`) for source/target 
- Mode: 'MD'
- Type: 'TY'
- Interval: 'IVL' (to avoid confusion with "Intensity")
- Rate: 'Frq', 'Spd' or 'Rt' (inconsistent for now)
- Detune: 'DET'
- Octave: 'OCT'
- Effects: the 'fx symbol', '}' or '}1'
- Arp: `;`: note symbol


All letters are uppercase in the definitions, so that it is simple to spot where readability is not good. Lowercase letters obscure that at times.

Some Examples:

- Cutoff: when there is only one filter, and parameter name is less than 9 characters, no encoding is necessary
- OSC1 LVL: Oscillator 1 level
- SUB2 LVL: Suboscillator 2 level
- O2-DET
- `>1!O2PI`: LFO1 to Oscillator 2 Pitch
- `=1!O2PI`: Env1 to Oscillator 2 Pitch


## Suported Character Set

I tested the subset of [ASCII characters 32-127](http://asciiset.com/) that is available on my US keyboard. (you can load chartest.txt to see for yourself).

-   simple characters (work as expected):
    -   `A-Z` (or `a-z`): upperchase characters
    -   `0-9`: Digits 
    -   `.#-:_` and _space_: work as expected 
-   usable but misrepresented characters
    -   `*`: quotes
    -   `+`: `?`
    -   `{`: `%` 
    -   `'`: `[`
    -   `?`: `/` 
    -   `[`: minus sign (duplication)
    -   `@`: dot (duplication)
-   (potentially) helpful symbols
    -   `$`: magnifying lens symbol
    -   `}`: 'FX' (you get two characters as one)
    -   `=`: ramp up
    -   `;`: note symbol
    -   `]` or `\`: arrow left
    -   `!`: arrow right
    -   `<`: arrow down
    -   `>`: arrow up 
    -   backtick: F (kind of)
    -   `~`: dot (superscript)
    -   `,`: b or flat symbol
    -   `/`: an alien looking to the left
-   unusable characters:
    -   `%^&("`: yield no result at all (not even a space)
