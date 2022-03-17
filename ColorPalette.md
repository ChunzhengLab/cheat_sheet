## 4 colors

```C++
  int ci[4];
  TColor* color[4];
  ci[0] = TColor::GetFreeColorIndex();
  color[0] = new TColor(ci[0],   0/255.,  24/255., 113/255.);//dark blue
  ci[1] = TColor::GetFreeColorIndex();
  color[1] = new TColor(ci[1], 255/255.,  88/255.,  93/255.);//red
  ci[2] = TColor::GetFreeColorIndex();
  color[2] = new TColor(ci[2], 255/255., 181/255.,  73/255.);//yellow
  ci[3] = TColor::GetFreeColorIndex();
  color[3] = new TColor(ci[3], 65/255.,  182/255., 230/255.);//light blue
```

## 5 colors
```C++
  int ci[5];
  TColor* color[5];
  ci[0] = TColor::GetFreeColorIndex();
  color[0] = new TColor(ci[0],  24/255.,  63/255.,  94/255.);//深蓝
  ci[1] = TColor::GetFreeColorIndex();
  color[1] = new TColor(ci[1],  33/255.,  99/255., 154/255.);//浅蓝
  ci[2] = TColor::GetFreeColorIndex();
  color[2] = new TColor(ci[2], 246/255., 213/255., 101/255.);//黄
  ci[3] = TColor::GetFreeColorIndex();
  color[3] = new TColor(ci[3],  62/255., 174/255., 164/255.);//绿
  ci[4] = TColor::GetFreeColorIndex();
  color[4] = new TColor(ci[4], 236/255.,  85/255.,  60/255.);//红
```
  
## 6 colors
```C++
  int ci[6];
  TColor* color[6];
  ci[0] = TColor::GetFreeColorIndex();
  color[0] = new TColor(ci[0],  240/255.,  102/255.,   70/255.);//红
  ci[1] = TColor::GetFreeColorIndex();
  color[1] = new TColor(ci[1],   79/255.,  194/255.,  216/255.);//蓝
  ci[2] = TColor::GetFreeColorIndex();
  color[2] = new TColor(ci[2],  254/255.,  198/255.,  101/255.);//黄
  ci[3] = TColor::GetFreeColorIndex();
  color[3] = new TColor(ci[3],  146/255.,  100/255.,  140/255.);//紫
  ci[4] = TColor::GetFreeColorIndex();
  color[4] = new TColor(ci[4],  125/255.,  200/255.,  165/255.);//绿
  ci[5] = TColor::GetFreeColorIndex();
  color[5] = new TColor(ci[5],   64/255.,   64/255.,   64/255.);//黑
```
