# hapltype
1.haltype.py
This script processes haplotype information using the `hastat` tool based on user-provided parameters.
It supports filtering by minimum allele frequency (MAF) and allows analysis of specific genomic regions
or genes based on GFF annotations.

Usage:
    python haltype.py --maf <maf_value> -a <gff_file> [-r <region> | -i <gene_id>] [-u <upstream>] [-d <downstream>]

Arguments:
    --maf (str): The minimum allele frequency for filtering haplotypes. 
                 Choices are '0', '0.01', '0.02', '0.05'. Default is '0.05'.
    -a, --gff (str): The GFF file containing the gene annotation. when refer 6K rice haplotype, it should be os1_r7.gff.
    -r, --region (str): The region of the gene to be analyzed in the format `chr:start-end`.
    -i, --gene_id (str): The gene ID for the target region, which should be provided with the GFF file.
    -u, --upstream (int): The upstream distance of the gene. Default is 0.
    -d, --downstream (int): The downstream distance of the gene. Default is 0.

Functionality:
    - If a region is provided (`-r`), the script generates haplotype information for the specified region.
    - If a gene ID is provided (`-i`), the script generates haplotype information for the specified gene.
    - The script uses the `hastat` tool to generate three types of outputs:
        1. Haplotype table (`hap_table`).
        2. Haplotype group (`hap_group`).
        3. Haplotype frequency (`hap_freq`).
    - Outputs are saved to files with names based on the MAF value.

Error Handling:
    - If neither a region nor a gene ID is provided, the script logs an error and exits.
    - If both a region and a gene ID are provided, the script logs an error and exits.

Dependencies:
    - Python modules: argparse, logging, os, sys, subprocess.
    - External tool: `hastat`.

Example:
    python hapltype.py --maf 0.05 -a annotation.gff -r chr1:1000-2000 -u 500 -d 500
