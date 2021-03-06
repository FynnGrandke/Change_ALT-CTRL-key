# Change Control Key with Alt Key

If you program on a Mac and also have have a PC with Windows installed the keybindings for ALT and CTRL are switched and this can be quite annoying in some cases.
That's why I created this repository to make it as easy as possible to switch these two keymappings. (No third party tools required!)

## Prerequisites

### Methode 1  
For safety reasons create a 'restore point' under System Properties -> System Protection.  
If something went wrong you can always go back to the time before using this script.  
![before keymapping screenshot](./img/beforeKeymapping.PNG)  

### Methode 2  
Another option is to go to your 'Registry Editor' and export your current system environment by right clicking on 'Computer' and then export.

## Procedure

Execute the .reg file Change_ALT-CTRL-key and restart your computer. 
The changes should then be reflected as expected. (Be careful that ALT + TAB will no longer switch between Windows tabs anymore!)

## Explanation

> [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]

The location where in the Registry Editor we want to change or add an entry.

> "Scancode Map"=hex:00,00,00,00,00,00,00,00,05,00,00,00,38,00,1d,00,1d,00,38,00,38,e0,1d,e0,1d,e0,38,e0,00,00,00,00

What we want to change, where 'Scancode Map' is the command to change a keymap and the hexadecimal value is which keymaps we wish to change.

The value of the new scancode map:
**00,00,00,00** Version of the header. All zero.  
**00,00,00,00** Flags we want to set. All zero.  
**05,00,00,00** How many entries we want to change (4 keymaps + null entry).  
**38,00,1d,00** Change Left CTRL to Left ALT.  
**1d,00,38,00** Change Left ALT to Left CTRL.  
**38,e0,1d,e0** Change Right CTRL to Right ALT.  
**1d,e0,38,e0** Change Right ALT to Right CTRL.  
**00,00,00,00** Last entry as null entry.
