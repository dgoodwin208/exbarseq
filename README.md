All this code is shared "as-is," with admittedly little commenting. 

ExBarSeq_stitching.ipynb shows how Terastitcher was used to stitch the 14 fields of view per sequencing round

Not shown is how the downsampled stitched data was then copied into an ExSeqProcessing directory and then affine warped to create a rough estimate.

Also not shown is how the virtual FOVs (vFOVs) can be created using the affine warps calculated by the ExSeqProcessing pipeline. Briefly, in the 3_registration folder, there is both the warped image files (eg, "rseqds-downsample_round001_ch00_affine.tif") and the affine transform warp information (eg, "affineTForm_rseqds-downsample_round001.mat"). Depending on memory constraints, you can either apply the affineTForm file yourself on subsections of the data or simply let the ExSeqProcessing pipeline apply it for you. 

We then moved each vFOV into its own ExSeqProcessing folder system to conduct a second affine transform to accomplish a higher resolution warp. 

Once the vFOVs have been warped, you can use code like in exbarseq-cell-extract.ipynb and then exbarseq-fullstitch-original.ipynb to discover present barcodes from the cell bodies. Then, puncta-level analysis could be done something like exbarseq-punctaextract-integration, which utilizes the ExSeqProcessing puncta segmetnation to discover and align individual amplicons.

Please feel free to post issues to the ExSeqProcessing pipeline github for support in using these attached scripts.  http://github.com/dgoodwin208/ExSeqProcessing

 
