# SmartWasteAI: AI-Powered Smart Waste Management System

Final project for the Building AI course

## Summary

SmartWasteAI uses computer vision and machine learning to detect, sort, and analyze waste types from camera input to automate recycling and reduce landfill waste. This project supports smart city sustainability goals and encourages eco-friendly behavior.

## Background

Improper waste disposal and lack of recycling are major environmental problems in cities around the world. Landfills are overflowing, and recyclable materials often end up in the trash due to lack of awareness, poor infrastructure, or inconvenience.

My motivation for this project comes from witnessing poor waste management in my own community. I wanted to create a system that could make waste sorting easier and promote responsible recycling habits using the power of AI.

This idea addresses:

* The incorrect sorting of household or industrial waste  
* Low recycling rates due to poor accessibility or education  
* The need for smart, eco-conscious solutions in modern cities  

## How is it used?

SmartWasteAI is installed at waste collection points such as homes, offices, or recycling centers. A camera captures an image of the item to be discarded. The AI model then classifies the item (e.g., plastic, glass, organic, metal, paper) and lights up the correct bin for disposal.

**Users:**
* Citizens at public or private recycling bins  
* Municipal waste management departments  
* Smart city developers  

<img src="https://upload.wikimedia.org/wikipedia/commons/5/57/Waste_separation_bins.jpg" width="400">

## Data sources and AI methods

**Data Sources:**
* [TrashNet Dataset](https://github.com/garythung/trashnet) – labeled waste images  
* Custom images collected locally from waste sorting centers  

**AI Techniques:**
* Image classification using Convolutional Neural Networks (CNNs)  
* Transfer learning using pre-trained models (e.g., MobileNet, ResNet)  
* Real-time inference via TensorFlow Lite for embedded edge devices  

### Sample model training code:

```python
from tensorflow.keras.applications import MobileNetV2
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, GlobalAveragePooling2D

model = Sequential([
    MobileNetV2(include_top=False, input_shape=(224,224,3)),
    GlobalAveragePooling2D(),
    Dense(128, activation='relu'),
    Dense(5, activation='softmax')  # 5 classes: plastic, glass, metal, paper, organic
])
