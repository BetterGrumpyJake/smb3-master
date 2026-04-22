vine eats munchers and jelectros

prg1
ObjNorm_Vine:
	JMP VineCheck
	NOP
	NOP

end of bank
VineCheck:
	CMP Tile_AttrTable,Y
	BLT VineNotSolid
	CMP #TILEA_MUNCHER
	BEQ VineNotSolid
	CMP #TILE4_JELECTRO
	BEQ VineNotSolid
	JMP PRG001_AC80
VineNotSolid:
	JMP PRG001_AC86
	
Bounce_TileReplacements:
	.byte CHNGTILE_DELETETOBG
	
prg8
LATR_QBlocks:	.byte $20, $20, $20, $20, $20, $20, $20, $30, $20, $20, $20, $20, $20, $60, $20, $70, $20