此处是为了记录一些视觉模型的宏观与微观图而准备的.

同时,如果你有任何关于优化流程图中某些细节或有更简洁直观表达流程图的工具的建议,都可直接提issue.

以下是一些术语,你可能会在流程图(以及我的mmdet注释代码)中看见它们:
* nc:检测/分割类别数.一般在代码中该值可能会由于最后计算loss时的激活函数选择方式的原因有些不同,当选择softmax时输出维度会变为nc+1.额外+1是表示背景类.
* bs:batch size
* nl:num_level,输入数据来自多少个层级
* na:每个特征点生成的anchor数量
* np:每个特征点生成的point数量,一般固定为1.后面可能会与na合并,表示prior数量.
* prior:模型的先验基准.在anchor-base中称为anchor,在anchor-free中称为point.在多阶段网络中的第二及后续阶段中称为roi,它是一阶段网络提供的动态的prior.
* batch_h/batch_w:网络的输入高度.
* h/w:网络输出特征图的高/宽.
* `[bs, c, h, w]`: 表示是一个4D类型的张量
* `[[bs, c, h, w], ] * nl`: 表示一个bs个张量.只不过外层结构是列表或元组
* `[nl*h*w, 4]`:多个层级上的数据cat到一起.注意h/w随着所处层级不同而不同.
* prior cls:模型的cls 分支输出的值,一般会经过sigmoid/softmax处理.表示prior的cls结果
* prior reg:模型的reg 分支输出的值,一般会经过sigmoid处理.表示prior的reg结果
* prior obj:模型的ob 分支输出的值,一般会经过sigmoid处理.表示prior的obj结果(并非所有模型都存在该分支)
