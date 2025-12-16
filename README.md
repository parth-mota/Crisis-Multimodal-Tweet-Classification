# Crisis Multimodal Classification System 🚨

Deep learning pipeline for real-time crisis tweet classification and humanitarian content categorization using BERT and multimodal fusion.

## 🎯 Performance

| Model | Task | Macro F1 | Accuracy | Status |
|-------|------|----------|----------|--------|
| **Text Classifier** | Informative vs Non-informative | **71.4%** | 73.9% | ✅ Production-ready |
| **Multimodal** | 7 Humanitarian Categories | **37.7%** | 46.4% | 🔬 Research prototype |

*Outperforms CrisisMMD baseline (65.3% → 71.4%) on informative classification*

##  Architecture

### Text Classifier
- **Encoder**: BERT-base-uncased (110M params)
- **Loss**: Class-weighted Cross-Entropy
- **Training**: 3 epochs, 12K samples, AdamW optimizer

### Multimodal Classifier
- **Text Encoder**: BERT-base-uncased
- **Image Encoder**: EfficientNet-B0 (5M params)
- **Fusion**: Cross-modal attention mechanism
- **Loss**: Focal Loss (γ=3.0) for extreme imbalance handling
- **Training**: 6 epochs, mixed precision (FP16)

## 📈 Detailed Results

### Text Classifier
- **Informative tweets**: 79.8% F1 (83.3% recall, 76.5% precision)
- **Non-informative**: 63.1% F1 (58.6% recall, 68.4% precision)
- Only 207/1237 critical tweets missed (16.7%)

### Multimodal Classifier (Per Category)
- **Vehicle damage**: 53.0% F1 (72.1% recall)
- **Rescue/volunteering**: 51.9% F1 (57.3% recall)
- **Injured/dead people**: 47.9% F1 (59.0% recall)
- **Missing/found people**: 47.0% F1 (79.6% precision)
- **Infrastructure damage**: 37.4% F1

## 🛠️ Key Features

✅ **Cross-modal attention** for text-image fusion  
✅ **Focal loss** handles 1:118 class imbalance  
✅ **Rare class filtering** (< 50 samples removed)  
✅ **Mixed precision training** (2x speedup on GPU)  
✅ **Data augmentation** (rotation, jitter, color, erasing)  
✅ **Comprehensive metrics** (confusion matrices, per-class F1)

## 🤝 Use Cases

- 🚨 **Real-time crisis tweet filtering** - Reduce noise by 70% for emergency responders
- 🏥 **Humanitarian triage** - Categorize content for resource allocation
- 🔍 **Damage assessment** - Extract infrastructure damage reports from social media
- 📍 **Missing person identification** - High precision (80%) on missing person posts
- 🚁 **Rescue coordination** - Detect rescue/volunteering requests (52% F1)
