# Temporal AA
-------------
## Reprojection
``` View.ClipToPrevClip
ViewUniformShaderParameters.ClipToPrevClip = InvViewProj * PrevViewProj;
```
- 当前帧屏幕坐标（ScreenPos）通过viewproj矩阵，reproject到上一帧（history）的屏幕坐标，这针对静止模型或只有相机运动的情况
- Reprject在模型存在运动时就失效了（动画：位移、骨骼动画等），需要通过motion vector（velocity buffer）来判断是否存在模型的运动，如果存在就使用motion vector来采样历史帧的屏幕坐标
- motion vector可以
