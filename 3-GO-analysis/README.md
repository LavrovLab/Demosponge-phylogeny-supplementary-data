# GO-analsyis

## Matrix preparation
1. Used gogo to do the analysis of G4comp
2. Removed/edited unusual genes 
	Changed unusual anticodons: trnI(aau) --> trnI(gau) in Adreus, trnR(acg) -> trnR(ucg) in Cliona and trnL(caa) -> trnL(uaa) in Heteroxia_sp_nov in all.go
	filter -genes trnX #homology not known
	filter -orders 33 22 (DM_Hamacantha_johnsoni, DM_Desmacella_informis) #incomplete
	filter -orders 14 15 18 46 #problematic genomes (DM_Corallistes_floreana, DM_Corallistes_sp, DM_Craniella_wolfi, DM_Neophrissospongia_sp2)
	filter -genes trnX(uua) #from Stelligera stuposa
	filter -genes trnY2(aua) #from Negombata magnifica
	export test.fa -format fasta #this saves go format
3. The final matrix is saved as demo_go.fa
 
## MEMG analysis

1. Removed duplicaed  genes 
	in Cymbaxinella and Stylissa based on the results of our  previous study
	in Vetulina according to the ancestral position
	om Plenaster removed trnV from the cluster and the end

2. export test.fa -format fasta %% this saves go format
`-/usr/local/bin/my_scripts/splitGO test.fa`
`-/usr/local/bin/my_scripts/skiptRNA *.go`

3. using vi saved the matrix and the set of species names from gorder.dat

## ME analysis 
1. -Renamed `test.fa` to `68taxa_cleaned.fa`
2. -Opened `68taxa_cleaned.fa` in gogo (`open 68taxa_cleaned.fa`)
3. Exported in MPME format: export 68taxa.nex -format nexus -encoding MPME
4. -extracted matrix and species list as below and used nex2tnt R script to make a TNT file
5. edited TNT file for RAXML (changed order of two numbers in the first lane, removed ; at the end.
6. Ran analysis as: `-/usr/local/bin/raxml-ng --all --msa 68taxa.phy --model MULTI13_MK --prefix T68 --threads 1`

## ML analysis with RAXML-NG and TNT
-For TNT commands see .tnt data file
-Used nex2tnt script to make a file and edited it in vi
-/usr/local/bin/raxml-ng --check --msa 49taxa.phy --model MULTI9_MK --prefix T1
-/usr/local/bin/raxml-ng --all --msa 49taxa_reduced.phy --model MULTI9_MK --prefix T2 --threads 1
-/usr/local/bin/raxml-ng --support --tree T2.raxml.bestTree.tre --bs-trees T2.raxml.bootstraps --prefix T3 --threads 1
-NOTE, we don't have to use the reduced dataset, but it runs much faster if we do.
