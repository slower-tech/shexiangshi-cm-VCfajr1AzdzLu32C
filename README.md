
在数据可视化中，图例（legend）是一个非常重要的元素，它能够帮助读者理解图表中不同元素的含义。特别是在使用Python进行可视化时，matplotlib库是一个非常强大的工具，能够轻松创建包含多个子图的图表，并在每个子图中显示图例。本文将详细介绍如何在Python的matplotlib库中为所有子图显示标签legend，包括理论概述和详细的代码示例。


#### 一、理论概述


1\.图例（Legend）的作用


* 图例用来解释绘图中各种元素的符号，帮助观众理解每种线条、颜色或符号代表的数据。例如，在一个折线图中，通过图例可以清晰地了解到每一条线代表的是哪个数据集。


2\.matplotlib中的legend函数


* `matplotlib.pyplot.legend(*args, **kwargs)`：用于创建图例。
* `loc`参数：设置图例的位置，如`'upper right'`、`'lower left'`等。
* `fontsize`参数：设置图例的字体大小。
* `frameon`参数：设置是否显示图例边框。
* `edgecolor`和`facecolor`参数：分别设置图例边框和背景的颜色。
* `title`参数：设置图例的标题。


3\.在多个子图中显示图例


* 使用`plt.subplots()`方法创建包含多个子图的图表。
* 每个子图可以单独调用`legend()`方法显示图例。
* 也可以使用`fig.legend()`方法在整个图形上方添加一个全局图例。


#### 二、代码示例


以下是一个详细的代码示例，展示了如何在多个子图中显示图例。



```
import matplotlib.pyplot as plt
import numpy as np
 
# 生成数据
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)
 
# 创建包含两个子图的图表
fig, axs = plt.subplots(2)
 
# 在第一个子图中绘制 sin(x)
axs[0].plot(x, y1, label='sin(x)', color='blue')
axs[0].set_title('Sine Function')
axs[0].legend()  # 添加图例
 
# 在第二个子图中绘制 cos(x)
axs[1].plot(x, y2, label='cos(x)', color='orange')
axs[1].set_title('Cosine Function')
axs[1].legend()  # 添加图例
 
# 调整布局
plt.tight_layout()
plt.show()

```

在上述代码中，我们创建了一个包含两个子图的图表，每个子图都有自己的图例。通过`label`参数为每个数据系列指定标签，并在每个子图中调用`legend()`方法显示图例。


![](https://img2024.cnblogs.com/blog/3448692/202412/3448692-20241220212255825-1793616901.png)


#### 三、全局图例的显示


如果你想在整个图形上方添加一个全局图例，可以使用`fig.legend()`方法。以下是一个示例：



```
import matplotlib.pyplot as plt
import numpy as np
 
# 生成数据
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)
 
# 创建包含两个子图的图表
fig, axs = plt.subplots(2)
 
# 在第一个子图中绘制 sin(x)
axs[0].plot(x, y1, label='sin(x)', color='blue')
axs[0].set_title('Sine Function')
 
# 在第二个子图中绘制 cos(x)
axs[1].plot(x, y2, label='cos(x)', color='orange')
axs[1].set_title('Cosine Function')
 
# 在整体图中添加图例
fig.legend(loc='upper center', ncol=2)
 
# 调整布局
plt.tight_layout()
plt.show()

```

在这个示例中，我们使用`fig.legend()`方法在整个图形上方添加了一个全局图例，并且设置了图例的位置为`'upper center'`，列数为2。这样不仅保持了每个子图的独立性，同时也避免了重复内容。
![](https://img2024.cnblogs.com/blog/3448692/202412/3448692-20241220212318474-1461959730.png)


#### 四、图例的样式调整


除了设置图例的位置，还可以调整图例的样式，如字体大小、边框和背景颜色等。以下是一个示例：



```
import matplotlib.pyplot as plt
import numpy as np
 
# 生成数据
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)
 
# 创建包含两个子图的图表
fig, axs = plt.subplots(2)
 
# 在第一个子图中绘制 sin(x)
axs[0].plot(x, y1, label='sin(x)', color='blue')
axs[0].set_title('Sine Function')
 
# 设置图例样式
legend = axs[0].legend(loc='upper left', fontsize='x-large', frameon=False, edgecolor='blue', facecolor='lightgray')
 
# 在第二个子图中绘制 cos(x)
axs[1].plot(x, y2, label='cos(x)', color='orange')
axs[1].set_title('Cosine Function')
 
# 设置第二个子图的图例样式
legend2 = axs[1].legend(loc='upper right', fontsize='medium', frameon=True, edgecolor='red', facecolor='white')
 
# 调整布局
plt.tight_layout()
plt.show()

```

在这个示例中，我们分别为两个子图设置了不同的图例样式。第一个子图的图例没有边框，背景颜色为浅灰色，字体大小为`x-large`，边缘颜色为蓝色。第二个子图的图例有边框，背景颜色为白色，字体大小为`medium`，边缘颜色为红色。
![](https://img2024.cnblogs.com/blog/3448692/202412/3448692-20241220212337428-1662945889.png)


#### 五、图例位置的调整


有时候，我们可能需要将图例放置在图表之外的位置，这时可以使用`bbox_to_anchor`参数。以下是一个示例：



```
import matplotlib.pyplot as plt
import numpy as np
 
# 生成数据
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)
 
# 创建包含两个子图的图表
fig, axs = plt.subplots(2)
 
# 在第一个子图中绘制 sin(x)
axs[0].plot(x, y1, label='sin(x)', color='blue')
axs[0].set_title('Sine Function')
 
# 获取当前子图的位置
box = axs[0].get_position()
# 调整子图位置，为图例留出空间
axs[0].set_position([box.x0, box.y0, box.width, box.height * 0.8])
 
# 在图表外部添加图例
axs[0].legend(loc='center', bbox_to_anchor=(0.5, 1.2), ncol=2)
 
# 在第二个子图中绘制 cos(x)
axs[1].plot(x, y2, label='cos(x)', color='orange')
axs[1].set_title('Cosine Function')
 
# 调整布局
plt.tight_layout()
plt.show()

```

在这个示例中，我们首先获取了第一个子图的位置，然后调整了子图的高度，为图例留出空间。接着，使用`bbox_to_anchor`参数将图例放置在图表外部的中心位置。
![](https://img2024.cnblogs.com/blog/3448692/202412/3448692-20241220212355452-1658178884.png)


#### 六、结论


在数据可视化中，合理使用图例可以极大提升图表的可读性。在Python中，利用matplotlib创建的子图可以很容易地添加图例，无论是为每个子图单独添加，还是统一在一起。本文详细介绍了如何在多个子图中显示图例，包括全局图例的显示、图例样式的调整和图例位置的调整等。通过这些方法，你可以更灵活地创建具有丰富信息的图表，帮助观众更好地理解数据。


 本博客参考[楚门加速器](https://shexiangshi.org)。转载请注明出处！
