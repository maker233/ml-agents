# Release notes

## 0.1.4
- Implemented fast Conv2DTrans. Useful for GAN type networks.
- Fixed few ComputeBuffer handling issues.
- Simplified way to pass texture via ``Tensor`` constructor.
- Documentation improvements.
- Added Unity Companion License as part of distribution.
- Fixed boundary checks for Compute Copy/Concat operations.
- Improved profiling experience, now each layer will be reported separately in Unity Profiler.
- Fixed Broadcast layer support in ``ModelAnalyzer``.
- Exp, Pow and other layers are now also implemented in Compute. Improves RL model inference performance on GPU.
- Added platform specific BLAS plugin support. Out of the box Barracuda ships with Apple Accelerate framework support for iOS and macOS.
- Added Burst BLAS plugin, greatly improves performance in Unity Editor where native OS BLAS is not available. It's packaged as separate package and requires to have Burst enabled.
- Improved memory handling, now less GC allocations should be made per inference execution.

## 0.1.3

- Improved Barracuda support for Unity Profiler.
- Cleaned up Barracuda APIs.
- Added direct ``Texture`` input support. Look for ``TextureAsTensorData``. The following types of texture supported as input: ``Texture2D``, ``Texture2DArray``, ``Texture3D``, ``RenderTexture``.
- Added ``Tensor`` to ``RenderTexture`` conversion. Look for ``TensorToRenderTexture``.
- Autoencoder type networks can run completely on GPU now. Data roundtrip via CPU is not necessary anymore.
- Vertical flip is applied when converting between ``Texture`` and ``Tensor`` to match conventionts. To override this behavior look for ``TextureAsTensorData.Flip`` enum.
- Removed direct reference to WebCamTexture, now Barracuda compiles for Console targets.
- Fixed _Conv2DTranspose_ layer support. Now GANs using _Conv2DTranspose_ work properly.
- Added automated test for pix2pix GAN.

## 0.1.2

- Barracuda now is also available as preview package. Look for ``com.unity.barracuda`` in https://staging-packages.unity.com registry.
- Conv2D layers are now *up to 30x faster* with ``CSharpFast`` backend (``ComputeFast`` remains best backend for convolutional networks).
- Added profiler sample for ``Fetch()``.
- Fixed compilation issues on Xbox One.
- TexConv2D support was temporary disabled.
- Barracuda logging now can be configured via static fields of ``Barracuda.D`` class, it allows both disable specific logging levels or just disable stack trace collection (helps with performance when profiling).
- Compute Concat implementation now will fall back to C# implementation instead of throwing exception when unsupported configuration is encountered. 
- Fixed several ``ComputeBuffer`` release issues. 
- Added constructor for ``Tensor`` that allows to pass in data array.
- Improved Flatten handling in TensorFlow models.
- Added helper func ``ModelLoader.LoadFromStreamingAssets``.
- Fixed .meta file packaging.
- Small docs improvements.
- Fixed unnecessary patching of Activation layers in ``ModelLoader``.
- Added output trimming at run-time. See for extra parameters Worker factory.

## 0.1.1
- First internal realease as drop-in package
- Compatibility with ML Agents models: 3DBall, PushBlock, GridWorld, Soccer.

## 0.1.0
- First internal build. Due some bugs encountered wasn't published.