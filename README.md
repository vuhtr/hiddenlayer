# HiddenLayer

Install on Ubuntu and Debian:

```bash
sudo apt install graphviz
git clone https://github.com/vuhtr/hiddenlayer
cd hiddenlayer
pip install -e .
```

Usage:

```python
import torch
import torchvision.models
import hiddenlayer as hl

# VGG16 without classifier
model = torchvision.models.vgg16()
model.classifier = torch.nn.Sequential()

# Build HiddenLayer graph
graph = hl.build_graph(model, torch.zeros([1, 3, 224, 224]))
graph.theme = hl.graph.THEMES["blue"].copy() 
dot = graph.build_dot()
dot.attr("graph", rankdir="TD")
dot.render('vgg16', format='jpg')

from PIL import Image
Image.open('vgg16.jpg')
```