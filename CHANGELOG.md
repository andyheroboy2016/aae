#### 0.2.6-201911041408-SNAPSHOT
>- 优化了语义匹配阶段的问题查找方法，利用正则匹配‘Q ’的方式代替原来的根据‘in_response_to’字段两阶段查找问题句子的方式，直接到数据库中匹配出表示问题的句子，并且只返回text字段，提升查询效率。
>- 优化了语义匹配阶段的算法，现统一采用词向量余弦值的方式来计算相似度，并且使用了向量化并行计算代替for循环，以提升计算效率。
>- README中增加了新的常见问题。
>- 删除了一些sf语料文件，为了保证各个语料文件的样本个数均匀。
>- 增加对learning.txt的删除检查，若发现本次学习前上一次的该文件没被删除，就先删除后再学习。
>- 修改不能回答时的默认回复。
>- 提高闲聊意图下的语义匹配最大阈值，并增加降级策略的指定阈值。
>- IntentClassifier类改成了单实例的。
>- 增加了语料“文本-向量”索引文件的构建和加载函数。
>- 增加对“小黄鸡”语料的处理函数。
>- 简化了聊天页面的问候语。
>- test方法中添加了对“test_build_text_vec_indx”方法的调用。
>- 增加了对问题字符长度的判断，若长度为1，则直接判别为聊天意图。 
>- 提高“多个候选问答对的场景下，若第一条问答对的分数大于0.8，则只返回首个问答对的答案”逻辑中的0.8到0.95，让回复更精准。
>- 提交的问题前拼上'Q '标记以便和数据库中的问题格式一致。
>- 语义匹配逻辑中去掉了对文本统一转小写的代码，在中文文本中，统一转小写的的操作意义不大。
>- .gitignore中添加对‘闲聊’语料文件和‘文本-向量索引文件’的忽略。

#### 0.2.5-201908211444-SNAPSHOT
>- .gitignore中添加对__pycache__/目录的忽略。 anai 2019/8/21 14:43

#### 0.2.4-201908211120-SNAPSHOT
>- .gitignore中添加对whl类型的文件的忽略。 anai 2019/8/21 11:19
>- readme中提供了whls文件的下载链接。 anai 2019/8/21 11:18
>- 删除了requirements.txt中2个不是必须添加的依赖包，因为这两个包一般在创建新的虚拟环境的时候就已经安装了。 anai 2019/8/21 10:56
>- 修改readme中关于安装包的说明，目前采用whl的方式来安装，避免重新下载和构建。 anai 2019/8/21 10:55

#### 0.2.3-201904291112-SNAPSHOT
>- 支持通过python命令执行testmain.py、kbqa_main.py、tornado_main.py脚本
>- 完善了README文档

#### 0.2.2-201904161432-SNAPSHOT
>- 将主要文件中的“税服”一词改成更通用的“业务”
>- 添加了README文档

#### 0.2.1-201902261925-SNAPSHOT
>- 只采集问答对中的问题用作训练集
>- 词向量模型分类器中计算分数时加入了阈值的控制逻辑（注意：虽然加了逻辑，但是词向量模型目前并没有使用）
>- 增加了文本摘要接口

#### 0.2.0-201801021334-SNAPSHOT
>- 引入词向量做为句子的特征表示
>- 语义推理模块使用余弦相似度算法代替莱温斯坦距离算法


#### 0.1.4-201812191040-SNAPSHOT
>- 修复偶尔问一些非领域知识会报500错误的问题

#### 0.1.3-201812171006-SNAPSHOT
>- 自动提示功能支持根据top_n参数返回问题
>- 当匹配到多个问答对时，若首条问答对的分数大于0.9，则只返回首条问答对
>- 重构了目录结构，将语料和配置相关的文件与核心代码分离，方便部署

#### 0.1.2-201812131530-SNAPSHOT
>- 支持从配置模块中修改默认回复内容
>- 支持从配置模块中修改意图识别分数阈值
>- 支持从配置模块中修改语义理解分数阈值
>- 意图识别分数阈值增加最小阈值，以支持降级回复
>- 语义理解分数阈值增加最小阈值，以支持降级回复
>- 语义理解模块代码重构，闲聊理解和业务领域知识理解分开处理
>- 解决意图识别未能匹配到任何意图时返回空数组的问题
>- 解决意图识别匹配到多个意图分类后，可能导致语义理解匹配到项总数超过3个的问题
>- 改为使用多项式朴素贝叶斯分类器，提升了对词问题的识别
>- 自定义分词表取消对“退运”扩展分词，只保留“退运”
>- 自定义分词表取消对“离岸价”扩展分词，只保留“离岸价”
>- 自定义分词表取消对“汇率”扩展分词，只保留“汇率”
>- 默认回复内容修改，不再使用请致电xxx以及转人工客服的引导语，因为用户群体定位是内部使用
>- history-learn.txt中增加对标注时间的记录

#### 0.1.1-201812101330-SNAPSHOT
>- 学习接口中对答案做了300字内的限定

#### 0.1.0-201812051215-SNAPSHOT
>- 对聊天页面的操作体验做了一些优化
>- 修复答案中的空格被自动消除的问题
>- 修复可以利用添加答案进行script脚本注入的问题