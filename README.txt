PRG000_C713:
	;LDA Level_TilesetIdx
	JSR PswitchCheck_30
	
prg30 end of bank
PswitchCheck_30:
	;if it's not a p switch carry on with the quicksand check
	CMP #TILEA_PSWITCH
	BNE PswitchCheckNo
	;stores #CHNGTILE_PSWITCHSTOMP into Level_ChgTileEvent and gets the coords of the tile to change it to pressed switch
	LDA #CHNGTILE_PSWITCHSTOMP
	STA Level_ChgTileEvent
	LDA ObjTile_DetYHi
	STA Level_BlockChgYHi
	LDA ObjTile_DetYLo
	STA Level_BlockChgYLo
	LDA ObjTile_DetXHi
	STA Level_BlockChgXHi
	LDA ObjTile_DetXLo
	AND #$F0
	STA Level_BlockChgXLo

	;set the normal p switch timer countdown and music
	LDA #$80
	STA Level_PSwitchCnt
	JSR PswitchSound
PswitchCheckNo:
	;load this back into A for quicksand and continue on
	LDA Level_TilesetIdx
	RTS

PswitchSound:
	LDA #SND_LEVELBABOOM
	STA Sound_QLevel1
	LDA #MUS2B_PSWITCH
	STA Sound_QMusic2
	RTS