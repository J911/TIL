# VISDOM with pytorch

install python modules
```bash
$ pip install --user visdom
$ pip install --user torchnet
```

```python
from torchnet.logger import VisdomPlotLogger, VisdomLogger

PORT = 19028
train_loss_logger = VisdomPlotLogger('line', port=PORT, opts={'title': 'Train Loss(cifar10-RMSProp)'})
test_loss_logger = VisdomPlotLogger('line', port=PORT, opts={'title': 'Test Loss(cifar10-RMSProp)'})



for epoch in range(start_epoch, start_epoch+50):
  # ...
  train_loss_logger.log(epoch, train_loss/(batch_idx+1))
  test_loss_logger.log(epoch, test_loss/(batch_idx+1))

```

run
```bash
$ python -m visdom.server -port 19028
```
