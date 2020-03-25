# SpheroinCluster
To develop spherocity analisis in cluster for pp real data


//============== Some escential  steps ===============
// When produce its say, then a cluster analysis is done @xook
 
 //---- Produce So and St (true and measured) for perC--------------------
1.- Produce Equalization for Data(Per0 as data) using So: get Merge,
         SOpp13TeV_MERGE_newbinsSOPCSOEQSo_PER0.root
2.- Produce Equalization for Data(Per0 as data) using St: get MErge,
         SOpp13TeV_MERGE_newbinsSOPCSOEQSt_PER0.root
 //---- Get the distributions for ESA percentil ---------------------------
3.- Run NormAbsSoSt.C and we get HistPercPP13000_PER0asdata.root
     save as HistPercPP13000.root in /~/set1 
 //-- Produce So distributions and response Sopc vs So for get intervals--- 
4.- Produce GetSpherocitySpectrum for Data(Per0 as data) using So: get Merge,
         SOpp13TeV_MERGE_newbinsSOPCSO_PER0asDat.root
 //--- Get So intervals for bining from the percentil binning -------------
5.- Run GetSoIntervals.C and we get SoIntervals_Per0asdat_100Nchbins.root
    save as SoIntervals_Per0asdat_100Nchbins.root in /~/set1
 //--- Produce Sot vs Som correlations for correction with MC -------------
6.-Produce GetSpherocitySpectrum  for MC (EPOS) to correct using Newbins for pc So intervals
       SOpp13TeV_MERGE_newbinsSOPCSO_EPOS4corr.root 

//--- Get the So Response normalized matrix ---------


PostProcesing   (All seems included in macro produceplotsFeb2017.C)

//--- We can get the Response Matrix for MC (EPOS) -------
   MakeNchResponseMatrix("SOpp13TeV_MERGE_newbinsSOPCSO_EPOS4corr.root","BuildingNchRM_EPOS") 
//--- Make the Efficiency for MC (EPOS) ---------
   MakeTestEfficiency("Efficiencypt/EfficiencyPerc10_EPOS.root", "PicturesEfficiency_EPOS")
//--- Make the resolution
   MakePerformanceResolutionsVsNtrk("SOpp13TeV_MERGE_newbinsSOPCSO_EPOS4corr.root", "PicturesEfficiency_EPOS")
//--- Get SPECTRA corrected by Eff & Sec.
   MakeCorrectionEfficiencyCorrPt("/Users/hbelloma/Desktop/FORMEANPT/DataPer0_corrEPOS/postprocesing/SOpp13TeV_MERGE_newbinsSOPCSO_PER0asdataALL.root", "PicturesEfficie     ncy_EPOS/EfficiencyCorrection.root", 0, "MeanPtInput")  


//--- Get the So Response normalized matrix ---------
  … etc.

//--- Proced with post processing macros --------
