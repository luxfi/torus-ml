# Torus ML

Machine Learning framework for encrypted data using Fully Homomorphic Encryption.

## Overview

Torus ML enables training and inference on encrypted data without decryption. Part of the [Lux FHE ecosystem](https://github.com/luxfi/fhe).

## Features

- **Privacy-preserving ML**: Train models on encrypted data
- **Quantization-aware training**: Optimized for FHE computation
- **scikit-learn compatible**: Familiar API for ML practitioners
- **GPU acceleration**: native CUDA / Metal / WebGPU via the Torus compiler over the [luxfi/gpu](https://github.com/luxfi/gpu) runtime

## Installation

```bash
pip install torus-ml
```

Or from source:
```bash
git clone https://github.com/luxfi/torus-ml
cd torus-ml
pip install -e .
```

## Quick Start

```python
from torus.ml import FHEModelClient, FHEModelServer
from sklearn.datasets import make_classification

# Train a model
X, y = make_classification(n_samples=1000)
model = FHEModelClient()
model.fit(X, y)

# Compile for FHE
model.compile(X)

# Encrypted inference
encrypted_X = model.encrypt(X[:1])
encrypted_pred = model.predict(encrypted_X)
pred = model.decrypt(encrypted_pred)
```

## Integration

- [luxfi/fhe](https://github.com/luxfi/fhe) - Core FHE library (Go)
- [luxfi/torus](https://github.com/luxfi/torus) - Python FHE framework
- [luxfi/fhe-compiler](https://github.com/luxfi/fhe-compiler) - LLVM compiler
- [luxfi/lattice](https://github.com/luxfi/lattice) - Lattice primitives

## License

BSD 3-Clause Clear License

## Links

- [Lux Network](https://lux.network)
- [Documentation](https://docs.lux.network/fhe/ml)
