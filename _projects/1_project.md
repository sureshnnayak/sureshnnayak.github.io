---
layout: page
title: Product detection Using Neural networks
description: YOLOv5 trained on SKU110K
img: assets/img/shelf_product1_result.png
importance: 1
category: work
---

the detection of a product is a first step towards indentifying a product on the shelf. In this project I have trained YOLOv5 model on the SKU110K data set to creata a model that can identify all the products in the shelf  

The Sku110k dataset provides 11,762 images with more than 1.7 million annotated bounding boxes captured in densely packed scenarios.
DAta set: https://paperswithcode.com/dataset/sku110k


Results Obtained after training the model
Image 1:  
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/shelf_product1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/shelf_product1_result.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Object detection results obtained from passing images to YOLOv5 model.
</div>

Image 2:   
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/shelf_product1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/shelf_product1_result.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Object detection results obtained from passing images to YOLOv5 model.
</div>

These bounding boxex can be used to copare the desired product to obtain the location of desired product target



<!--
The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:
-->
