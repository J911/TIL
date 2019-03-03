## problem
- Object detection
- Object Classification
- Object localization

## CNN ?
CNN alone is not easy.
- Too difficult to localization

## R-CNN
Region Proposals Convolution Neural Networks

### R-CNN STEPS
1. Detection Object box
2. Cropping Object Box and resize(wrap) to a normalized size
3. Passing CNN
4. Predict Position and classified Object


## Still Problem
- Slow Train
  - Wrapping..
  - Cropping..
  - Many Networks
    - Eject image feature
    - Classification
    - Predict Bounding box 
