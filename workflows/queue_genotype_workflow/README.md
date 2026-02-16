### Queue Genotype Workflow (QGW) tool config

This directory tracks the **configuration** used by the Galaxy Tool Shed tool **“Queue genotype workflow”** (`queue_genotype_workflow`, v1.0.0).

The tool wrapper executes a Python script via `$__tool_directory__/queue_genotype_workflow.py` and reads settings from `qgw_config.ini` (same directory). The config determines:
- which **Galaxy instance** the tool talks to (via BioBlend),
- which workflow(s) it invokes (selected by **workflow name**),
- paths/names used for “All Genotyped Samples” bookkeeping.

#### Live deployment location (UOL Galaxy VM)

On the UOL VM, the Tool Shed install lives under:

`~/galaxy/database/shed_tools/toolshed.g2.bx.psu.edu/repos/greg/queue_genotype_workflow/<revision>/queue_genotype_workflow/`

#### Files tracked here
(NB: removed API keys)
- `qgw_config.PSU.ini` — snapshot of the historical PSU config 
- `qgw_config.UOL.ini` — snapshot of the config for UOL
