# GenericCNC
Simple Generic CNC control firmware for dsPIC30F3011 Microcontrollers.
Communication is on UART 1, 8n2, 9600 Baud.

Schemadic is in PDF format, "CNC.pdf"

###############################################################################
###############################################################################

#: This is a list of commands and responce codes for this CNC machine.
#: Action commands respond with a "c", they will be listed here with a "@".
#: All commands are case sensitive.

Tool Rotation Timeout is about 5 - 6 seconds. If the tool Rotation input does 
not get a pulse within 5 - 6 seconds of an action command AND the Tool Power is
not 0, the tool output will be shut of and the tool status light will blink.
To reset you must press the Stop/Pause button and send a pulse to the Rotation
input, then un-pause the machine.

###############################################################################
CNC responce codes.

#: On command receive the microcontroller will send an 
 acknowledged responce "a" back to the computer.

#: On a succesfull action command the microcontoller will 
 send a "c" for "completed" but only after send the acknowledge 
 responce AND after completing the command.

#: If an E is sent then an error has occured.
#: If an SE is sent then a syntax error has occured.



###############################################################################
CNC command codes.


#: "#" Resets the microcontoller.

#: "T" Tool movement config. How many times the tool rotates before stopping. (0 - 9)
	"0" means rotate forever. Default is 0.

#: "E" Local Echo. (y - n)
	Default is "n".

#: "S" Head Speed Ramp Up/Down. Ramps the stepper motor speeds when starting/stopping.
	Default is "n". (y - n)

#: "M" Head Max Speed. Max speed of stepper motors. (0 - 99)
	Default is "99"

#: "C" Tool Ready input. What input is used for Tool Ready. The Tool Ready input, or the
Tool Rotation Input.	Default is "r".		(r - c)

#: "O" Tool Head order. What starts first, the Tool or the Head. (t - h)
	Default is "t".
		:: If set to "t" the head will not move until tool ready is SET
		    unless the "R" config is set to "n".
		:: If set to "h" the CNC will not send a "c" command complete
		    until tool ready is SET unless the "R" config is set to "n".



@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Action Commands.

#@: "R" Tool Ready. Waits for tool ready status to be ready before continuing. (y - n)
	Default is "n".

#@: "P" Tool Power. PWM percentage of the tool control output. (0 - 99)
	Default is "0"

###################################
Head Movement.

#@: "X" X axis command. Format (xxxx). Example for a movement of 46 steps, (X0046).

#@: "Y" Y axis command. Format (xxxx). Example for a movement of 105 steps, (Y0105).

#@: "Z" X axis command. Format (xxxx). Example for a movement of 3000 steps, (Z3000).

#@: "A" Aux axis command. Format (xxxx). Example for a movement of 2 steps, (A0002).



###############################################################################
###############################################################################


