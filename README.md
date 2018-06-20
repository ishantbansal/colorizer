
## Dependencies

- [Torch7](http://torch.ch/docs/getting-started.html)
- [nn](https://github.com/torch/nn)
- [image](https://github.com/torch/image)
- [nngraph](https://github.com/torch/nngraph)

All packages should be part of a standard Torch7 install. For information on how to install Torch7 please see the [official torch documentation](http://torch.ch/docs/getting-started.html) on the subject.

## Usage

First, download the colorization model by running the download script:

```
./download_model.sh
```

Basic usage is:

```
th colorize.lua <input_image> [<output_image>]
```

For example:

```
th colorize.lua ansel_colorado_1941.png out.png
```

### Best Performance

- This model was trained on the [Places dataset](http://places.csail.mit.edu/) and thus best performance is for natural outdoor images.
- While the model works on any size image, we trained it on 224x224 pixel images and thus it works best on small images. Note that you can process a small imageto obtain the chrominance map and then rescale it and combine it with the original grayscale image for higher quality.
- Larger image sizes can give uneven colorings (limited by spatial support of the network).

### ImageNet Model
We also provide the colorization model that was trained on [ImageNet](http://image-net.org/challenges/LSVRC/2012/index). This model can be used for comparisons with other colorization models trained on ImageNet. We recommend using the places colorization model for general purposes.

For using the ImageNet model, download the model by running:

```
./download_model_imagenet.sh
```

Usage is:

```
th colorize.lua <input_image> <output_image> colornet_imagenet.t7
```

### Notes

- This is developed on a linux machine running Ubuntu 14.04 during late 2015.
- The provided code does not use GPU accelerated (trivial to change).
- Please note that the model is slow on large images (over 512x512 pixels) and may run out of memory. Demo should take around 2 GiB of peak RAM memory, system with 4 GiB or more of RAM is recommended.
- Provided model and sample code is under a non-commercial creative commons license.



