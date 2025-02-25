## Matlab 绘图颜色设置

> [参考网址-mathworks_plot](https://ww2.mathworks.cn/help/matlab/ref/plot.html)

### 绘制颜色设置

```matlab
% 设置新的颜色矩阵可以替换原颜色矩阵
newColorOrder = [...];

% deepseek
ax = gca;  % 会弹出绘图窗口
colorOrder = ax.ColorOrder;  % 绘制时颜色的顺序
disp(colorOrder);  % 颜色矩阵
set(groot, 'defaultAxesColorOrder', newColorOrder)

% gpt-4o
defaultColors = get(groot, 'defaultAxesColorOrder');  % 默认绘制颜色顺序
disp(defaultColors)  % 默认颜色矩阵
ax.ColorOrder = newColorOrder;
```

1. [0, 0.4470, 0.7410] — 蓝色(默认) 
2. [0.8500, 0.3250, 0.0980] — 橙色
3. [0.9290, 0.6940, 0.1250] — 黄色
4. [0.4940, 0.1840, 0.5560] — 紫色
5. [0.4660, 0.6740, 0.1880] — 绿色
6. [0.3010, 0.7450, 0.9330] — 浅蓝色
7. [0.6350, 0.0780, 0.1840] — 红色