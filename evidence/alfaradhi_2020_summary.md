Omniknight Dota2 macro



#NoEnv ; for compatibility with future AutoHOtkey releases
#UseHook
#InstallKeybdHook
#InstallMouseHook
#SingleInstance, force
#Persistent

^Numpad0::ExitApp ; Ctrl + 0


; 1 : Soul Ring + heal self and then move to cursor location
; toggle auto atk off first then on at last
~Numpad1::
{
SetKeyDelay, 10
SendInput, sn!q
Sleep, 350
SendInput, m
return
}

; 0 : go to cursor location and cast Soul Ring Purification
~Numpad0::
{
SetKeyDelay, 10
SendInput, s{Shift down}{RButton up}{RButton down}n!q{Shift up}
return
}


; 2 : blink, soul ring, purification at cursor location
~Numpad2::
{
SetKeyDelay, 10
SendInput, s{Shift down}{Space}n!q{Shift up}
return
}

; 3 : Soul Ring, repel
~Numpad3::
{
SetKeyDelay, 10
SendInput, sn!w
return
}

; h : Soul ring and heal at cursor location (for eg. heal ally if they are within purification cast range)
~h::
{
SetKeyDelay, 10
SendInput, snq
return
}


; 4 : Dominated creep goes to cursor location to explore there and then returns back to your hero location
; overridable by "5"
~Numpad4::
{  
SetKeyDelay, 10
while (!GetKeyState("5")) {
    SendInput, 1s{Shift down}
    SendInput, {Click Right}
    Sleep, 41
    MouseGetPos, xpos, ypos
    MouseMove, 1160, 20, 0
    SendInput, a
    SendInput, {Shift up}
    SendInput, {F1}
    MouseMove, 2*xpos, 2*ypos, 0
    break
}
return
}

; 5 : Centaur creep stomp at current cursor location and then return to hero location
~Numpad5::
{
SetKeyDelay, 10
SendInput, 1s{Shift down}
SendInput, {Click Right}q
Sleep, 41
MouseGetPos, xpos, ypos
MouseMove, 1160, 20, 0
SendInput, a
SendInput, {Shift up}
SendInput, {F1}
MouseMove, 2*xpos, 2*ypos, 0
return
}

; 6 : Dominated creep atacks cursor location (target)
~Numpad6::
{
SetKeyDelay, 10
SendInput, 1s
SendInput, a{Click}
SendInput, {F1}
return
}

; 7 : Use creep skill at it's current location and return to hero location
~Numpad7::
{
SetKeyDelay, 10
SendInput, 1s
SendInput, q
Sleep, 41
MouseGetPos, xpos, ypos 
MouseMove, 1160, 20, 0
SendInput, a
SendInput, {F1}
MouseMove, 2*xpos, 2*ypos, 0
return
}

; Dominated creep returns to you
~F12::
{
MouseGetPos, xpos, ypos 
MouseMove, 1160, 20, 0
SendInput, 1a{F1}
MouseMove, 2*xpos, 2*ypos, 0
return
}

; d blink, ghost and phase escape (use after repel cast)
~d::
{
SetKeyDelay, 10
SendInput, {F1}s
SendInput, {Space}zx
return
}
; #Warn ; Enable warnings to assist with common errors
SendMode Input ; Better speed and reliability for newer scripts
SetWorkingDir %A_ScriptDir% ; Ensures a consistent working directory
