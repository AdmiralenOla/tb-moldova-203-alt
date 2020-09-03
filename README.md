# tb-moldova-203-alt

Code to replicate:

`augur refine -a data/MoldovaUral203_010920_filtres.vcf.gz -t results/tree_203_filtres.nwk --output-tree results/tree_203_refine_filtres_timetree_CONVERGED.nwk --vcf-reference auxiliary/M_tuberculosis_H37Rv.fasta --metadata data/metaUral203.tsv --timetree --output-node-data results/branch_lengths_203_filtres_time_CONVERGED.json --clock-filter-iqd 3 --coalescent opt --root least-squares`

`augur ancestral --tree results/tree_203_refine_filtres_timetree_CONVERGED.nwk --alignment data/MoldovaUral203_062620.vcf.gz --vcf-reference auxiliary/M_tuberculosis_H37Rv.fasta --inference joint --output results/nt_muts_203_filtres_time_CONVERGED.json --output-vcf results/nt_muts_203_filtres_time_CONVERGED.vcf`

`augur translate --tree results/tree_203_refine_filtres_timetree_CONVERGED.nwk --ancestral-sequences results/nt_muts_203_filtres_time_CONVERGED.vcf --vcf-reference auxiliary/M_tuberculosis_H37Rv.fasta --genes config/genes.txt --reference-sequence config/Mtb_H37Rv_NCBI_Annot.gff --output results/aa_muts_203_filtres_time_CONVERGED.json --alignment-output results/translations_203_filtres_time_CONVERGED.vcf --vcf-reference-output results/translations_reference_203_filtres_time_CONVERGED.fasta`

`augur traits -t results/tree_203_refine_filtres_timetree_CONVERGED.nwk --metadata data/metaUral203.tsv --columns country --output-node-data results/traits_203_filtres_time_CONVERGED.json`

`augur sequence-traits --ancestral-sequences results/nt_muts_203_filtres_time_CONVERGED.vcf --translations results/translations_203_filtres_time_CONVERGED.vcf --vcf-reference auxiliary/M_tuberculosis_H37Rv.fasta --vcf-translate-reference results/translations_reference_203_filtres_time_CONVERGED.fasta --features config/DRMs_AAnuc.tsv --label "Drug resistance" --output-node-data results/drms_203_filtres_time_CONVERGED.json`

`augur export v2 --tree results/tree_203_refine_filtres_timetree_CONVERGED.nwk --metadata data/metaUral203.tsv --auspice-config config/config.json --colors config/colors.tsv --lat-longs config/lat_longs.txt --node-data results/branch_lengths_203_filtres_time_CONVERGED.json results/traits_203_filtres_time_CONVERGED.json results/drms_203_filtres_time_CONVERGED.json results/aa_muts_203_filtres_time_CONVERGED.json results/clades.json results/nt_muts_203_filtres_time_CONVERGED.json --output auspice/tb-moldova-203-filtres-CONVERGED.json`

