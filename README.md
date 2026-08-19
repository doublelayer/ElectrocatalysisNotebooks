# Computational Electrocatalysis Tutorials

This repository is a collection of 15 executable Jupyter notebooks for learning computational electrocatalysis through worked, reproducible examples. The tutorials connect atomistic model construction and scientific visualization with adsorption thermochemistry, the Computational Hydrogen Electrode (CHE), scaling relations, activity volcanoes, machine-learning potentials, interfacial molecular dynamics, constant-potential density functional theory, and microkinetic modeling.

Oxygen reduction reaction (ORR) catalysis is the main scientific thread. Examples range from Pt surfaces and Pt–Ni alloys to metal–nitrogen–carbon sites and iron phthalocyanine (FePc). The notebooks use tools including the Atomic Simulation Environment (ASE), TBLite, UMA, SpookyNet, MACE, and GPAW/SJM. Each notebook combines background, executable calculations, interpretation prompts, a summary, and references to the relevant software or literature.

## Tutorials

The numbered notebooks form a recommended learning path, but individual tutorials can also be used independently when their prerequisites are met.

### 1. Scientific-computing foundations

1. [Introduction to Google Colab, Python, and ASE](1.1_Introduction_Colab_Python_ASE.ipynb) — Colab and Python fundamentals, molecular structures, geometry optimization, potential-energy scans, and vibrations.
2. [Building Periodic Atomistic Models](1.2_Creating_Models.ipynb) — Bulk crystals, surfaces, alloys, two-dimensional materials, nanotubes, and nanoribbons.
3. [Visualizing Electrocatalyst Models](1.3_Rendering_Models.ipynb) — Interactive and publication-quality rendering of catalyst structures and ORR pathways.
4. [Color in Scientific Graphics](1.4_Plotting_Figures.ipynb) — Perceptual colormaps, colorblind-safe palettes, accessibility simulations, and grayscale checks.

### 2. Adsorption thermodynamics and activity

5. [Calculating Adsorption Energies](2.1_Adsorption_energy.ipynb) — Molecular references, surface adsorption, vibrational corrections, and adsorption free energies.
6. [Constructing ORR Free-Energy Diagrams](2.2_Free_energy_diagram.ipynb) — CHE free-energy diagrams, limiting potentials, overpotentials, and comparison with literature DFT data.
7. [Free-Energy Diagrams: From Ideal Models to Literature Catalysts](2.3_Free_energy_diagram_literature.ipynb) — Ideal, scaling-constrained, Pt(111), FePc, and CoPc ORR landscapes.
8. [Scaling Relations in Oxygen Electrocatalysis](2.4_Scaling_relations.ipynb) — Adsorbate correlations and the thermochemical origin of scaling slopes and intercepts.
9. [Constructing an ORR Activity Volcano](2.5_Activity_volcano.ipynb) — Theoretical volcano construction, literature-data corrections, and ensemble uncertainty.
10. [OH Binding-Energy Distributions on Pt–Ni Alloys](2.6_UMA_High_entropy_alloy.ipynb) — UMA calculations of pure-surface references and alloy binding-energy distributions.

### 3. Machine-learning molecular dynamics

11. [Molecular Dynamics of a Pt–OH–H₂O Interface with SpookyNet](3.1_Pt-2D_spookynet.ipynb) — Constrained NVT dynamics and structural, chemical, and thermal trajectory checks.
12. [Visualizing Pt–Water Molecular Dynamics with MACE](3.2_Pt-water_MACE_MD.ipynb) — MACE-based Pt–water dynamics and animated trajectory rendering.

### 4. Catalyst effects, reaction barriers, and kinetics

13. [Structure and Electronic Effects in Oxygen Electrocatalysis](4.1_Effects%20in%20electrocatalysis.ipynb) — Electronic, facet, strain, curvature, ligand, and coordination effects on OH binding.
14. [Constant-Potential SJM–NEB](4.3%20SJM-NEB.ipynb) — Solvated-jellium endpoint optimization, constant-potential NEB, and activation-barrier analysis.
15. [Microkinetic Modeling of ORR on FePc](4.4_Microkinetic%20modelling.ipynb) — Steady-state coverages, kinetic current, RDE transport, and interactive sensitivity analysis.

## Setup and expectations

Work through a notebook from top to bottom on its first run. Reflection prompts are invitations to predict and interpret rather than tests. When a result differs from your expectation, first check units, signs, reference states, geometry, and the state of prerequisite cells.

Installation commands near the beginning of each notebook are intentionally commented. In a fresh Google Colab runtime, uncomment only the packages required by that notebook, run the cell once, and leave the commands commented when sharing the notebook. Notebooks that download files from Google Drive include `gdown` in this installation cell.

For a local Linux or WSL environment, create the supplied Conda environment and launch JupyterLab:

```bash
conda env create -f environment.yml
conda activate electrocatalysis-notebooks
jupyter lab
```

The shared environment covers most of the collection. Some workflows have additional requirements or licensing conditions described in their notebook, notably the UMA checkpoint and FAIR Chemistry License, the SpookyNet source installation, MACE, and the GPAW datasets used for SJM–NEB. GPU acceleration is optional, but can substantially reduce the runtime of compatible machine-learning calculations.

### Prerequisites, runtime, data, and outputs

Times are approximate and depend on hardware, model downloads, and whether saved trajectories are reused.

| Notebook | Prerequisites | Estimated runtime | Data and principal output |
| --- | --- | --- | --- |
| 1.1 | No quantum chemistry required; basic Python is helpful but not assumed. | 20–40 min | Downloads periodic-table data and may query public molecular databases; produces optimized molecules, energy profiles, a fitted vibration, and structure/data files. |
| 1.2 | Notebook 1.1 or familiarity with Python and ASE `Atoms`. | 25–45 min | Downloads selected CIF files; produces periodic models and a lattice-parameter comparison. |
| 1.3 | ASE model construction and optimization from 1.1–1.2. | About 30 min; 45–90 min with all optimizations | Downloads CIF/XYZ structures and writes rendering files; produces interactive structures, static images, an APNG, and an ORR mechanism render. |
| 1.4 | Basic NumPy and Matplotlib; Notebook 1.1 is sufficient. | 15–25 min | No scientific dataset required; produces palette comparisons, color wheels, accessibility simulations, and grayscale checks. |
| 2.1 | ASE structures, calculators, constraints, and optimization. | 30–60 min | Writes vibration trajectories and GIFs; produces reference energies, vibrational modes, thermochemical terms, and an adsorption free energy. |
| 2.2 | Notebook 2.1 or familiarity with adsorption energies and ORR intermediates. | 15–30 min after model download | Requires a large UMA checkpoint and BEEF-vdW ASE databases; produces ORR free-energy diagrams from two data sources. |
| 2.3 | CHE concepts from Notebook 2.2. | 10–15 min | Uses values transcribed from cited literature; produces comparable idealized and literature free-energy diagrams. |
| 2.4 | Notebooks 2.1–2.3 or equivalent adsorption-free-energy knowledge. | 20–40 min after model download | Requires the UMA checkpoint; produces adsorption-energy data and annotated scaling-relation fits. |
| 2.5 | Notebook 2.4, limiting potentials, and adsorption-energy corrections. | 15–25 min | Downloads BEEF-vdW databases; produces a theoretical volcano, a corrected catalyst dataset, and uncertainty-aware points. |
| 2.6 | Notebooks 2.1, 2.4, and 2.5 or equivalent descriptor knowledge. | Potentially several hours | Requires UMA and writes one trajectory per alloy configuration; produces Pt₅₀Ni₅₀ and Pt₉₀Ni₁₀ OH binding-energy distributions. |
| 3.1 | ASE structures and constraints, MD ensembles, and NumPy. | 20–60 min | Requires a pretrained SpookyNet model and Pt–OH–H₂O input; produces an NVT trajectory and structural/species diagnostics. |
| 3.2 | Notebook 3.1 or familiarity with ASE MD and trajectories. | 15–40 min | Requires a Pt–water structure and MACE model; writes a trajectory, image frames, and an animated GIF. |
| 4.1 | Notebooks 2.1–2.6 and adsorption-energy, descriptor, and regression concepts. | Several hours; facet section at least 40 min | Requires UMA and selected structure files; produces six structure–property plots for OH adsorption. |
| 4.3 | ASE optimization and NEB concepts; GPAW, libxc, and GPAW datasets. | More than 13 h | Uses a solvated Pt slab and writes endpoint/NEB trajectories; produces a constant-potential path and activation-energy profile. |
| 4.4 | ORR free-energy diagrams, elementary rate laws, linear algebra, and electrochemical current conventions. | 10–20 min | No external data; produces interactive free-energy, coverage, kinetic-current, and RDE-current dashboards. |

### Troubleshooting

- Rerun prerequisite cells and inspect object types, array shapes, file paths, and the current working directory before changing a calculation.
- For atomistic models, check cell vectors, periodic boundaries, atom counts, vacuum, constraints, adsorption sites, and representative geometries.
- For energies and electrochemical diagrams, verify stoichiometry, units, energy zeros, molecular references, potential signs, electron counts, and adsorption-energy conventions.
- For regression and ensemble results, inspect structures before rejecting outliers; record random seeds, composition, reference slabs, and optimization status.
- For molecular dynamics, check model/device compatibility, numerical precision, timestep, initial overlaps, temperature history, neighbor cutoffs, and several trajectory frames.
- For SJM–NEB, verify the GPAW data path, endpoint potentials and forces, image continuity, and the compatibility of any reused electron-count guesses or restart files.
- For microkinetics, check rate dimensions, current sign, site-balance normalization, non-negative coverages, and exponential overflow.

## Reproducibility notes

- Several notebooks download external structures, databases, or pretrained model checkpoints. Record the source and version of these assets when using results in a publication.
- Long-running notebooks write trajectories and restartable intermediate files. Preserve these alongside the notebook if an exact calculation needs to be audited or continued.
- Executed outputs are illustrative. Hardware, dependency, and model-version differences may change timings and numerical details.
- The notebooks contain references and model-provenance notes specific to each workflow. Cite the original methods, datasets, and software when reusing a calculation.

## Repository contents

```text
.
├── README.md          Project overview and tutorial guide
├── environment.yml   Reproducible Conda environment
├── LICENSE           CC0 1.0 Universal dedication
└── *.ipynb           Fifteen tutorial notebooks
```

## Citation

No formal citation metadata is currently included. If these tutorials contribute to a research output, cite this repository together with the primary literature and software references given in the relevant notebook. A publication-specific DOI or citation can be added here when available.

## License

The repository is released under the [CC0 1.0 Universal](LICENSE) public-domain dedication. External datasets, pretrained models, and software retain their own licenses and terms of use.

## Feedback and contributions

Corrections and improvements are welcome through the repository's [issue tracker](https://github.com/doublelayer/ElectrocatalysisNotebooks/issues) or as pull requests. When reporting a computational problem, include the notebook name, failing cell, environment details, and the complete error message.
