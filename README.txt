statue and shoe kills enemies and shells koopas
stops kicked shells and thrown ice blocks
side affect: 
	sideways piranhas become shelled without fixing
	green spiny eggs become shelled
	
PRG000_D272:
	BEQ PRG000_D29B	 ; If OA3_SQUASH NOT set, jump to PRG000_D295 (kill it)

PRG000_D295:
	LDA #OBJSTATE_SHELLED	 ; State is Killed

PRG000_D29B:
	CMP #OBJSTATE_KILLED