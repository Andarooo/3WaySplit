# 3 Way Split

### An open source split keyboard. (yeah we really needed more of those (¬_¬) )

## Layout

As you might have guessed this keyboard is split into 3 parts. A left, right and numpad.
Left and right is split in the middle but follows a standard layout with the right side squished in and a couple extra macros for use on the left side.
Numpad has a couple extra macro keys as well if you want to use them.

## Firmware

Keyboard was made with intention to utilise [ZMK](https://zmk.dev/)
I have made a [matching ZMK repo](https://github.com/Andarooo/zmk-3waysplit) with config setup to take the expected layout with the assumption of a nice!nano or equivalent dev board has been used.

## Start Here

Let's say you want to take my slop of gerbers and STLs and make a functional keyboard what are we going to need?
 - Time & money
 - A 3D printer or a 3d printer service
 - A soldering iron
 - Time & money
 - Access to a PCB printing service like PCBWay or JLCPCB
 - A bunch of random crap most likely off Amazon (boo) or Ali-Express (not a boo but it's still not great)
 - Time & money

 If you have enough time and attention span that you're still reading then you might be in a hyperfocus spiral; maybe go get some more coffee. But also keep reading in order and you should have a decent idea on how to get this keeb up and running. I'll try to structure everything in the order that you would expect to do it in. Anyway, without further ado let's throw ourselves into:

 ## Parts

 So here's a list of all the random bits to get off your horrifying conglomerate market of choice:
 - SOD-123 diodes (107)
    - I went for 1n4148 but any that'll fit the sod-123 form and work with keebs will do.
 - Hotswap sockets (107)
    - These PCBs were made with the intended use of kailh hotswap sockets, any that fit will work so don't get too precious about it
 - Developer boards (3). 
    - The PCBs are made with the nice!nano in mind, you could modify the PCB files and regenerate gerbers and change that but if you're cabable of that why are you looking at my crappy design?
    - You could also use any of the knock of nice!nanos which are significantly cheaper (sorry Nick Winans); especially if you live outside the US. (googling pro micro or nice!nano will probably get you somewhere) 
        - The companies that make these are kinda trash because they're exploiting someone else's R&D. I you can buy the real deal pls do, but also business is business y'know.
    - You'll need one per part of the keeb so go ahead and buy 3.
 - M3 screw hot inserts.
    - You use a soldering iron to push these into a slot which adds a threaded insert so you can screw stuff together.
    - These are relatively cheap and you can buy the special soldering iron tips for pushing them in but you don't actually NEED them most of the time.
 - M3 screws.
    - What did you think the inserts were for?
    - You'll likely need a few sizes between 4mm to 20mm so I'd recommend just buying one of those assorted packs.
    - I chose to use allen/hex screws but any will do as long as the heads fit in the hole provided.
 - Keyswitches
    - It is a custom keeb, so I'd assume you knew about this one if you're reading this.
    - There's honestly too many options for me to go into here so I guess just google it or watch some weird cringy keebfluencer.
 - Keycaps
    - See above.
    - I did mess up and chose to have a 2.5u spacebar without realising they're actually pretty uncommon so you can eiter just use a 2.25u with a gap or go track one down. Most sets will have the 3u spacebar that I designed the right side for
 - Key stabilisers
    - These are for the longer keys.
    - All the stab slots are meant for the regular 2u stabs so don't get a spacebar stab; it won't get used. (I think there's 7?)
 - USB C cables to flash firmware and charge etc.


## PCB Printing

So this bit is actually way easier than it sounds, but you jump on the website of the pcb printer of our choice and upload the gerbers which are in the [gerber directory](https://github.com/Andarooo/3WaySplit/tree/main/PCB/Gerbers). It'll take a little while and for the most part just choose the standard settings. We only need the regular 2 layer PCB and also change the mask colour to whatever you'd like to see (I got purple).

## PCB Assembly

This keeb is actually pretty easy to assemble because I couldn't figure out how to get LEDs or even the caps/num/scroll locks lights working.

The keeb has 107 keys in total, does that mean you'll be soldering 107 parts? No of course not, you'll be soldering about 215. The parts that need to be soldered are SMD (Surface Mount Device) which are finicky as fuck to attach to a board if you don't know what the hell you're doing.

If you don't have any soldering experience you'll first want:
 - A soldering iron.
    - I recommend a cheap modern temperature controlled one like a pinecil or ts101 you'll need a fast charging brick that pumps out like 65W and a decent USB C cable too to power it. (Yes different cables will deliver different amounts of power)
 - Solder
    - I'd recommend leaded flux core as it's much easier to melt and work with, just don't lick it I guess.
 - Tip Tinner
    - It's like a powder which keeps your tip tinned (metal and shiny).
 - Flux resin/flux pen
    - For when the solder just doesn't wanna stick.
 - Wet sponge/paper towel
    - Gotta keep that tip clean.
 - A decent video on how to solder.

Soldering SMD parts can be annoying but in general it comes down to 3 steps:
1. Melt some solder onto 1 (not both) pad.
2. Put the part on and re-melt the solder to attach the part.
3. Add solder to the other pad to connect up the other side of the part.

It's much easier to do the sockets than the diodes because I'm an idiot and thought it'd be fun to choose the smaller SMD form factor.

***REMEMBER THAT DIODES HAVE A DIRECTION***

Don't solder them around the wrong way or the switch will not work. There's a thin line on one side which shows the cathode (-). This needs to go away from the the socket so make sure the side that you're soldering to the trace that goes straight to the socket doesn't have the line.

Similarly don't put the sockets on upside down, It'll be really obvious because you'll cover the hole that the middle of the switch usually goes in.

If you mess anything up then watch some videos on desoldering and buy some solder wick or a sucker I guess.

For the microcontroller board, there is some assumptions that I've made with regards to how it's mounted in my case design. If you don't want to mount it the same way I have planned then go and modify the case STLs. It's meant to be mounted with the standoffs on the underside of the case. The bottom of the dev board should be exposed. Just make sure the pins on the dev board match the keeb PCB and you should be sweet. Measure twice cut once. The USB C port should be exposed to the hole in the case if everything has been done right.

## Printing the case

This bit should be pretty straightforward if you've done some 3d printing before. 

There are 3 sets of parts; the plates, the enclosures and the feet. I would recommend printing the plates first to get an idea of how well your printer will handle it and if it will fit the build. The right side is the largest so if you can print the right enclosure you'll be g.

The case STLs are made up of a top and bottom piece, I'll leave that to you to work out on the slicer. They attach together later using the m3 screws and inserts.

I've never used a 3D printing service before so If you want to go that route I wish you luck but I can't provide advice.

## Adding the heated inserts

This part is actually pretty fun and satisfying. So as I alluded to earlier you can buy these special soldering iron tips that fit into the top of the m3 inserts. You don't need it and it doesn't make much difference TBH but It'll probably save you from accidentally poking the back of the hole with the tip of your iron.

There's not a whole lot to this really. make sure the insert is the right way around with the thinner bit going in first then push it in with the tip of your soldering iron giving light even pressure until it's fully seated. Preferably it should be flush with the surface, but if it goes a bit deep you just might need a slightly longer screw so nothing that bad. Try to keep it going in straight if you can.

Each top part of the enclosure has slots where the inserts are meant to go to support screws from the bottom.
Each bottom part has slots for where the feet will attach. ***Do not put the inserts in the screw holes which go all the way through**

## Firmware + Test

You should probably flash the firmware before you assemble as you'll need access to the controller boards to put them into bootloader mode. First go to the [zmk-3waysplit](https://github.com/Andarooo/zmk-3waysplit) repo and navigate to actions (near the top). Then click on the last successful workflow run and scroll down to the Artifacts where there should be a firmware artifact which you can download. After downloading this you should be able to unzip each of the firmwares for each part.

Connect the board to the pc using a USB C cable and it should enter in bootloader mode where it will essentially open as a mounted drive (like a flash drive or similar) if it isn't in bootloader mode simply short the reset pin to the ground (should be next to it) twice in quick succession using some wire or tweezers etc.

Now simply copy the appropriate firmware file onto the root directory of the drive and it should reset. You should now essentially have a working keeb or part there of. And can test each switch by shorting the contacts on each slot again using wire or tweezers or something else metal. I would reccommend testing the whole keeb before assembly as now is the best time to fix dodgy soldering etc.

## Assembly

This is the real fun bit where everything comes together. Assuming you've done everything right this should be a cakewalk.

Make sure to put in your stabilisers before the switches, you can watch a video or just work it out. It's not rocket science

Then start by adding a couple switches into their slots in the plate, preferably on the corners then push the the switches into their PCB slots to marry the PCB and plate together. Make sure you put the switches in the right direction and orientation when attaching to the plate; though it will be pretty obvious if you mess up and can be easily remedied.

Once that's done add the switches one by one making sure they're fully inserted into the pcb and clicked into place in the plate. It's easy to bend a pin if you're not paying attention while adding the switch to the pcb slot. If this happens just carefully remove it and try and bend the pin straight again with some pliers or something then be careful putting it back in this time. Always worth having a few spare switches for this reason.

Once all your switches are all inserted it's time to assemble the enclosures. It all fits together like a sandwich with the plate in between. Do a dry fit first to get an idea of how the keeb will all go together and don't force anything; any printing defects can be cut or sanded to fit so don't break stuff because you thought yourself a caveman.

I would also recommend putting some padding where the plate gets sandwiched into the case to help with noise. I just used some double sided foam tape with the plastic linine unremoved. This is the "gasket" in gasket mounted design. No clue if it actually does anything to the sound so feel free to explore this.

Screws go in from the bottom into the inserts in the top. There are various sizes for each part. The numpad should be 2x 20mm screws and 2x 16mm screws. I designed it first; can you tell? The others should all be 10 or 12 depending how deep you added the inserts.

Now it's time to add your keycaps. If you bought a set they should be in the correct arangement. Otherwise I guess refer to the [layouts](https://github.com/Andarooo/3WaySplit/tree/main/Layout) I've made as to where everything should go. or just google it I guess. You can also change the layout with your own by forking the zmk config I have and making your own. Crazy huh?

The feet attach with a couple of 4mm screws and should face with the rounded side of the feet towards the front of the keeb.

And that's it. Thanks for reading all of this. It took me an evening to write up so I hope someone gets through it.
