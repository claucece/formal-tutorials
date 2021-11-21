# How to install EasyCrypt and Jazmin

For MacOS:

## Installing easycrypt:

1. Install ocaml and opam:

	```
	brew install ocaml opam
	opam init
	eval $(opam env)
	```

	(note that on some MacOS versions you don't need to execute `eval $(opam env)` as it
 it for you in your terminal).

2. Pin easycrypt: `opam pin -yn add easycrypt https://github.com/EasyCrypt/easycrypt.git`.
3. Install the needed dependencies:

	```
	opam install --deps-only easycrypt
	opam install alt-ergo
	```

4. Configure why3: `why3 config detect`.
5. Install easycrypt: `opam install easycrypt`.

	Note that on many occasions, you will need to add Z3, which you can do as:

	```
	brew install z3
	opam install alt-ergo.2.3.1 (in case it cannot find the prover)
	```
6. Check your installation:

	```
	Check that you can run: easycrypt
	```

## Installing jasmin

1. Clone the repository:

	```
	git clone --branch glob_array3 git@github.com:jasmin-lang/jasmin.git
	cd jasmin
	```

2. Install nix: `curl -L https://nixos.org/nix/install | sh`, and follow the specific instructions.

3. Run:

	```
        nix-shell
	cd compiler
	make CIL
	make
	make check
	exit
        ```
4. Check that it exists:

	```
        jasmin/compiler/jasminc
	```

## EasyCrypt extra flavors

### Documentation

The old documentation lives [here](https://github.com/EasyCrypt/easycrypt-doc).
The folder `obsolete` can be used for reference but note that it is obsolete.
In order to create a pdf of that folder's information, you can:

For MacOS:

1. Install mactext: `brew install --cask mactex`
2. Move the `multind.sty` from `common` folder to `obsolete/userman` one
2. In the `obsolete/userman` folder, run: `pdflatex  common/easycrypt-common.tex`

### Emacs integration

The interface you can use for the proof assistant is [Proof General](https://github.com/ProofGeneral/PG).
You can install:

For MacOS:

1. Install emacs via cask, as recommended [here](https://www.emacswiki.org/emacs/EmacsForMacOS#toc14): `brew install --cask emacs`
2. Use MELPA and run (on emacs):

	```
	M-x package-refresh-content
	M-x package-install
	proof-general
	```

