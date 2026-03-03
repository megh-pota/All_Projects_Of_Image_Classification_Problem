# 📌 Project: CIFAR-10 Image Classification with Transfer Learning

## 🎯 Objective

Evaluate CNN architectures on CIFAR-10 and compare:

- Baseline CNN  
- Transfer Learning using MobileNetV2  

The goal of this project was not just to improve accuracy, but to understand:

- Feature learning
- Generalization behavior
- Robustness to transformations
- Fine-tuning strategies
- Model selection based on evidence

---

## 🧠 Key Insights

- Baseline CNN achieved ~75% validation accuracy  
- MobileNetV2 (frozen backbone) achieved ~81%  
- Fine-tuning the last 60 layers improved performance to **85%**  
- Transfer learning significantly improved generalization and training stability  
- Robustness to noise and geometric transformations increased  
- Fine-tuning depth had measurable impact on final performance  

---

## 🏆 Final Model

**Backbone:** MobileNetV2 (ImageNet pretrained)  
**Fine-Tuned Layers:** Last 60 layers  
**Validation Accuracy:** 85%  

The final selected model demonstrated the best balance between:

- Performance
- Stability
- Generalization
- Practical deployment feasibility

---

## 📊 Why This Model Won

- Better feature reuse from pretrained ImageNet representations  
- Lower overfitting compared to custom CNN  
- Improved robustness under augmentation  
- More stable optimization dynamics  
- Stronger confidence calibration  

---

## 🎯 Final Project Strategy & Model Selection

For this project, I intentionally uploaded only two models:

- A Baseline CNN  
- The Final Winning Model (MobileNetV2 – Fine-Tuned)

This was a deliberate engineering decision.

Instead of uploading multiple experimental models, I focused on structured comparison and clear model selection. The goal was not to stack architectures randomly, but to:

✔ Establish a baseline performance benchmark  
✔ Evaluate improvement through transfer learning  
✔ Test fine-tuning depth strategies  
✔ Analyze generalization and robustness  
✔ Select the best-performing model based on measurable evidence  

The baseline CNN served as a controlled reference point.

The final winning model — MobileNetV2 (ImageNet pretrained, last 60 layers fine-tuned) — achieved **85% validation accuracy** and demonstrated:

- Stronger generalization  
- Better robustness  
- Reduced overfitting  
- More stable training behavior  

This approach reflects how real-world ML systems are built:

Not by stacking models blindly, but by testing, evaluating, and selecting based on measurable performance and trade-offs.

---

# 💼 LinkedIn Post Version

🚀 **Vision Project — CIFAR-10 Transfer Learning**

I built an end-to-end image classification pipeline comparing:

• Baseline CNN  
• Data Augmentation  
• Transfer Learning (MobileNetV2)  
• Fine-tuning strategies  

After structured experiments, fine-tuning the last 60 layers of MobileNetV2 achieved **85% validation accuracy**, outperforming the baseline CNN by ~10%.

Key takeaways:

✔ Transfer learning significantly improves generalization  
✔ Fine-tuning depth matters  
✔ Robustness > raw training accuracy  
✔ Pretrained features reduce overfitting  

This project strengthened my understanding of feature reuse, calibration, and robustness in computer vision systems.
