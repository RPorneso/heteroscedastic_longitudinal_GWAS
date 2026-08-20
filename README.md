Simulation codes and analytic pipeline repository for the manuscript "**Longitudinal modelling reveals putative non-additive genetic loci in trait developmental**". Link to publication: https://www.cell.com/cell-reports/fulltext/S2211-1247(26)00918-6.

To re-create the simulations:

1. Download all functions in 0. dgm and 1. power. Update directories where required. **Note** that the functions use parallel::mclapply suitable for Mac users to distribute jobs across multiple cores. For Windows users, you may simply change mclapply to lapply but the runtime will be longer depending on the number of iterations.
2. Run the scripts for power and bias analysis.
3. To assess power and bias of our pipeline against TrajGWAS, you will need Julia. To install and run TrajGWAS, please refer to: https://github.com/OpenMendel/TrajGWAS.jl.

**OPTIONAL:** To check how genetic interactions generate SNP variance effects, refer to Pilot.pdf under 0. dgm/interaction/. Codes are available in Pilot.Rmd.

A few notes on the analytic pipeline:

1. Each phenotype per time point was residualized on the GRM using GCTA.
2. The order of the analysis dataframe containing the phenotype and covariates must be aligned with the genotype file (using the .fam file).
3. The pipeline runs on multiple cores and nodes in parallel using HPC Colossus (Linux). It is computationally intensive.
4. The inputs in the bash are: blocks (cores), number of SNPs per block, total number of SNPs, analysis dataframe, plink files, and output files.
5. Each output file contains 2000 SNPs. They need to be combined into 1 summary statistics file.
6. Since we relied on LRT to assess SNP mean and variance effect, we repeated the analysis two times for significant SNPs where a) we added PCs in the residual, and for those that remain significant, b) isolated "variance" SNPs by comparing a mean only against a mean-and-variance model.
7. Variance SNPs are sensitive to non-normality. It is recommended to transform non-normal phenotypes and rerun the pipeline to see if the detected SNP variance effects are scale-dependent.

**Citation**

Porneso, R., Havdahl, A., Eilertsen, E. M., & Ystrom, E. (2026). Longitudinal genome-wide analysis reveals putative non-additive loci in trait development. Cell Reports, 45(8), 117840. https://doi.org/10.1016/j.celrep.2026.117840

**Preprint**

Porneso, R., Havdahl, A., Eilertsen, E., & Ystrom, E. (2025). Longitudinal modelling reveals widespread non-additive genetic effects underlying developmental plasticity. bioRxiv. https://doi.org/10.64898/2025.12.19.695443

**Acknowledgement** 

This work was funded by European Union’s (EU’s) Horizon Europe research and innovation program under the Marie Skłodowska-Curie grant agreement (no. ESSGN 101073237), the EU grant agreement (grant no. 101045526, project GeoGen), and by Sigma2 (grant no. NS9867S).
