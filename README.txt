;stationary shell
PRG000_CB10:
	JSR Object_HandleConveyorCarry

;kicked shells
PRG000_CC75:
	JSR Object_HandleConveyorCarry

;delete some nops at line 3158
	; Unused space... deleted code?
	NOP
	NOP