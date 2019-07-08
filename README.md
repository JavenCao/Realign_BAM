# Tailored_thalassaemia

This is a collection of scripts for tailored thalassaemia mutation detection pipeline by next-generation sequencing technology.

A typical working example is illustrated as follows:

Suppose now we have 3 samples with NGS data(such as whole genome seuqncing data, or targeted sequencing data):

Step1: Follow workflow described in repository Easy_WES, and get the Bam file for each sample in the follwing structure:

    |    |/home/data/WESproject/
    |    | -- Raw_data
    |    | .... ignore here
    |    | -- Bam_file
    |    |   | -- Sample1
    |    |   |   | -- Easy_WES_XXX_Sample2.pbs
    |    |   |   | -- good_Sample1.bam   
    |    |   | -- Sample2
    |    |   |   | -- Easy_WES_XXX_Sample2.pbs
    |    |   |   | -- good_Sample2.bam   
    |    |   | -- Sample3
    |    |   |   | -- Easy_WES_XXX_Sample3.pbs
    |    |   |   | -- good_Sample3.bam   
    |    | -- VCF_file
    |    | .... ignore here

Step2: Create another working fold for rescue process:

    mkdir /home/data/WESproject/Rescue_Phase

Step3: Within /home/data/WESproject/Rescue_Phase, run the workflow in the repository Thala_Rescue, and you will have the follwing structure:

    |    |/home/data/WESproject/
    |    | -- Raw_data
    |    | .... ignore here
    |    | -- Bam_file
    |    | .... ignore here
    |    | -- VCF_file
    |    | .... ignore here
    |    | -- Rescue_Phase
    |    |    | -- Bam_file
    |    |    |    | -- Sample1
    |    |    |    |    | -- Thala_Rescue_Sample1.pbs
    |    |    |    | -- Sample2
    |    |    |    |    | -- Thala_Rescue_Sample2.pbs
    |    |    |    | -- Sample3
    |    |    |    |    | -- Thala_Rescue_Sample3.pbs
    |    |    | -- VCF_file
    |    |    |    | -- Sample1
    |    |    |    |    | -- Thala_Rescue_RunHC_Sample1.pbs
    |    |    |    | -- Sample2
    |    |    |    |    | -- Thala_Rescue_RunHC_Sample2.pbs
    |    |    |    | -- Sample3
    |    |    |    |    | -- Thala_Rescue_RunHC_Sample3.pbs
    |    |    |    | -- Joint
    |    |    | -- Easy_WES_jointGT.pbs
    |    | -- submit.sh
