# Notice

**This library is deprecated. It will not compile against current PyTorch and I have no intention to fix or support it.**

**For a long time, PyTorch (master) comes with its own implementation of the [CTC loss](https://pytorch.org/docs/master/nn.html#torch.nn.CTCLoss). 
  It has CuDNN support and fast CUDA and reasonably fast CPU backend.
  I recommend using that going forward.**

# warpctc module for PyTorch

*Thomas Viehmann <tv@lernapparat.de>*

This is a warpctc module for PyTorch.
It targets PyTorch 0.4+ and uses the C++ extension mechanism.

Warp-CTC was created by Baidu, see [the original
README](README.orig.md) and
[github project](https://github.com/baidu-research/warp-ctc).

**Very important: please do use the same compiler as PyTorch (gcc-5
seems to be a good choice for Linux), or you will see segfaults.** 

The idea is to

```
cd pytorch_bindings
python3 setup.py bdist_wheel
```
and install the wheel in `pytorch_bindings/dist`. Remember to set the
compiler as you do to compile PyTorch.
You can test with
```
python3 tests/test.py -v
```


Note that this is not the same as [Sean Naren's great Warp-CTC PyTorch
wrapper](https://github.com/SeanNaren/warp-ctc), which is the most
popular binding for CTC Loss I am aware of.
I have tried to make the bindings look as PyTorch-y as possible in terms
of interface, have checks on all tensor sizes, and also to stay close to
the modern way of doing things in the internals by using ATen. (Sean
created his set of bindings when PyTorch was in a much earlier stage.)
