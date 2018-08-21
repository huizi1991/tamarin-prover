Obsolete: ESORICS Symmetric-only files, included for reference only.
===

*******************************************************************************

DNP3 SAv5 Symmetric Only models Tamarin file README
---

This is the README for the Tamarin files associated with ESORICS 2017 submission
''Secure Authentication in the Grid: A formal analysis of DNP3: SAv5''.
This paper can be found at https://doi.org/10.1007/978-3-319-66402-6_23

The models in this folder have been substantially built upon to create the
Asymmetric AND Symmetric version of the models to be found in this folder's
parent directory. If unsure, you want the models in `/examples/jcs18/`, not these.


Authors: Cas Cremers, Martin Dehnel-Wild, Kevin Milner.

**TL;DR: Install Tamarin. Run make on this directory. Visit http://127.0.0.1:3001/**

*******************************************************************************

Tamarin Installation & Usage
----------------------------

Follow the instructions in `examples/jcs18/README.md`, and open the Tamarin web GUI at http://localhost:3001/

Within this web-page, you then have the choice between `DNP3`, `DNP3_proven`, and
`DNP3_incorrect`.

- `DNP3` is the main (symmetric-only) model. Feel free to play around with this, or to click
  'autoprove' on any or all of these lemmas. These all auto-prove fairly quickly on modern computers, but prove fastest with the latest version of Tamarin (1.3.0 or higher, built from source). Minimum version required: 1.2.1.
  This is from the file `dnp3.spthy` (generated from `dnp3.m4`).
  If you just want to read the source-code, please read `dnp3.m4`, as this will make the most sense to the reader.

- `DNP3_proven` is the same main model, but with all the proofs pre-calculated.
  This is from the file `dnp3-proven.spthy`.
  This may take a little while to load as it has to check that the presented proofs are indeed correct. When it does load, everything should be green.

- `DNP3_incorrect` is the incorrect attack from Amoah et al., 2014 (ESORICS paper reference number [7]). This is a significant under-approximation of the main model, to make the attack work.
  Please read Section 6 of the main (ESORICS) paper for more details.
  This is from the file `dnp3-amoah-attack.spthy`.

The main (correct) DNP3 file is provided as an `m4` file, as we use m4 macros
to change the order of some of the protocol rules for the sake of proof-speed;
Tamarin solves goals for various rules dependent on the order of the rules in
the file, so the logical order as per the protocol execution is not the most
efficient for Tamarin's heuristics. Note: this DOES NOT affect the protocol
model's correctness or validity, or possible protocol execution paths, it merely
changes the order in which goals are solved.
We also provide `dnp3.spthy` pre-generated (for users without m4), but it is not
recommended that you attempt to read this version. 
Feel free to run `m4 dnp3.m4 > dnp3.spthy` to confirm that the latter file was
actually generated by the former.