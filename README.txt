*** Introduction ***

GemmaLib is a set of ‘Pure Data’ abstractions that allow one to easily create high quality musical apps that run on mobile devices through the application called Gemma. (currently only available on iOS)

GemmaLib uses ‘GEM’(Graphics Environment for Multimedia) to easily design a graphical interface of an app on the desktop platform by taking the advantage of its real-time programming environment and flexibility.

Since it’s currently not possible to use‘GEM’ on mobile platforms, the abstractions that contain ‘GEM’ externals will be replaced by pure vanilla abstractions which simply forward the drawing info (e.g shape, size, color) to ‘openFrameworks’ when a patch runs on the mobile device through the Gemma app.

You can find some examples of what you can build with GemmaLib from our website www.iceblinkdigital.com.

GemmaLib works on 3 platforms (Mac OS X, Windows, Linux)

GemmaLib uses some external libraries that are mostly used in abstractions that make the development process easier. None of these externals will be supported when the patch runs in the Gemma app. So you are allowed to use only GemmaLib abstractions and vanilla objects in order to make the patch runs in Gemma app without any problem.

GemmaLib works in both the vanilla and the extended version of Pure Data except for only one abstraction called [t.myhero]. The abstraction uses an object [text] that currently only works in vanilla currently. 

GemmaLib contains all the necessary externals itself including ‘GEM’ so you don’t need to install any externals in order to use GemmaLib.

When you install GemmaLib using the installer, the ‘gl’ folder will be copied to the user specific library path of Pure Data which differs depending on your Operating System.

After the installation, you can call abstractions of GemmaLib in the Pure Data patch by typing into the ‘object box’ as the example below.

Example: [gl/p.display]

’gl’ is a library name (GemmaLib), ‘p’ is a namespace which is used to sort abstractions by common characteristics and ‘display’ is a name of an abstraction which tells what it is or what it does.

You will be able to see more details of what each abstraction does by opening its help file.

You can see the full list of GemmaLib abstractions sorted by the namespaces below.


*** Abstractions overview ***

1. Primitives

p.display - create a display window
p.rectangle - draw a rectangle to the display window
p.circle - draw a circle to the display window
p.triangle - draw a triangle to the display window
p.image - draw an image to the display window
p.label - draw a label to the display window
p.font - store fonts that can be used by ‘p.label’
p.scope - draw a scope to the display window
p.pos - get the canvas position of the parent abstraction
p.wavdata - get data of a wav file


2. Graphical control elements

g.button - draw a button to the display window
g.toggle - draw a toggle to the display window
g.vslider - draw a vertical slider to the display window
g.hslider - draw a horizontal slider to the display window
g.xypad - draw an xypad to the display window
g.knob - draw a knob to the display window

3. Receivers

r.accel - accelerometer receiver
r.closebang - receive bang when ’back' button on the display is pressed
r.touchid - receive nth of the touches when any touch on the display is made

4. Text file handlers

t.myhero - text file based state saving abstraction (vanilla only)
t.saveme - text file based state saving abstraction (vanilla only)
t.preset - read and write a list based preset from/to a text file

5. Development related

start - create a set of startup objects at once 
d.auto - auto complete abstraction
d.abs2sub - create a subpatch and copy/paste contents of the target abstraction
d.dspstate - get and set the dspstate of pd.

6. Audio signal based

a.bltriangle~ - bandlimited triangle wave oscillator
a.blsaw~ - bandlimited saw wave oscillator
a.blsquare~ - bandlimited square wave oscillator
a.blpulse~ - bandlimited pulse wave oscillator
a.multiwave~ - bandlimited oscillator with waveform selection
a.lpf2~ - 2 pole low pass filter with resonance control
a.bpf2~ - 2 pole band pass filter with resonance control
a.hpf2~ - 2 pole high pass filter with resonance control
a.lpf4~ - 4 pole low pass filter with resonance control
a.bpf4~ - 4 pole band pass filter with resonance control
a.hpf4~ - 4 pole high pass filter with resonance control
a.multimode~ - filter with multiple modes
a.adsrc~ - adsr envelope generator with curve amount option
a.playwav1~ - play a wav file in mono
a.playwav2~ - play a wav file in stereo
a.wavsampler1~ - advanced wav file player with mono output
a.wavsampler2~ - advanced wav file player with stereo output

7. Control message based (will be added)

8. Examples (will be added)


*** Usage of folders ***

GemmaLib contains some folders that are mainly used to put files to be used by GemmaLib abstractions.

‘abs’ folder is mainly used to put Pd abstractions that are not being used by themselves but only being called by other Pd abstractions that are in the ’gl’ folder.

‘audio’ folder is used to put audio files that can be used by audio related abstractions that are in the ‘gl’ folder. Only ‘wav’ files are allowed to be used in Gemma.

‘font’ folder is used to put font files that can be used by ‘p.font’ abstraction in the ‘gl’ folder. Only ‘ttf’ and ‘otf’ files are allowed to be used in Gemma.

‘image’ folder is used to put image files that can be used by ‘p.image’ abstraction in the ‘gl’ folder. Only ‘png’ files are allowed to be used in Gemma.

‘text’ folder is used to put text files that can be used by abstractions that use the preset loading feature (primitives and graphical control elements) as well as by the text file handling abstractions.

Each of these folders can have a folder named ’shared’ which allows you to make the files in the folder accessible by the users of your Gem, provided that your Gem is submitted to us and available on the Gem Store.

It can be useful if you want to, for example, let users of your Gem add or replace the audio files that your Gem is using or let them store their own preset settings of your Gem by downloading the preset text files.


*** Accessing to the ’shared’ folder ***

Connect your iOS device to your Desktop, open iTunes and go to the file sharing section and find the Gemma app.

- Downloading shared files

If you want to download all shared contents of a Gem, create a folder named ‘-d Gemname’ and drag & drop the folder into the file sharing section of the Gemma app.
In the Gemma app you have to go back to the main view and tap the ‘My Gems’ section to refresh the Gems you currently have in your device. After refreshing the folder will contain all shared files in it if it has any.

- Uploading files to the shared folder

If you want to upload any file into the shared folder of a Gem, the easiest way to do it is to first download all the shared files using the method above and then put the files you want to upload into the proper folder (e.g. audio, text). Then, rename the folder to ‘-u Gemname’ and then drag & drop the folder into the file sharing section of the Gemma app.
After refreshing the folder will be deleted if the uploading is properly done.
It will overwrite the files that have the same name when you upload them.

- Replacing the shared folder

It is basically the same as uploading files to the shared folder except that it will replace the whole shared folder contents with the one that you will upload. You can do this the same way as uploading but by renaming the folder to ‘-r Gemname’.

* if you want to download/upload files to/from only a specific shared folder, you can do it the same way as described above but by adding ‘shared folder name’ when renaming the folder.
For example, ‘-d -text Gemname’ will only download shared files in the text folder of the Gem. It applies the same way for uploading and replacing.


*** Testing your Gem on iOS devices ***

In order to test your GemmaLib based Pd patch on your iOS device, you should first have the ‘Gemma’ app installed on your device since your patch is only executable through the Gemma app on iOS.

You can test your patch by transferring the ‘Gem project’ folder to the Gemma app on your iOS device through the file sharing on your iTunes.

The ‘Gem project’ is a folder that contains your main Pd patch as well as a ‘gl’ folder that has all the necessary local files such as images, fonts, audio and text files.

Your main Pd patch must have a ‘p.display’ abstraction. Otherwise the patch will not be able to be executed in the Gemma app.

Your ’Gem project’ folder and the main Pd patch in it should have the same name since the Gemma app will find and open the patch based on the name of the folder it is in.

For example, if the name of your ‘Gem project’ folder is ‘Monster Synth’, your main Pd patch file should be named ‘Monster Synth.pd’ inside the folder.

The ‘p.display’ abstraction has the feature of automatically creating a ‘Gem project’ folder whenever you save the patch to a new location. You can find more info from the ‘p.display’ help file.


