# keys

I created a new keyboard layout for coding <br>
I use 2 layout on my PC and switch them when I need one of them<br>
And this is my settings<br>

### !! Warning !!
We will change system settings. Be careful, think twice before start and take your own risks ! <br>
Copy files to somewhere before editing :)

#### Resource
https://rlog.rgtti.com/2014/05/01/how-to-modify-a-keyboard-layout-in-linux/ <br>
[web.archive.org](https://web.archive.org/web/20210926164837/https%3A%2F%2Frlog.rgtti.com%2F2014%2F05%2F01%2Fhow-to-modify-a-keyboard-layout-in-linux%2F)

## Creating a new layout
~~~
// in /usr/share/X11/xkb/symbols/tr

// add this code after   xkb_symbols "basic" { ... };
// my edit
partial
xkb_symbols "my_layout" {

    include "tr(basic)"
	
    key <AC11>  { type[group1] = "FOUR_LEVEL_SEMIALPHABETIC",
                  [  idotless,  Iabovedot,    apostrophe,    dead_caron ] };
    key <AD08>  { type[group1] = "FOUR_LEVEL_ALPHABETIC",
                  [         i,          I,   icircumflex,   Icircumflex ] };
                  
    key <BKSL>  { [  scedilla,   Scedilla,         grave,    dead_grave ] };
    key <AC10>  { [     comma,  semicolon,         acute,    dead_acute ] };
	
};
~~~

## Updating rules files
~~~
// in /usr/share/X11/xkb/rules/evdev.lst and /usr/share/X11/xkb/rules/base.lst
// (same code should added)

// after   ! variant
// add this to top of other tr: codes

my_layout       tr: Turkish (i-idotless and scedilla-comma swap)
~~~

~~~
// in /usr/share/X11/xkb/rules/base.xml and /usr/share/X11/xkb/rules/evdev.xml

// add this inside "Turkish" "variantList"
<variant>
          <configItem>
            <name>my_layout</name>
            <description>Turkish (i-idotless and scedilla-comma swap)</description>
          </configItem>
        </variant>

~~~

It's done !
Restart your pc and configure settings
