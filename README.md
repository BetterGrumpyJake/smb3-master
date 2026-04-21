ObjNorm_BusterBeatle:
	CMP #TILEA_BRICK
	
PRG002_A5AE:
	LDA #OBJSTATE_KICKED
	STA Objects_State,X
	; jump to our routine to decide what to throw
	JSR BusterCheck
	NOP
	NOP

PRG002_A587:
	JSR BusterProxCheck
	BCS PRG002_A5A1
	NOP
	
BusterCheck:
    LDY <SlotIndexBackup    ; get busters slot index
    LDA Objects_Var5,Y      ; get the y variable we stored earlier
    CMP #$02                ; if it equals 2, then:
    BEQ BusterShell   ; branch to throwing koopa routine

    LDA #OBJ_ICEBLOCK       ; otherwise use ice brick, (could change this to anything?)
    STA Level_ObjectID,X     ; store ice brick here
    RTS

BusterShell:
    LDA #OBJ_GREENTROOPA    ; loads green koopa and stores it (could change this to anything?)
    STA Level_ObjectID,X
    RTS
	
BusterProxCheck:
	LDY <SlotIndexBackup
	LDA Objects_Var5,Y
	CMP #$02
	BEQ BusterThrowNow
	LDA <Temp_Var15
	CMP #$0c
	RTS
BusterThrowNow:
	CLC
	RTS