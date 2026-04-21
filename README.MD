GiantPiranha_TimerReloads:
	.byte $01, $FF, $FF, $FF

PRG004_B79D:
	LDA <Player_HaltGame
	BNE PRG004_B7FD	 ; If gameplay is halted, jump to PRG004_B7FD (RTS)

	INC Objects_Var3,X	 ; Var3++

	LDA <Objects_Var4,X
	AND #$03	; Keep internal state counter 0-3

	JSR DynJump

	; THESE MUST FOLLOW DynJump FOR THE DYNAMIC JUMP TO WORK!!
	.word GiantPiranha_HideInPipe	; 0
	.word GiantPiranha_Chomp	; 1
	.word GiantPiranha_Chomp	; 2
	.word GiantPiranha_Chomp	; 3