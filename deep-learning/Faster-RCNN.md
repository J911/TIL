## Fast R-CNN Problem
- not fast enough
  - Selective search is running in CPU
  - bottleneck...
  
## Faster RCNN?
selective search is also performed by ConvNet.

### Steps...
1. passing image to the Conv layers -> build feature map
2. passing the featuremap to RPN(Region Proposal Network) -> classifiy and regress
3. After that, it is the same as Fast-RCNN

## RPN
Region Proposal Network
