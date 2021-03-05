# Candidate_Selection
## Curation of Suspect List
### Libraries used:
import pubchempy as pcp,
import pandas as pd,
import numpy as np,
import time,
from rdkit import Chem,
import re,
import wget,
import urllib.parse.

### NAMES VS SMILES
Read the Suspect list; remove entries with NO SMILES
Check whether the names vs SMILES are correct or should I add new names; also check synonyms, iupac names, inchi, molecular weight, molecular formula, and CID for every check even the ones made later.
Add this information into the original suspect list based on their index.
Some SMILES are not correct or are isomeric and hence pubchempy cannot identify them. Use rdkit to convert isomeric to canonical smiles; some smiles still have wrong syntax hence we can check them at the end (save these). After conversion to non isomeric smiles, extract information for these smiles from pubchempy.
Remove the entries for which PubChemPy still gave error or there was no compound at all.
Add this point 5 information into the original suspect list based on their index.(also add a column for these non-isomeric smiles just for future reference) (also convert the list of synonyms as string)

### ADD STRUCTURAL INFORMATION AND WRONG INDEX SMILES
Take all entries that don’t have SMILES; remove empty names or unknown names.
Add structural information to the names
For those with more CIDS→ check manually and add non-isomeric smiles. For those with wrong names, check their names and add information manually.
Some names will still not in be in PubChem
Earlier for compounds with wrong SMILES, use their names to add correct smiles.
Repeat from above steps 2, 3, 4, 5.
Add all of this information to the original suspect list!

### CHECK LITERATURE REVIEW, OTHER DATABASES:
Following are the lists: unknown names, empty names, canonical smiles with no PubChem id, Wrong names part 1, 2 and 3.
Check all of them manually → link
Add index and their CIDs and add that information to the suspect list. While extracting the index that had incomplete information and stored into another small list.
Remove the duplicates
Add information on their classification using NPClassifier API.
For error ones check and change the index of the NPClassifier file.
Add monoisotopic masses since you changed them earlier; and name the numeric mass as molecular mass column.
Create one for Saskia, removing unwanted columns, rearranging them and removing more duplicates.
