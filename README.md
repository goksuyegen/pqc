# PQC Benchmark Lab

## Overview

PQC Benchmark Lab is an experimental research project for benchmarking post-quantum cryptography algorithms against classical cryptographic methods.

The goal of the project is to compare computational performance, key sizes, ciphertext sizes, and communication overhead between classical cryptographic algorithms and post-quantum alternatives.

This project is designed as a small R&D-style lab, combining cybersecurity, mathematics, software development, and experimental evaluation.

## Research Question

How do post-quantum cryptographic algorithms compare with classical cryptographic algorithms in terms of runtime performance, key size, ciphertext/signature size, and practical communication overhead?

## Project Goals

The main goals of this project are:

* Implement a small benchmarking framework for cryptographic algorithms.
* Compare classical and post-quantum key exchange mechanisms.
* Measure key generation, encapsulation, decapsulation, signing, and verification times.
* Analyze public key, secret key, ciphertext, and signature sizes.
* Export benchmark results to CSV files.
* Visualize performance and size trade-offs using plots.
* Write a short R&D-style report based on the experimental results.

## Background

Post-quantum cryptography focuses on cryptographic algorithms that are designed to remain secure against attacks from large-scale quantum computers.

Classical public-key algorithms such as RSA and elliptic-curve cryptography are widely used today, but they are vulnerable in principle to quantum algorithms such as Shor's algorithm. Post-quantum cryptographic schemes are based on different mathematical problems, such as lattice-based cryptography and hash-based signatures.

This project does not aim to create new cryptographic algorithms. Instead, it focuses on experimentally evaluating existing algorithms and comparing their practical trade-offs.

## Initial Scope

The first version of the project focuses on key exchange and key encapsulation mechanisms.

Planned comparison:

| Category           | Classical Algorithm | Post-Quantum Algorithm |
| ------------------ | ------------------- | ---------------------- |
| Key Exchange / KEM | X25519 or ECDH      | ML-KEM-512             |
| Key Exchange / KEM | X25519 or ECDH      | ML-KEM-768             |
| Key Exchange / KEM | X25519 or ECDH      | ML-KEM-1024            |

Later versions may include digital signature algorithms.

Planned future comparison:

| Category          | Classical Algorithm | Post-Quantum Algorithm |
| ----------------- | ------------------- | ---------------------- |
| Digital Signature | Ed25519             | ML-DSA                 |
| Digital Signature | RSA-PSS             | ML-DSA                 |
| Digital Signature | RSA-PSS             | SLH-DSA                |

## Metrics

The project will measure the following metrics:

### Key Exchange / KEM Metrics

| Metric              | Description                                              |
| ------------------- | -------------------------------------------------------- |
| Key generation time | Time required to generate a public/secret key pair       |
| Encapsulation time  | Time required to generate a shared secret and ciphertext |
| Decapsulation time  | Time required to recover the shared secret               |
| Public key size     | Size of the public key in bytes                          |
| Secret key size     | Size of the secret key in bytes                          |
| Ciphertext size     | Size of the exchanged ciphertext in bytes                |

### Signature Metrics

| Metric              | Description                                             |
| ------------------- | ------------------------------------------------------- |
| Key generation time | Time required to generate signing and verification keys |
| Signing time        | Time required to generate a signature                   |
| Verification time   | Time required to verify a signature                     |
| Public key size     | Size of the verification key in bytes                   |
| Secret key size     | Size of the signing key in bytes                        |
| Signature size      | Size of the generated signature in bytes                |

## Methodology

Each algorithm will be benchmarked over multiple iterations to reduce the effect of random variation.

For each algorithm:

1. Generate keys.
2. Run the cryptographic operation many times.
3. Measure execution time.
4. Record output sizes.
5. Compute statistical summaries.
6. Export results.
7. Compare algorithms using tables and plots.

Example statistical values:

* Mean runtime
* Standard deviation
* Minimum runtime
* Maximum runtime
* Median runtime

## Example Result Format

```csv
algorithm,operation,iterations,mean_ms,std_ms,min_ms,max_ms,public_key_bytes,secret_key_bytes,ciphertext_bytes
ML-KEM-512,keygen,1000,TBD,TBD,TBD,TBD,TBD,TBD,TBD
ML-KEM-512,encapsulation,1000,TBD,TBD,TBD,TBD,TBD,TBD,TBD
ML-KEM-512,decapsulation,1000,TBD,TBD,TBD,TBD,TBD,TBD,TBD
X25519,key_exchange,1000,TBD,TBD,TBD,TBD,TBD,TBD,TBD
```

## Starting Folder Structure

```text
pqc-benchmark-lab/
├── benchmarks/
│   ├── bench_kem.py
│   ├── bench_signatures.py
│   └── utils.py
├── results/
│   ├── kem_results.csv
│   └── signature_results.csv
├── plots/
├── report/
│   └── report.md
├── README.md
└── requirements.txt
```

## Planned Files

### `benchmarks/bench_kem.py`

Benchmark key exchange and key encapsulation mechanisms.

Planned operations:

* Key generation
* Encapsulation
* Decapsulation
* Shared secret comparison
* Size measurement

### `benchmarks/bench_signatures.py`

Benchmark digital signature algorithms.

Planned operations:

* Key generation
* Signing
* Verification
* Signature size measurement

### `benchmarks/utils.py`

Shared helper functions.

Planned utilities:

* Timer function
* CSV export
* Statistical calculation
* Byte-size measurement
* Result formatting

### `results/`

Stores raw experimental results in CSV format.

### `plots/`

Stores generated plots comparing runtime and size overhead.

### `report/report.md`

Contains the final R&D-style analysis.

## Example Research Hypothesis

Post-quantum algorithms are expected to introduce larger public keys, secret keys, ciphertexts, or signatures than many classical algorithms, but their runtime may still be practical for common client-server use cases.

## Expected Output

The final project should produce:

1. A working benchmark framework.
2. Runtime comparison tables.
3. Key and ciphertext size comparison tables.
4. CSV result files.
5. Performance plots.
6. A short research report discussing results and limitations.

## Possible Extensions

Future versions may include:

* Hybrid classical + post-quantum key exchange.
* TLS-style handshake simulation.
* Signature algorithm benchmarking.
* Memory usage measurement.
* Crypto-agility configuration system.
* Comparison across different machines or operating systems.

## Example Hybrid Key Exchange Idea

A future extension could combine a classical shared secret and a post-quantum shared secret:

```text
hybrid_secret = Hash(classical_secret || post_quantum_secret)
```

This can simulate a transition-period design where both classical and post-quantum security assumptions are used together.

## Limitations

This project is an educational and experimental benchmark. It does not provide a complete cryptographic security analysis.

The results may depend on:

* Hardware
* Operating system
* Python version
* Cryptographic library implementation
* Number of benchmark iterations
* Background system load

## Disclaimer

This project is for educational and research purposes only. It does not implement new cryptographic algorithms and should not be used as a production cryptographic system without expert review.
