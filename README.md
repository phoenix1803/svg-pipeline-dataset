# Extreme Lossy SVG Compression for Bandwidth-Critical Applications

**Trading Visual Fidelity for 99% Size Reduction in AI-Generated Content**

A specialized compression pipeline designed for scenarios where extreme bandwidth constraints outweigh visual quality requirements, achieving unprecedented 99.01% compression ratios while acknowledging significant quality degradation.

## Overview

This repository contains the implementation of an extreme lossy compression pipeline for scalable vector graphics (SVG) that prioritizes file size reduction over visual fidelity. The method reduces AI-generated images from an average of 287KB to 1.88KB while maintaining basic structural recognizability.

**Critical Warning**: This method produces severely degraded output unsuitable for most conventional applications. It is specifically designed for bandwidth-critical scenarios where extreme compression justifies quality loss.

## Key Features

- **Extreme Compression**: Achieves 99.01% ± 1.04% size reduction
- **Five-Stage Pipeline**: Preprocessing, color quantization, contour extraction, vectorization, and optimization
- **Perceptual Optimization**: Uses CIEDE2000 color distance metrics for intelligent color reduction
- **Budget Management**: Strict file size constraints with adaptive simplification
- **Production Ready**: Demonstrated feasibility for specialized deployment scenarios

## Performance Metrics

| Metric | Value | Interpretation |
|--------|-------|----------------|
| Compression Ratio | 99.01% ± 1.04% | Extreme size reduction achieved |
| SSIM | 0.233 ± 0.074 | Severe structural degradation |
| CIEDE2000 | 30.9 ± 3.0 | Major color distortion |
| LPIPS | 0.624 ± 0.054 | Significant perceptual dissimilarity |
| Processing Time | 2.5 minutes | Per 384×384 pixel image |

## Repository Structure

```
├── results/
│   ├── original_images/          # Original AI-generated images from Stable Diffusion v2
│   ├── ref_images/               # Reference SVGs converted using SVGcode web tool
│   └── svg_images/               # Compressed SVGs from our pipeline
├── results-compiled.csv          # Comprehensive metrics for all test images
├── main.zip                      # Complete dataset archive
└── README.md                     # This file
```

## Dataset

- **Source**: 273 AI-generated images from Kaggle "Drawing with LLMs" competition
- **Categories**: Abstract/Geometric (68), Natural Scenes (71), Character/Portrait (67), Technical/Architectural (67)
- **Format**: Original images generated using Stable Diffusion v2
- **Size Range**: Average 287KB ± 172.6KB input size

## Implementation Links

### Code Repository
- **Main Pipeline**: [Kaggle Notebook - SVG Pipeline](https://www.kaggle.com/code/prakhar1803/svg-pipeline-main)
- **Evaluation Metrics**: [Kaggle Notebook - Comparison Metrics](https://www.kaggle.com/code/ryantwt/comparison)

### Reference Tools
- **SVGcode**: Web-based SVG conversion tool used for reference comparisons
- **Stable Diffusion v2**: Image generation model for dataset creation

## Methodology

### Five-Stage Compression Pipeline

1. **Input Preprocessing**: Content analysis and bilateral filtering
2. **Perceptual Color Quantization**: CIEDE2000-based aggressive palette reduction
3. **Hierarchical Contour Extraction**: Multi-scale feature importance ranking
4. **Adaptive Vectorization**: Budget-constrained polygon simplification using Douglas-Peucker algorithm
5. **Size Optimization**: Coordinate precision reduction and markup minimization

### Key Algorithms

- **Color Distance**: CIEDE2000 perceptual color difference calculation
- **Importance Scoring**: Multi-factor geometric feature ranking
- **Budget Management**: Dynamic epsilon adjustment for size constraints
- **Polygon Simplification**: Adaptive Douglas-Peucker with pressure-based parameters

## Appropriate Use Cases

### Suitable Applications
- IoT and edge computing devices with severe bandwidth constraints
- Emergency communication systems with limited network capacity
- Content preview and thumbnail systems
- Batch processing environments prioritizing storage costs
- Archival systems for AI-generated content

### Inappropriate Applications
- Medical imaging or diagnostic applications
- Professional graphic design or print media
- Scientific visualization requiring accuracy
- E-commerce product images
- Any application requiring color accuracy or fine detail preservation

## Quality Assessment

This method operates well beyond conventional quality thresholds:

- **SSIM < 0.5**: Indicates severe structural degradation
- **CIEDE2000 > 10**: Represents perceptually significant color differences
- **Visual Artifacts**: Severe color quantization, loss of fine details, simplified geometry

## Technical Requirements

- **Processing Time**: 2.5 minutes average for 384×384 images
- **Memory Usage**: ~50MB for 1024×1024 images
- **Dependencies**: OpenCV 4.7, scikit-image 0.19, colormath 3.0
- **Computational Complexity**: O(n log n) where n = pixel count

## Results Data

The `results-compiled.csv` file contains comprehensive evaluation metrics for all 273 test images:

- **Compression Performance**: Original size, compressed size, compression ratio
- **Quality Metrics**: SSIM, CIEDE2000, LPIPS scores
- **Geometric Analysis**: Path count reduction, complexity measures
- **Category Breakdown**: Performance by content type
- **Statistical Analysis**: Confidence intervals and effect sizes

## Limitations and Warnings

### Technical Limitations
- Single-threaded implementation limits throughput
- Linear memory scaling with input size
- 2.5-minute processing time unsuitable for real-time applications

### Quality Limitations
- Severe visual degradation for most use cases
- Significant color accuracy loss
- Failure with fine detail preservation requirements
- Content type sensitivity beyond AI-generated imagery

## Citation

If you use this work in your research, please cite:

```bibtex
@article{chandra2025extreme,
  title={Extreme Lossy SVG Compression for Bandwidth-Critical Applications: Trading Visual Fidelity for 99\% Size Reduction in AI-Generated Content},
  author={Chandra, Prakhar and Kapur, Pulkit and Kohli, Jaspreet Singh},
  journal={Submitted for Publication},
  year={2025},
  institution={Maharaja Surajmal Institute of Technology, New Delhi, India}
}
```

## License

This project is released under the MIT License. See LICENSE file for details.

## Contact

- **Prakhar Chandra**: prakharchandra1803@gmail.com
- **Pulkit Kapur**: pulkitkapur100@gmail.com  
- **Jaspreet Singh Kohli**: jaspreet.jsk.kohli@gmail.com

**Institution**: Maharaja Surajmal Institute of Technology, New Delhi, India

## Acknowledgments

We thank the Kaggle "Drawing with LLMs" competition organizers for providing the motivation that inspired this work. We acknowledge the computational resources provided by our institution and valuable feedback from the computer graphics research community.

---

**Disclaimer**: This method is designed for specialized applications where extreme compression justifies quality loss. Users must carefully evaluate whether the trade-offs are acceptable for their specific use case.
