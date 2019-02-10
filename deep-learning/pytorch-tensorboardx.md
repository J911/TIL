pip install

```bash
$ pip install tensorboard
$ pip install tensorboardX
```

code 

```python

from tensorboardX import SummaryWriter
writer = SummaryWriter('log_dir/'+time.strftime('%Y%m%d_%H%M%S_ResNet18'))


# ...
writer.add_scalar('train acc', 100.*correct/total,epoch)
writer.add_scalar('train loss', 100. * loss, epoch)
writer.add_scalar('test acc', 100. * correct / total,epoch)
writer.add_scalar('test loss',test_loss,epoch)

# ...
```


run

```
tensorboard --port 7561 --logdir=./log_dir
```
