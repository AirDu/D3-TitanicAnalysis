# D3分析泰坦尼克人员数据
# 概要
泰坦尼克号的沉默是上世纪最著名的灾难之一。我简单分析了泰坦尼克号891名乘客数据，意图从中找出有哪些人在这场灾难中幸存，以及这些幸存者的特征。

# 设计
由于我的目的在于观察不同种类乘客的幸存者和罹难者人数，因此我选用了柱状图作为我的分析工具。

在简单观察了泰坦尼克号的数据后，我的第一直觉告诉我，性别、船舱将会是重要的特征，于是，我的第一份图稿即以性别、船舱为一组分类来进行统计。

为了统计数量，我给每个人员的数据中增加了Count项，值为1。这个新添的特征仅仅为了统计数量。

第一份草图的结果显而易见，在这场灾难中，女性幸免于难的几率要比男性大得多，这也正如那个著名的电影《泰坦尼克号》中上演的一样，船只沉默之时，绅士们将女性安置在救生艇上。与这个结果同样明显的是，舱位的等级，与幸存的几率成正比，也就是说，一等舱的乘客幸免于难的几率要比三等舱的乘客大。

然而第一份草图完成的有些随意，我没有刻意去排版，配色也是dimple.js默认的红蓝配色，并且，幸存者是红色。在听取了我的女朋友的意见后，我在第二份图标中更改了配色，由原先的红蓝配色改为绿和灰。绿色本身就代表着生命，这里是幸存者的颜色。灰色则相反，代表了死亡，这里是罹难者的颜色。同时，我调整了图标在网页中的位置，移到了屏幕中间，这样看起来会更舒适。最后，我把每个性别组中的柱状图，按照船舱，从1到3依次排序。

随后，我将这一成果展示给我的一位程序员朋友看，他提醒我，除了性别和船舱，年龄是否也是一项重要的指标？譬如儿童的幸存比例是否比成年人要高？这个想法提醒了我，于是，我先给每个乘客按照年龄分段添加了一个特征Span。这里我按照0-8，9-17，18-30，31-50，51+，Unknown来对年龄分段。Unknown是一些没有年龄的数据。同样，对于年龄，我依然采用柱状图进行分析。这次的分析结果让我有些惊讶，因为0-8岁的儿童的存活率没有我想象的高————它甚至还不如二等舱的女性的生还率高。但总体而言，0-8岁的儿童的幸存率已经是各个年龄段中最高的了。

这之后，我又听取了一些朋友的建议，更改了我的图标。在最终成图中，我增加了图例提示，告诉观众灰色代表遇难，绿色代表生还。并且，我将性别和船舱特征合并为了一个特征，ClassSex，这样一来，图中X轴上的坐标就是Class-1 Femle，而不会是此前图中只有mail/female，却没有船舱等级的尴尬描述。最后，我把年龄的统计由数量变为了百分比，且加入了船舱等级作为第二个分类标准。出人意料的是，一等舱中0-8岁儿童的生还率居然不如二等舱的高，这是其他所有年龄段都不存在的现象。并且，在9-17岁年龄段中，一等舱的存活率为100%。

经过这次数据分析，我发现这么几个规律：
* 女性的生还几率要远大于男性。
* 船舱等级和生还率整体成正比，即一等舱大于二等舱大于三等舱。
* 儿童的幸存率是所有年龄段中最高的。

# 反馈
## 第一份图
* 配色方案不合适，dimple自带的配色方案中，将幸存者分配了红色，罹难者为蓝色。
* 图标的整体样式，位置需要调整。
* 性别组中的船舱没有排序，看起来很奇怪，不符合人类的直觉。

## 第二份图
* 单单性别和船舱的统计还不够，应当把年龄加上。
* 数据中年龄数据丢失的人员不应该删除，而是单独分组。
* 从性别/船舱切换到年龄的动作，应该由用户来触发。

## 第三份图
* 应当添加图例来指示图中的颜色。
* 此前性别/船舱图中，X轴只显示了性别，没有显示船舱，这不方便。
* 因为儿童组人数较少，年龄可以改成百分比。
* 年龄图也应当添加船舱来观察不同船舱的生还率。

# 资源
* [d3.js](https://d3js.org/)
* [dimple.js](http://dimplejs.org/)
