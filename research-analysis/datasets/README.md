# Datasets

> This guide lists the main public datasets for training, fine-tuning, and evaluating molecular ML models with Molfun, including download instructions and how each one connects to the library.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Datasets for Serious Fine-Tuning with Molfun

This guide lists the main public datasets for training, fine-tuning, and evaluating molecular ML models with Molfun, including download instructions and how each one connects to the library.

---

## Protein–Ligand Binding Affinity

The primary use case for Molfun fine-tuning: predict pKd/pKi/IC50 from 3D structure.

| Dataset | Size | Contents | Download | Molfun integration |
|---------|------|----------|----------|-------------------|
| **PDBbind v2020** | ~19K complexes (refined: 5,316) | 3D structures + experimental pKd/pKi/IC50 | [pdbbind.org.cn](http://www.pdbbind.org.cn) (free registration) | `AffinitySource.from_pdbbind_index()` + `PDBFetcher` |
| **BindingDB** | ~2.7M measurements | Experimental affinity, some with structure | [bindingdb.org](https://www.bindingdb.org/rwd/bind/index.jsp) → bulk TSV download | Parse TSV → `AffinitySource.from_csv()` |
| **ChEMBL 34** | ~2.4M compounds, 20M+ activities | Bioactivity, SMILES, targets | [ebi.ac.uk/chembl](https://www.ebi.ac.uk/chembl/) → FTP dump or API | SDF via `SDFParser`, labels via CSV |
| **ATOM3D LBA** | Pre-packaged task | Ligand binding affinity with controlled splits | [atom3d.ai](https://www.atom3d.ai) → `pip install atom3d` | `BenchmarkSuite.atom3d_lba()` |

### Quick start: PDBbind

```bash
# 1. Register at pdbbind.org.cn (free academic license)
# 2. Download PDBbind_v2020_refined.tar.gz
# 3. Extract — includes structures + INDEX_refined_data.2020

tar xzf PDBbind_v2020_refined.tar.gz -C data/pdbbind/
```

```python
from molfun.data.sources.affinity import AffinitySource

labels = AffinitySource.from_pdbbind_index("data/pdbbind/INDEX_refined_data.2020")
# Returns dict: {pdb_id: pKd_value}
```

---

## Structure Prediction / Folding

For training or evaluating structure prediction models.

| Dataset | Size | Contents | Download |
|---------|------|----------|----------|
| **Full PDB** | ~215K structures (~50 GB CIF) | All experimental structures depos

*[truncated — see source for full prompt]*