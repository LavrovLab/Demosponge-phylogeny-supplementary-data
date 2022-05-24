## G2 analysis
Added subscripts to some trnM.
Four gene orders filtered: 
4 gene orders filtered:
```
DM_Chondrilla_nucula
DM_Halisarca_caerulea
DM_Halisarca_dujardini
DM_Aiolochroia_crassa
```

Checking Pseudoceratinidae and Thymosia:

## G3 analysis
`open all-g3.cc` #Loaded the files all_g3.cc (14 gene orders)
`list -all` #Display gene orders
```
filter -orders 2 6 9 10 11

# 5 gene orders filtered:
# DM_Amphimedon_queenslandica
# DM_Haliclona_indistincta
# DM_Neopetrosia_sigmafera
# DM_Niphates_digitalis
# DM_Niphates_erecta
```

Changed the name of trnA(ngc) to trnA(ugc) in X. muta
Created a matrix of adjacencies and saved it to a file:
`adj -outfile 77taxa_adj.txt`
