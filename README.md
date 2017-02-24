# Chordtable

This package has a simple purpose: it is based
on [guitarchordschemes](https://www.ctan.org/pkg/guitarchordschemes) and provides predefined
commands for typesetting tabulatures of the most common guitar chords in TikZ, as well as a
mechanism to put them in a nice-looking full-page table.

For a finished table, look at the [example file](./examples.pdf) (as of yet, not all chords are
defined!)

## Commands

### `chordtable` and `rightchordtable`
A slightly modified table suitable to the chord diagrams of the package.  Can be used like a normal
table:
  
	\begin{chordtable}
	\notename{C} & \CMaj & \CMin & \CSeven & \CMinSeven & \CMajSeven \\
	\notename{\tsharp{C}/\tflat{D}} & \CSharpMaj & \CSharpMin & \CSharpSeven &
	                                \CSharpMinSeven & \CSharpMajSeven \\
    % etc.
	\end{chordtable}
	
`rightchordtable` is for putting the note names to the right, if one wants to use the table on a
recto page.

### Typesetting commands

`notename`, as used above, typesets the name of a note in a box, to fit into the `chordtable` name
column (does vertical centering).
  
`\tsharp`, `\tflat`, `tminor`, etc., are semantic commands for typesetting chord names. They work in
the expected way: `\tminor{\tsharp{A}}`.


### Chord definitions

As many usual chords as possible are tried to be predefined. The naming scheme should be clear from
examples: `\ASharpMaj`, `\ASharpSeven`, `\ASharpMinSeven`, etc. There are suffixed `Dim`, `Aug`,
`SusFour`, `AddNine`.

Chords are tried to be always provided in both enharmonic variants. The definitions consist of a
`\chordscheme` from `guitarchordschemes`, inside a `\newchord` command to define the enharmonics:

	\newchord{ASharpMaj/\tsharp{A}, BFlatMaj/\tflat{B}}{%
		\chordscheme[
			name=\chordname,
			position={},
			barre={1/1-5},
			finger={3/2,3/3,3/4},
			ring={},
			mute={6}
			]
		}
		
`\newchord` is a kind of "template replacer. Its first argument is of the form
`<command1>/<chordname1>, ..., <commandnameN>/<chordnameN>`; `\chordname` is context-dependent and
gets replaced by the current chordname.

## License

This work is [unlicensed](http://unlicense.org/). 

The code in [guitarchordschemes-custom.sty](./guitarchordschemes-custom.sty) is derived from
the [guitarchordschemes package](https://www.ctan.org/pkg/guitarchordschemes) by Clemens
Niederberger, which is LPPL licensed.
