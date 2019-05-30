## 搜狗开源最新NLP研究成果，打造业内最全机器阅读理解工具包SMRC

关注前沿科技 [量子位](javascript:void(0);) *今天*

##### 晓查 发自 凹非寺 量子位 出品 | 公众号 QbitAI

上周，搜狗在GitHub低调发布了机器阅读理解工具包**SMRC**（Sogou Machine Reading Comprehension）。

这是目前业内最全的TensorFlow版本的阅读理解工具集合，从相关数据集的下载到最后模型的训练和测试，一应俱全。

搜狗此次开源的目的也是为了帮助NLP从业人员快速实现已有的机器理解模型，从而更高效地开发新模型。

近两年来，NLP领域取得了许多突破性进展。但是在机器阅读理解方面开源的资源还是非常少。目前在CoQA上“打榜”的选手中，只有搜狗和微软公开了源代码。

搜狗开源SMRC恰逢其时，填补了该领域稀缺的开源资源。SMRC发布仅短短一周，已经成为该研究方向最热门的开源项目之一。

## 什么是SMRC？

说到SMRC，就不得不提近年来在NLP领域内的热门问题——机器阅读理解。它的目标是根据给定的问题和文章，在文章中抽取或改写文字片段作为问题的答案。

搜狗将机器阅读理解任务的流水线分解为4个步骤：**数据集读取、预处理、模型构建、训练和评估**，对每步都进行了抽象和模块化，以简洁的接口呈现。

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtCRjw3pxBCs8NZOTNjIQEF3p7Vsed5Y4TlOPoGaZrMHKUPaqzdW3Jwbyladic84wHbWxV2ZXEIRyQw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

在搜狗开源的SMRC工具包中，以上每个步骤都可以单独拿来使用，嵌入开发者自己的流程中，保证了整套工具的易用性和可扩展性。

同时，SMRC对已发表的多种机器阅读理解数据集、模型进行了整合或复现。

代码主要分为以下几个模块：

**1、数据集读取模块（dataset_reader）**

该模块集成了对SQuAD 1.0/2.0、CoQA以及中文数据集CMRC的读取和预处理功能。

**2、数据预处理（data、utils）**

data部分包含词表构建模块和负责特征变换和数据流的batch生成器。utils用于提取语言学特征。

**3、模型构建（nn、models）**

nn（神经网络）由机器阅读理解中的常用组件组成，可以快速构建和训练原型模型，避免部分重复工作。model中集成了常见的机器理解模型，如BiDAF、DrQA、FusionNet、QANet等等。

**4、模型训练与评估（examples）**

这一部分是运行不同模型的示例。

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtCRjw3pxBCs8NZOTNjIQEF3zvdRNJ4qTEkLSKr5WRWzLDEssIGJfsjYB3y4Aib5JdB3wYmL8q9tNibQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

SMRC代码安装使用十分方便。搜狗官方文档以SQuAD 1.0数据集、DrQA模型为例，只需二十几行代码即可实现一个主流机器阅读模型的训练和测试。

既然从模型到数据集得资源如此丰富，为何搜狗还要对它们进行整合？

这是由于部分机器理解模型没有官方实现版本，而其他开源模型由于框架不同，使得开发者在不同平台上需要自己理解、改进并重现，大大降低了开发效率。

针对这些问题，搜狗开源了 “阅读理解工具集合”。但SMRC并不是简单的整合，它还包含了搜狗近年来的NLP领域研究成果。

## SMRC中的搜狗技术

搜狗CEO王小川认为搜索的未来是问答，而机器阅读理解是现今问答技术发展的核心之一。

由于搜索、输入法等核心业务的驱动，搜狗在NLP尤其是机器阅读理解领域有着深厚的技术积淀。

可以说，SMRC项目中凝结了搜狗多年来最先进的研究成果。

今年1月，搜狗凭借BERT+Answer Verification(单一模型)登上CoQA榜单第一名，超过了国内外众多知名研究机构和高校，如微软、讯飞、清华、复旦，斯坦福等等。

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtCRjw3pxBCs8NZOTNjIQEF3hNZNbsvtjOtQxHpUicQRicfT9DprNrqUJjguk1XIMndLDO1R0QATCZLA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

搜狗在理论研究方向脚步一直不停。今年4月，搜狗与中科院自动化所合作，在信息检索领域的国际顶级学术会议**SIGIR 2019**上发表论文**《基于文档门控制器的开放域问答》**，提出了一种新的阅读理解算法。

所谓开放域问答（open-domain question answering），是指在给定任意类型的问题后，从任意资源中取得答案。越来越多的开放域问答方法采用机器阅读理解技术生成答案。

![img](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtCRjw3pxBCs8NZOTNjIQEF3wVLDkWw10F9Fa0a8GOiaDfq1QOLuS2rmxbe4OLZQDlTs9FS8PPqiaGog/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

然而，传统基于机器阅读理解的开放域问答技术存在数据噪声大、答案概率偏置等问题，使最后获得的答案效果欠佳。

为了解决以上问题，搜狗在传统模型基础上，引入了**文档门控制器**（Document Gate）来控制最终答案的输出，将文档选择信息引入到最终的结果中去。

此外，搜狗还使用了基于自举法（bootstrapping）的弱监督数据生成，解决传统弱监督数据中存在的噪声较大的问题。

搜狗不仅有理论研究文章发布，也非常重视技术落地化，过去的研究成果已经渗入到搜索产品中，不知不觉中为用户服务。

当我们在使用搜狗网页搜索时，当用户输入的搜索关键字是一个问题时，尤其是在医疗和法律等大众关心的问题，智能问答系统会尝试从搜索结果的网页中寻找答案并以最高优先级呈现给用户。

## 与行业分享成果

前面我们提到的CoQA挑战，现在已经有29家公司与机构提交了成绩，但是其中只有3家开源了自己算法，分别是微软、艾伦研究所和搜狗。

而SDNet、FlowQA只针对模型本身开源，并包含一些数据预处理工具，搜狗开源的是机器阅读理解一整套完整解决方案。

搜狗不吝分享最新的研究成果对学术界和工业界来说都是一个福音。

如果你是从事NLP研究的高校学生，那么SMRC可以帮助你快速将自己的模型与其他技术结合，这个过程中只需一个接口，大大降低了有志从事NLP学生的使用门槛，也能为研究人员减少重复劳动， 加速相关学术研究。

而如果你是一名工业界人员，拿来即用的SMRC能帮助你将搜狗的研究成果整合到自己产品方案中。

可以说，开源SMRC解决了开发者从数据集处理到模型训练等一系列痛点，是一项造福整个机器理解研究领域的大事。而对于普通大众来说，将来可能会看到更多的智能对话系统、解题应用，而背后或许就有搜狗开源技术默默的支持。

最后，附上SMRC的开源地址：
https://github.com/sogou/SMRCToolkit

— **完** —

**小程序|全类别AI学习教程**

[![img](https://mmbiz.qpic.cn/mmbiz_jpg/YicUhk5aAGtDpADEKp9rvicB48XgA8ueVdwNbXM1wibYx0ic2pYicwu3UCU5BM6fpDvbH8c4e9JV3uGvYaWAhvGiaTVQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)](https://mp.weixin.qq.com/s?__biz=MzIzNjc1NzUzMw==&mid=2247522055&idx=2&sn=a3039523b8fbd41139177143c177877d&chksm=e8d02075dfa7a9638b0bc3ebb146daf67781ab7513f08094205f20ad404123566ffd0be6db76&mpshare=1&scene=1&srcid=0530NqP621pUR67t4ICyVyQ0&key=55f99d04c6be589cb6bcb415ab0d17ec75577c96a8b6169397751ddf996a6b3d3cd9642be7c60e47846755e8c986cdcc46b9fe9c3594b93830056464701a348b7cb062253b7ad3b2f7b6336a9f78bd2f&ascene=1&uin=MjMzNDA2ODYyNQ%3D%3D&devicetype=Windows+10&version=62060833&lang=zh_CN&pass_ticket=p2XlI0Ofbuoae95AXUkwd7Vu8WFUZlqdMgTFTVbfWwGuNeaygo98vk8gYURMnTbY)

**AI社群|与优秀的人交流**



![img](https://mmbiz.qpic.cn/mmbiz_jpg/YicUhk5aAGtDcZyEBVM81oW4VRoNAibJWw1qt2Fxv2MINM4SsViaaOsD7exDSlDnoBKicLIXhuZlgPEPrne0p3NqNg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)



**量子位** QbitAI · 头条号签约作者





վ'ᴗ' ի 追踪AI技术和产品新动态



喜欢就点「在看」吧 !













微信扫一扫
关注该公众号