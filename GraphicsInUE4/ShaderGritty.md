# UE4 Shader Gritty

## 颜色空间
- YCoCg
YCoCg，亮度Y，色度绿色Cg和色度橙色Co。

[![rgb2ycocg](https://wikimedia.org/api/rest_v1/media/math/render/svg/5b57fdade4b8c6891ef7aef7b7d7041e7477a70b)](https://en.wikipedia.org/wiki/YCoCg)

![rgb2ycocg](./ShaderGritty/rgb2ycocg.png）

在RGB到YCoCg实现中，UE4中有多份实现，差别主要在于参数的处理，比如Private\TemporalAA\TAAStandalone.usf中的实现，参数做了4倍处理。
```
float3 RGBToYCoCg( float3 RGB )
{
	float Y = dot( RGB, float3( 1, 2, 1 ) );
	float Co = dot( RGB, float3( 2, 0, -2 ) );
	float Cg = dot( RGB, float3( -1, 2, -1 ) );
	float3 YCoCg = float3( Y, Co, Cg );
	return YCoCg;
}
```