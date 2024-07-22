## Overview

Welcome to **imaged SDK**, a powerful and versatile vision and nlp AI SDK. This repository contains the public binaries, documentation, and issue tracker for the SDK. 

## Features

- **NSFW Detection**: Detect and score potentially NSFW content in images.
- **Image Colorization**: Convert grayscale images to color.
- **Image Restoration**: Remove noise and restore details in images.
- **Image Upscaling**: Increase the resolution of images using advanced upscaling techniques.
- **Background Removal**: Remove backgrounds from images for better object isolation.
- **Object Detection and Segmentation**: Detect and segment objects in images using YOLO models.

## Getting Started

### Download and Extract

1. **Download the latest release**
2. **Extract the contents** to your desired directory.

### Include Headers

Include the necessary headers in your project:

```cpp
#include "imaged_sdk/include/sdk.hpp"
```

### Link Libraries

Link against the static or dynamic libraries provided in the `lib` directory:

- `libsdk.dylib` (Dynamic Library)
- `libsdk.a` (Static Library)
- `libonnxruntime.dylib` (ONNX Runtime Library)

### Examples

Refer to the examples below to get started with using the SDK.

#### NSFW Detection

```cpp
imaged::SDK::AI ai;
ai.loadModel(imaged::SDK::ModelType::nsfw);
imaged::SDK::Image image;
image.load("path_to_image.jpg");
auto response = ai.isNSFW(image);
std::cout << "NSFW score: " << response.score << std::endl;
```

#### Image Colorization

```cpp
ai.loadModel(imaged::SDK::ModelType::colorizer);
image.load("path_to_grayscale_image.jpg");
ai.colorize(image);
image.save("colorized_image.jpg");
```

#### Image Restoration

```cpp
ai.loadModel(imaged::SDK::ModelType::restore);
image.load("path_to_noisy_image.png");
ai.restore(image);
image.save("restored_image.png");
```

#### Image Upscaling

```cpp
ai.loadModel(imaged::SDK::ModelType::upscale);
image.load("path_to_low_res_image.png");
ai.upscale(image);
image.save("upscaled_image.png");
```

#### Background Removal

```cpp
ai.loadModel(imaged::SDK::ModelType::rembg);
image.load("path_to_image.jpg");
ai.removeBackground(image);
image.save("image_without_background.png");
```

#### Object Detection and Segmentation

```cpp
ai.loadModel(imaged::SDK::ModelType::yolov8);
image.load("path_to_image.jpg");
auto response = ai.yolov8(image);
for (const auto &obj : response.objects) {
    std::cout << "Detected object: " << obj.label << " with score " << obj.score << std::endl;
}
```

## Documentation

Comprehensive documentation is available in the `wiki` tag. It includes detailed guides, API references, and tutorials to help you make the most out of the imaged_sdk.

## Issue Tracker

If you encounter any issues, please report them through the [Issue Tracker](#). We appreciate your feedback and will work to address any problems as quickly as possible.

---

Thank you for using **imaged_sdk v0.9**. We hope it enhances your image processing tasks and look forward to your feedback.
