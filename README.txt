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