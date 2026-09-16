# mod_clockwork_picnic
The direct follow-on from Cold Boot. I've dialled the LLM's intelligence down to its lowest setting.

## A ChatGPT mod in Instant mode! Can it do it?
Err... no, turns out it can't. ChatGPT Instant is great for architecting the piece, the sample selection and designing the rhythmic and narrative arcs and all that. The low-power profile means we should still use it for all that good stuff. But it can't write patterns for toffee.

I'll kick it up to Medium to write the patterns.

## result

Pretty good, but doesn't quite live up to the initial spec.

### *Jaunty*? You call this *jaunty*?
Well, no. The first efforts were definitely jaunty. I had to slow the roll considerably to make it believable as a piano piece. We ended up with this. I'd say it's more *chill* than *jaunty*. But I think it's still listenable.

## build notes
To get the ST-01 and ST-02 archives on Debian-based Linux, issue these commands:
   
    ❯ sudo apt update
    ❯ sudo apt install lhasa wget
    ❯ install -d mod_cold_boot/stxx
    ❯ cd mod_cold_boot/stxx
    ❯ wget -O st-01.lha https://aminet.net/mods/inst/st-01.lha
    ❯ lha x st-01.lha
    ❯ wget -O st-01.lha https://aminet.net/mods/inst/st-02.lha
    ❯ lha x st-02.lha

These samples are in IFF format and AmigaOS doesn't use file extensions, so to make MilkyTracker see them you have to rename the ones you want with '.iff' extensions. Like this:
   
    ❯ mv Stabs Stabs.iff
