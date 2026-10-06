# C. Elegans Cell Information

The goal of this repo is to organize known information about C. elegans cells into a single, machine-readable source.

## Lineage information
The canonical embryonic lineage has been parsed from AceTree and stored as lineage_tree.geff. We plan to extend this to post-embryonic lineages for both male and hermaphrodite C. elegans.

## Linage to name mapping
`lineages_to_names.csv` contains a mapping from lineages to names. Usually, only cells that are present in the adult worm are named, so non-terminal lineages and lineages that die before maturation are excluded. Lineages that combine into one syncytial cell share the same name.

These exact names are used in all other data in this repo. There is a known aliases dictionary in `cell_name_aliases.json` that map other variants to these known names.

## Tissue types and cell categorization

Cells are often categorized along a number of axes, e.g. tissue, location, function. `tissue_type_hierarchy.json` encodes a categorization hierarchy. Any cell at the leaf of a hierarchy is tagged with all categories in the hierarchy. Also, cells can be listed in multiple leaf categories. For example, TL is listed as both a Seam Cell in the Epithelial section, and a Socket Cell in the Nervous system section, and as such gets tags: `nervous system`, `neuronal support`, `socket`, `epithelial`, `seam` (the union of each node's own `tags` along every ancestor path from root to the leaf categories it belongs to).

This list is not yet complete - it should not be counted on to include male specific cells, non-terminal cells that still have special names (e.g. tail spike scaffold cells), cells that appear after hatching (e.g. seam cell descendants). The current state should be able to classify/tag every cell present at hatching.