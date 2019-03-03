## R-CNN Problems..
- Slow Train
  - Wrapping..
  - Cropping..
  - Many Networks
    - Eject image feature
    - Classification
    - Predict Bounding box 
    
## Fast R-CNN
- Integration 3 separate networks into one

### STEPs..
1. initial RoI (Selective search)
2. passing Raw image to CNN
3. RoI Pooling(Pooling with strides...)
4. predict Position and classified Object

## Still Problem
- not fast enough
  - Selective search is running in CPU
  - bottleneck...
