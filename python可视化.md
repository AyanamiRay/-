## matplotlib.pyplot
### Figure画图
- 设置标题
```python
plt.title('figure')
```
- 设置图例
```python
plt.plot(x,y,label='label')
plt.legend()
```
- 设置坐标轴标签
```python
plt.xlabel('x')
plt.ylabel('y')
```
- 设置坐标轴范围
```python
plt.xlim(start,end)
plt.ylim(start,end)
# or
plt.axis([x_start,x_end,y_start,y_end])
```
- 设置图像大小
```python
plt.figure(figsize=[6,6])
```
- 设置箭头标注
```python
plt.annotate(s,xy,*args,**kwargs)
# s  注释字符串
# xy 注释目标点的坐标
# xytext 注释字符串的坐标
# textcoords 注释字符串所在的坐标系统，默认与xy相同
# arrowprops 箭头属性，字典
# arrowstyle 箭头样式
cnh = [13.608*1.06**i for i in range(1,31)]
us = [20.494*1.02**i for i in range(1,31)]
x = np.arange(1,31) +2018

plt.plot(x,cnh,label='CN')
plt.plot(x,us,label='US')
plt.legend()
plt.xlim(2020,2040)
plt.ylim(20,50)
plt.annotate('miracle',xy=[2035,35],xytext=[2035,50],arrowprops=dict(arrowstyle='->',connectionstyle='arc3'))
plt.show()
```
<center>
<img src='annotate.png'><img>
<br>
<div>箭头标注</div>
</center>
- 添加文字
```python
plt.text(x,y,s,fontdict=None,**kwargs)
# 在x,y坐标处添加文本，s 为文本内容
# fontsize 文本字体大小
# ha ha='center' 水平对齐 left right
# va center水平居中 top顶端居中 bottom 底端居中 baseline 底线居中
```
- 颜色，标记，线型和图表风格
```python
plot(x,y,color='',marker='',linestyle='')
# color，marker，linestyle可以任意排列
# 绿色虚线
plt.plot(x,y,'g--') 
# 绿色圆圈标记虚线
plt.plot(x,y,'go--')
```
<center>
<img src='color.png'><img>
<br>
<div>支持颜色</div>
</center>

[支持的marker样式](https://matplotlib.org/3.1.1/api/markers_api.html)
- Style 图片风格
```python
#调用方式
plt.style.use('ggplot')
#查看所有style
plt.style.available
```
[各个风格对应效果]([plt.style.available](https://tonysyu.github.io/raw_content/matplotlib-style-gallery/gallery.html))
### Subplot子图
- plt.subplots创建多个子图
```python
subplots(nrows=1,ncols=1,sharex=False,sharey=False,squeeze=True,subplot_kw=None,gridspec_kw=None,**fig_kw)
#返回一个figure对象和一个axes对象的数组
#nrows  subplot行数
#ncols  subplot列数
#sharex 所有subplot使用相同x轴刻度，调节xlim会影响所有subplot
#sharey 同上
```
```python
#Axes
fig， axes = plt.subplots(2,2)
axes[0,0].plot(np.random.randn(50).cumsum(),'k--')
axes[0,1].hist(np.random.randn(100),bins=20,color='k',alpha=0.3)
axes[1,0].scatter(np.arange(30),np.arange(30)+np.random.randn(30))
plt.show()
```
plt.suptitle()/fig.suptitle()方法可以为figure对象添加一个居中的标题
- plt.subplot创建子图
```python
subplot(nrows,ncols,index,**kwargs)
```
```python
plt.subplot(221)
plt.plot(np.random.randn(50).cumsum(),'k--')
plt.subplot(222)
plt.hist(np.random.randn(100),bins=20,color='k',alpha=0.3)
plt.subplot(223)
plt.scatter(np.arange(30),np.arange(30)+np.random.randn(30))
plt.show()
```
- 调整subplot周围间距
```python
#对于plt.subplots的figure对象
fig.subplots_adjust(wspace=0.4,hspace=0.4)
```
- 设置子图的标题、轴标签、刻度、刻度标签及添加图例
```python
AxesSubplot.set_title()           #设置标题

AxesSubplot.set_xlabel()          #设置轴标签
AxesSubplot.set_ylabel()         

AxesSubplot.set_xticks()          #设置刻度 （横坐标等于哪些值的时候显示刻度）
AxesSubplot.set_yticks()

AxesSubplot.set_xticklabels()     #设置刻度标签 （刻度之下显示什么，默认是其代表的值）
AxesSubplot.set_yticklabels()
```
### matplotlib支持的图
[支持绘制图的具体方法](https://matplotlib.org/tutorials/introductory/sample_plots.html)
- hist() 直方图
- streamplot() 流图
- 三维绘图
- 路径(matplotlib.path)
- bar() 
- pie() 饼图
- table()
- scatter()
- fill()
- 对数图(semilogx(),semilogy(),loglog())
- polar() 极坐标图