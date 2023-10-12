## Quick demo

- Install **[PyTorch](https://pytorch.org)** and Python >= 3.7.3 and run `sh requirements.sh`. You should slightly change `torchgeometry` kernel code following [here](https://github.com/mks0601/I2L-MeshNet_RELEASE/issues/6#issuecomment-675152527).
- Download the pre-trained I2L-MeshNet from [here](https://drive.google.com/file/d/14qAoFev6Rp_QY27f3cTztmIWTi7MVsnO/view?usp=sharing). This is not the [best accurate I2L-MeshNet](https://drive.google.com/file/d/1Ov6eYbBsgtmnrquo7l1plAT_gW7Gs0Ki/view?usp=sharing), but provides visually smooth meshes. [Here](https://github.com/mks0601/I2L-MeshNet_RELEASE#i2l-meshnet-for-mesh-visualization) is discussion about this.
- Prepare `input.jpg` and pre-trained snapshot at `demo` folder.
- Download `basicModel_f_lbs_10_207_0_v1.0.0.pkl` and `basicModel_m_lbs_10_207_0_v1.0.0.pkl` from [here](https://smpl.is.tue.mpg.de/) and `basicModel_neutral_lbs_10_207_0_v1.0.0.pkl` from [here](http://smplify.is.tue.mpg.de/). Place them at `common/utils/smplpytorch/smplpytorch/native/models`.
- Go to `demo` folder and edit `bbox` in [here](https://github.com/mks0601/I2L-MeshNet_RELEASE/blob/561fac8a74ae8bdc0429edc15e5dc4c47fda11bf/demo/demo.py#L83).
- run `python demo.py --gpu 0 --stage param --test_epoch 8` if you want to run on gpu 0.
- You can see `output_mesh_lixel.jpg`, `output_mesh_param.jpg`, `rendered_mesh_lixel.jpg`, `rendered_mesh_param.jpg`, `output_mesh_lixel.obj`, and `output_mesh_param.obj`. `*_lixel.*` are from lixel-based 1D heatmap of mesh vertices and `*_param.*` are from regressed SMPL parameters.
- If you run this code in ssh environment without display device, do follow:

```
1、Install oemesa follow https://pyrender.readthedocs.io/en/latest/install/
2、Reinstall the specific pyopengl fork: https://github.com/mmatl/pyopengl
3、Set opengl's backend to egl or osmesa via os.environ["PYOPENGL_PLATFORM"] = "egl"
```
