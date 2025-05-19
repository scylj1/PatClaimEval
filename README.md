# PatClaimEval

This repository is for evaluation of patent claims compared to the gold claims. More updates are coming soon. 

## Example Usage

```python
from transformers import AutoModel, AutoTokenizer
import torch 

device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
tokenizer = AutoTokenizer.from_pretrained("lj408/PatClaimEval-Quality", trust_remote_code=True)
model = AutoModel.from_pretrained("lj408/PatClaimEval-Quality", trust_remote_code=True).to(device)
gold_claim = "1. A computer-implemented method comprising: identifying a primary code segment; ..."
candidate_claim = "1. A computer-implemented method for managing logger source code segments in a source code development platform, ..."
res = model.score_pair(gold_claim, candidate_claim , tokenizer, device)
print(res)
```

Note that this evaluation method can serve as a reference, but it may not be accurate in all cases. Users should rely on evaluations by patent professionals for more precise results.

## Citation

If you use this dataset or code, please cite our paper:

```
@article{jiang2025towards,
  title={Towards Better Evaluation for Generated Patent Claims},
  author={Jiang, Lekang and Scherz, Pascal A and Goetz, Stephan},
  journal={arXiv preprint arXiv:2505.11095},
  year={2025}
}
```

## License

This repository is under the Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0).