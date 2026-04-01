# <center>第一届基于情景的常识推理评测任务（SCoRE2026）</center>

**[<center>👉 <font style=color:rgb(226,76,71)>点我立即报名</font> 👈</center>](https://docs.qq.com/form/page/DVURKQ3NGcmtEZmxu)**

- 组织者/主席：詹卫东、穗志方
- 工作人员：胡楠 ，肖力铭，秦宇航，邓思锐，崔香，蔡奇栩，姜秀旻，丁锦坤，张子涵，王希豪，孙春晖，邢丹，杨奕欣，马敬原，李政，王悦
- 主办单位：北京大学 
- 联系方式：[hunan@stu.pku.edu.cn]()


> - <a href="#content">任务内容</a>
> - <a href="#data">评测数据</a>
>     - <a href="#data_form">数据字段</a>
>     - <a href="#samples">数据样例</a>
>     - <a href="#distribution">数据概况</a>
> - <a href="#eval">评价标准</a>
> - <a href="#time">评测赛程</a>
> - <a href="#rules">评测规则</a>
> - <a href="#award">奖项设置</a>
> - <a href="#otherinfo">其他信息</a>
> - <a href="#committee">评测委员会</a>

### <center>1.  <span id="content">任务内容</span></center>

#### 1.1  任务简介

推理是一种高级认知功能，涉及基于现有知识对新信息进行分析、归纳和演绎。它在人类智能中起着基础性作用。虽然以往的基准测试主要侧重于评估大语言模型（LLMs）在复杂、专业领域内的推理能力，但它们往往忽视了类人认知的一个关键方面：常识推理。评估大型语言模型中的这种常识推理能力对于人工智能的发展至关重要。这种基本能力显著影响着 LLMs 在日常情境中的决策，并且对于在通用人工智能（AGI）中迈向类人智能至关重要。
为了全方位、细粒度地诊断大模型的常识推理能力，我们提出了基于情景的常识推理评测数据集(Scenario-based Commonsense Reasoning Evaluation, SCoRE)，用以评估大语言模型在常识场景下的复杂逻辑推理能力。根据所涉及的常识领域，该数据集包含的任务可分为以下五类：
（1）空间常识推理：给定一个空间场景和若干已知的实体间方位关系，本任务要求机器推理出实体在空间场景中的位置，以及未知的方位关系。
（2）时间常识推理：给定一个包含若干事件的时间叙述场景和已知的事件间时间关系（如先后顺序、持续时长、相对或绝对时间点），本任务要求机器推理出事件在时间轴上的具体时刻，以及未知的事件间时间跨度或次序关系。
（3）社会常识推理：给定一个社会交互场景和若干已知的人物间人际关系（如亲属、职场、朋友或师徒关系），本任务要求机器推理出人物在社会网络中的具体角色或地位，以及人物间隐含的或未知的社会关系。
（4）自然常识推理：给定一组自然物体（或实体）和若干已知的属性约束条件（如类别归属、物理性状、功能用途或感官特征），本任务要求机器推理出物体与描述（或位置）的一一对应关系，以及物体未知的属性或分类特征。
（5）融合常识推理：融合领域任务描述旨在构建一个多维度条件交织的推理问题。它要求机器同时处理来自空间、时间、自然属性及社会关系等多个领域的约束与常识，并建立统一的推理模型以进行协同分析与决策。其核心挑战在于，单一领域的逻辑链条不足以解决问题，必须识别并整合不同领域的隐含联系，才能对复杂多因素情境进行有效推断。

### <center>2.  <span id="data">评测数据</span></center>

#### 2.1  <span id="data_form">数据字段</span>

（1）text：文本材料。字符串。机器需要阅读理解 text 后回答问题。
（2）question：机器需要回答的问题。字符串。形式上是一个句中有下划线的陈述句。
（3）option：题目选项。字典，键-值对为“选项字母-选项内容”。最少有两个键-值对，
最多有四个键-值对。选项字母为 A、B、C、D。
（4）answer：题目答案。数组，元素是选项字母。例如，["A"]表示机器选择 option 的
A 选项作为答案。测试集没有 answer 字段。
#### 2.2  <span id="samples">数据样例</span>
SCoRE数据集中的所有题目包含中英两个版本，中文题和英文题除了实体的名称不同，其选项、问题和答案均为一一对应关系。

##### 2.2.1  <span id="task_space">空间常识推理任务</span>
中文样例
"text": "王处一、谭处端、丘处机、刘处玄、王重阳、周伯通六位道士在终南山重阳宫内盘腿席地打坐，围成一个圆圈，修炼内功，六人的位置恰好形成一个正六边形。六人都面朝外背对圆心而坐。任意相邻两人之间的间距相等，大约为一米。已知：丘处机在王处一顺时针方向第一个位置，谭处端在刘处玄右边数起第三个位置，谭处端在王重阳顺时针方向第二个位置，周伯通的右边接着就是谭处端，王处一的右边起第三个就是王重阳。"
"question": "周伯通在___左侧范围内。",
"options": {
            "A": "王处一",
            "B": "刘处玄",
            "C": "丘处机",
            "D": "以上选项都不是"
        }
"answer": ["A"]
英文样例
"text": "Robert, Mary, Patricia, John, James, David, —these six Taoist priests are seated cross-legged on the ground inside the Chongyang Palace on Zhongnan Mountain, arranged in a circle as they practice internal martial arts. The positions of the six priests form a perfect hexagon. Each priest is facing outward, with their backs toward the center of the circle. The distance between any two adjacent priests is equal, approximately one meter. It is known that: Patricia occupies the first position clockwise from Robert; Mary occupies the third position to the right of John; Mary occupies the second position clockwise from James; Mary is directly to the right of David; James occupies the third position to the right of Robert. ",
"question": "David is situated in the area to ___'s left."
"options": {
     "A": "Robert",
     "B": "John",
     "C": "Patricia",
     "D": "None of the above"
     }
"answer": ["A"]
【说明】
题目构建了一个六人背对背围坐的情景，为了解答周伯通在哪些人的左侧范围内，需推知周伯通的右侧范围内有哪些人。根据已知信息可推知，按照顺时针方向，六人的排列分别是周伯通、谭处端、王处一、丘处机、刘处玄和王重阳。因此，在周伯通右侧范围内的是谭处端和王处一。答案为A：王处一。



##### 2.2.2  <span id="task_time">时间常识推理任务</span>

中文样例
"text": 
"小明的女儿正在给朋友讲述父亲的一生: 
(1)在第一届普利策奖颁发之前17年，他出生; 
(2)他度过一生的时间比他上初中的时间长96年; 
(3)他开始上小学是在IBM发布第一款个人电脑的74年前; 
(4)他上小学一共6年; 
(5)他开始上初中是在第一届普利策奖颁发的4年前; 
(6)在他出生之后16年，他初中毕业; 
(7)在他开始上初中的2年之后，他遇见未来的妻子; 
(8)在他开始上初中的3年之后，他开始上高中; 
(9)在他出生之后19年，他高中毕业; 
(10)在1919年，他开始上大学; 
(11)在他小学毕业之后11年，他大学毕业。",
    "question": "在___之后15年，他遇见未来的妻子。",
    "options": {
            "A": "他出生",
            "B": "他开始上小学",
            "C": "他小学毕业",
            "D": "以上选项均不符合题目要求"
        },
    "answer": ["A"],
	英文样例
"text": "Jack's daughter is telling her friends about the story of her father's life:
(1)Jack was born 17 years before the first Pulitzer Prizes were announced; 
(2)The total duration that Jack lived his life is 96 years longer than he studied in junior high school; 
(3)Jack started elementary school 74 years before IBM released the first personal computer; 
(4)Jack studied in elementary school and spent 6 years on it; 
(5)Jack started junior high school 4 years before the first Pulitzer Prizes were announced; 
(6)Jack graduated from junior high school 16 years after he was born; 
(7)Jack met his future wife 2 years after he started junior high school; 
(8)Jack started high school 3 years after he started junior high school; 
(9)Jack graduated from high school 19 years after he was born; 
(10)Jack started university in 1919; 
(11)Jack graduated from university 11 years after he graduated from elementary school.",
    "question": "Jack met his future wife 15 years after ___.",
    "options": {
            "A": "Jack was born",
            "B": "Jack started elementary school",
            "C": "Jack graduated from elementary school",
            "D": "None of the options above meet the requirements of the question"
        },
    "answer": ["A"]
【说明】由条件（1）和（5）可知，第一届普利策奖颁发于1917年，因此他出生于1900年（1917-17），开始上初中是在1913年（1917-4）。由条件（7）可知，遇见妻子的年份是开始上初中后2年，即1915年（1913+2）。因此，遇见妻子之前15年是1900年（1915-15），这正是他出生的年份。

##### 2.2.3  <span id="task_social">社会常识推理任务</span>
中文样例
"text": "已知：吴强是李晓静的弟子，也是钱静的下属。孙大伟是吴强的好哥们儿，也是钱静的男朋友。孙大伟是李晓静的师傅。赵伟是钱静的师傅。",
"question": "以下选项正确的是___",
"options": {
        "A": "钱静的男朋友是钱静的下属的弟弟",
        "B": "赵伟是孙大伟的女友的下属",
        "C": "钱静的男朋友是钱静的下属的好哥们儿",
        "D": "孙大伟的弟子是钱静的下属的领导"
       }
"answer": ["C"]
英文样例
"text": "Given: Wu Qiang is Li Xiaoqing's disciple, and also Qian Jing's subordinate. Sun Dawei is Wu Qiang's good buddy, and also Qian Jing's boyfriend. Sun Dawei is Li Xiaoqing's master. Zhao Wei is Qian Jing's master.",
"question": "Which of the following options is correct?",
"options": {
"A": "Qian Jing's boyfriend is the younger brother of Qian Jing's subordinate.",
"B": "Zhao Wei is the subordinate of Sun Dawei's girlfriend.",
"C": "Qian Jing's boyfriend is the good buddy of Qian Jing's subordinate.",
"D": "Sun Dawei's disciple is the leader of Qian Jing's subordinate."
}
"answer": ["C"]
【说明】
根据给定的关系分析：钱静的男朋友是孙大伟。钱静的下属是吴强。孙大伟是吴强的好哥们儿。因此，选项C“钱静的男朋友是钱静的下属的好哥们儿”正确。

##### 2.2.4  <span id="task_nature">自然常识推理任务</span>
中文样例
"text": "一面墙上贴着萨克斯管、话梅、奶茶、茶叶筒四种物品的照片。已知：1号照片上的物品不属于加工食品；3号照片上的物品不属于加工食品；1号照片上的物品不属于工具；2号照片上的物品的味道是甜的；3号照片上的物品不属于饮品；1号照片上的物品不属于饮品。",
"question": "茶叶筒在____号照片上。",
"options": {
            "A": "1",
            "B": "2",
            "C": "3",
            "D": "4"
        },
"answer": ["C"],
英文样例
"text": "On a wall pasted photos of four different items: saxophone, preserved plum, tea with milk, tea caddy. Now we know that: The item on photo No.1 is not a processed food; The item on photo No.3 is not a processed food; The item on photo No.1 is not a tool; The item on photo No.2 tastes sweet; The item on photo No.3 is not a drink; The item on photo No.1 is not a drink.",
 "question": "Tea caddy is on photo No.____.",
 "options": {
            "A": "1",
            "B": "2",
            "C": "3",
            "D": "4"
        },
 "answer": ["C"]
【说明】物品分类：
加工食品类：话梅、奶茶。
非加工食品类：萨克斯管（乐器）、茶叶筒（容器）。
根据线索“1号和3号不属于加工食品”，可知1号和 3号只能是萨克斯管或茶叶筒。
根据线索“1号不属于工具”：茶叶筒本质是容器，属于生活工具；而萨克斯管是乐器，不属于工具。因此，1号是萨克斯管。既然1号是萨克斯管，那么剩下的3号就是茶叶筒。

##### 2.2.5  <span id="task_mix">融合领域常识推理任务</span>

###### 2.2.5.1  <span id="task_mix_space_nature">空间+自然常识推理任务</span>
中文样例
"text": "酒盅、百合花、葡萄酒、瑶柱、馄饨、马六种商品在三层货架上放置，货架紧靠商店南墙放置，每层两格，各放一种商品，一在东，一在西。顾客站在货架前选购商品。在描述各商品的位置关系时，约定以顾客自身左右方位为参照，即东侧商品为左，西侧商品为右。已知：馄饨在工具右下方且二者不隔层；花草是饮品的左邻；4条腿的动物在工具下一层；馄饨在花草右下方且二者隔了一层；工具在二层东侧。",
"question": "_ 在马右边且二者同层",
"options": {
            "A": "瑶柱",
            "B": "百合花",
            "C": "葡萄酒",
            "D": "以上选项都不是"
        },
"answer": ["D"]
英文样例
"text": "Handleless wine cup, lily, port wine, conpoy, wonton, horse, six items are placed on a three-tier shelf, which is positioned against the south wall of the store. Each tier has two sections, with one type of item placed in the east section and one in the west section. A customer is standing in front of the shelf. When describing the positional relationships of the items, it is agreed that the customer's own left and right will be used as a reference, with the east section being on the left and the west section being on the right. It is known that:\nThe wonton is located at the lower right of the tool and there is no tier between them,\nThe flower or grass is directly to the drink's left,\nThe animal with 4 legs is under the tool,\nThe wonton is located at the lower right corner of the flower or grass and there is a tier between them,\nThe tool is on the east side of the second tier.",
"question": "_ is to the right of horse and both are on the same tier",
"options": {
        "A": "conpoy",
        "B": "lily",
        "C": "port wine",
        "D": "None of the above"
        },
"answer": ["D"]
【说明】根据已知条件，可还原货架布局：一层东侧为马，西侧为馄饨。二层东侧为酒盅，西侧为瑶柱，三层东侧为百合花，西侧为葡萄酒。正确答案“馄饨”不在选项中，因此选D。
###### 2.2.5.2  <span id="task_mix_space_social">空间+社会常识推理任务</span>
中文样例
"text": "四人来到火锅店吃火锅，选了四人卡座坐下。卡座分列一张长方形桌子长边两侧，每排卡座上坐两人。面对面而坐。孙启航的前妻在孙启航的挚友同侧左边，孙启航的妹妹是孙榆琴的哥哥的左邻。孙启航是孙榆琴的哥哥，也是冯震宇的挚友。韩向秋是孙启航的前妻，也是冯震宇的前女友。",
"question": "孙启航的妹妹和___不挨着坐",
"options": {
            "A": "冯震宇",
            "B": "韩向秋",
            "C": "孙启航",
            "D": "孙榆琴"
        },
"answer": ["A","B"]
英文样例
"text": "Four people went to a tea restaurant to eat and chose a four-person booth. The booth is arranged along the long sides of a rectangular table, with two people sitting on each side, facing each other. Jacob Hernandez's elder sister is on Julia Brown's boyfriend's left on the same side, Jacob Hernandez's neighbor is the left neighbor of Julia Brown's neighbor.\nJulia Brown is Jacob Hernandez's neighbor, and also Donald Rodriguez's girlfriend. Mary Hernandez is Jacob Hernandez's elder sister, and also Donald Rodriguez's ex-wife.",
        "question": "Jacob Hernandez's neighbor and ___ are not sitting next to each other",
        "options": {
            "A": "Donald Rodriguez",
            "B": "Mary Hernandez",
            "C": "Jacob Hernandez",
            "D": "Julia Brown"
        },
        "answer": ["A","B"]
【说明】根据题目描述，可以确定四人的身份：
孙启航：孙榆琴的哥哥，冯震宇的挚友。
孙榆琴：孙启航的妹妹（由“孙启航是孙榆琴的哥哥”可推知）。
冯震宇：孙启航的挚友。
韩向秋：孙启航的前妻。
四人的空间布局为：
一侧：韩向秋、冯震宇
另一侧：孙榆琴、孙启航
孙榆琴只和孙启航挨着坐，和冯震宇、韩向秋都不挨着。因此答案为A、B。
###### 2.2.5.3  <span id="task_mix_time_nature">时间+自然常识推理任务</span>
中文样例
"text": "老农老赵，在1980到2000年之间一共种植过四种植物：生菜、当归、月季、腰果。每年他最多只种一种植物，且每种植物的种植时间都是连续的。已知：
(1)老赵开始种植坚果是在老赵不再种植月季的8年后;
(2)在1987年，老赵开始种植月季;
(3)老赵种植月季的时间比老赵种植开黄色花的蔬菜的时间长1年；
(4)老赵不再种植月季的时间比老赵开始种植月季晚3年；
(5)老赵种植坚果的时长为2年；
(6)在老赵开始种植开黄色花的坚果的2年之后，老赵不再种植开黄色花的坚果;
(7)从1992年开始老赵种植开白色花的花草，一直到1998年;
(8)1990年至1992年，老赵种植绿色的物品;"
 "question": "以下选项中正确的是____",
 "options": {
            "A": "老赵不再种植当归和老赵开始种植生菜之间相隔8年",
            "B": "老赵种植生菜一共2年",
            "C": "老赵开始种植月季是在老赵不再种植当归的11年前",
            "D": "老赵开始种植腰果是在老赵不再种植当归那年之后"
        },
"answer": ["A", "B","C"]
英文样例
"text": "Old farmer Jack has planted four kinds of crops between 1980 and 2000: lettuce、Angelica sinensis、Chinese rose、cashew nut. He can plant at most one crop each year, and the planting periods of each crop are continuous. It is known that:
(1)Jack started planting the nut 8 years after Jack ended planting the Chinese rose;
(2)In 1987, Jack started planting the Chinese rose;
(3)Jack planted the Chinese rose 1 year more than Jack planted the vegetable with yellow flower;
(4)Jack ended planting the Chinese rose 3 years after Jack started planting the Chinese rose;
(5)Jack planted the nut and spent 2 years on it;
(6)Jack ended planting the nut with yellow flower 2 years after Jack started planting the nut with yellow flower;
(7)Beginning in 1992, Jack planted the flower or grass with white flower for 6 years;
(8)Jack planted the green item from 1990 to 1992;",
"question": "Select the correct statement(s): ____",
"options": {
    "A": "There is a 8 years gap between Jack started planting lettuce and Jack ended planting Angelica sinensis",
    "B": "Jack planted lettuce and spent 2 years on it",
    "C": "Jack started planting Chinese rose 11 years before Jack ended planting Angelica sinensis",
    "D": "The year Jack started planting cashew nut postdates the year Jack ended planting Angelica sinensis"
        },
"answer": ["A", "B","C"],

| 植物 | 开始年份 | 结束年份（不再种植的那一年） | 实际种植年份                       | 时长 |
| ---- | -------- | ---------------------------- | ---------------------------------- | ---- |
| 月季 | 1987     | 1990                         | 1987, 1988, 1989                   | 3年  |
| 生菜 | 1990     | 1992                         | 1990, 1991                         | 2年  |
| 当归 | 1992     | 1998                         | 1992, 1993, 1994, 1995, 1996, 1997 | 6年  |
| 腰果 | 1998     | 2000                         | 1998, 1999                         | 2年  |


因此答案选A、B、C。
###### 2.2.5.4  <span id="task_mix_time_social">时间+社会常识推理任务</span>
中文样例
"text": "已知：周宁馨是杨威的邻居，也是朱乐行的下属。朱丹青是杨威的前妻，也是朱乐行的女儿。朱丹青的父亲、杨威的前妻、周宁馨的邻居和杨威的邻居四个人喜欢每星期定时播放的不同电视节目:
(1)在杨威的前妻收看《脱口秀大会》的6天之后，杨威的邻居收看《体育新闻》;
(2)周四，杨威的前妻收看《脱口秀大会》;
(3)在杨威的前妻收看《脱口秀大会》之后1天，朱丹青的父亲收看《热点直播间》;
(4)在杨威的邻居收看《体育新闻》之后3天，周宁馨的邻居收看《越战越勇》",
        "question": "在杨威收看《越战越勇》之后____，周宁馨收看《体育新闻》",
        "options": {
            "A": "1天",
            "B": "4天",
            "C": "2天",
            "D": "3天"
        },
        "answer": ["B"],
英文样例
"text": "It is known that: Ethan Garcia is Martha Garcia's dad, and also Ralph Miller's friend. Mary Martin is Ethan Garcia's teacher, and also Ralph Miller's subordinate. Ethan Garcia's friend, Ethan Garcia's teacher, Martha Garcia's dad, and Ethan Garcia's daughter like different TV shows that are broadcasted at fixed times every week:
(1)6 days after Ethan Garcia's teacher watches The Late Show with Stephen Colbert, Ethan Garcia's daughter watches SportsCenter;
(2)When it's Thursday, Ethan Garcia's teacher watches The Late Show with Stephen Colbert;
(3)Ethan Garcia's friend watches NBC Nightly News 1 day after Ethan Garcia's teacher watches The Late Show with Stephen Colbert;
(4)3 days after Ethan Garcia's daughter watches SportsCenter, Martha Garcia's dad watches Jeopardy!",
        "question": "____ after Ethan Garcia watches Jeopardy!, Martha Garcia watches SportsCenter",
        "options": {
            "A": "1 day",
            "B": "4 days",
            "C": "2 days",
            "D": "3 days"
        },
        "answer": ["B"]
【说明】
杨威的前妻：即朱丹青。
杨威的邻居：即周宁馨（题目已知“周宁馨是杨威的邻居”）。
周宁馨的邻居：根据邻居关系的相互性，周宁馨的邻居就是杨威。
朱丹青的父亲：即朱乐行。
根据线索(1)，“在杨威的前妻收看《脱口秀大会》的6天之后，杨威的邻居（周宁馨）收看《体育新闻》”。周四 + 6天 = 周三。周宁馨收看《体育新闻》= 周三。
根据线索(4)，“在杨威的邻居（周宁馨）收看《体育新闻》之后3天，周宁馨的邻居（杨威）收看《越战越勇》”。周三 + 3天 = 周六。杨威收看《越战越勇》= 周六。
周六到周三经过4天，因此答案选B。



#### 2.3  <span id="distribution">数据概况</span>

本数据集提供的训练集和验证集共计3600题。具体分布如下表所示：

| 领域 | 中文 | 英文 | 总计 |
| --- | --- | --- | --- |
| **单领域** | | | |
| 空间 | 500 | 500 | 1000 |
| 时间 | 500 | 500 | 1000 |
| 自然 | 500 | 500 | 1000 |
| 社会 | ---  | ---  | 合计 500 |
| **融合领域** | | | |
| 空间+自然 | --- | --- | 合计 100 |

测试集共计1000题


### <center>3.  <span id="eval">评价标准</span></center>
SCoRE2026使用准确率（Accuracy, ACC）作为评价指标和排名依据，公式如下：
ACC = 命中正确答案的比赛题数 / 比赛题目总数


### <center>4.  <span id="time">评测赛程</span></center>
| 时间 | 事项 |
| --- | --- |
| 2月20日-4月14日 | 开放报名 |
| 4月1日 | 发布训练集 |
| 4月1日 | 发布测试集，开放结果提交 |
| 6月1日 | 测试结果提交截止 |
| 6月6日 | 参赛模型提交截止 |
| 6月10日 | 评测论文初稿提交截止 |
| 6月12日 | 公布最终排名和获奖名单 |
| 6月30日 | 评测论文终稿提交截止 |
| 7月10日 | 评测论文录用通知 |
| 8月 | 评测研讨会 |

### <center>5.  <span id="rules">评测规则</span></center>
#### 一、参赛模型要求：
1. Dense 模型
参赛模型总参数量不得超过 8B。
2. MoE 模型
参赛模型总参数量不得超过 30B；
在标准推理配置下，每个 token 的激活参数量不得超过 3B。
其中：
“总参数量”指模型全部参数之和；
“激活参数量”指单个 token 在一次前向传播中实际参与计算的参数量总和。
#### 二、以下行为将取消获奖资格：
(1) 在模型训练、微调阶段使用测试集的数据。例如，用测试集生成伪标签数据进行数据增强；
(2) 将测试集的数据作为提示词示例使用；
(3) 测试集提交结果为人工作答结果；
(4) 使用SCoRE2026以外的其他数据集；
(5) 参赛模型不符合要求；
(6) 最终成绩无法复现。
#### 三、提交方式
通过[SCoRE2026线上自动评测系统](http://47.97.2.176:5000/)提交json文件，自动评分。

### <center>6.  <span id="award">奖项设置</span></center>

本次评测将评选出如下奖项：
一等奖拟定0-1名。
二等奖拟定0-2名。
三等奖拟定0-4名。
由中国中文信息学会为本次评测获奖队伍提供荣誉证书。


### <center>7.  <span id="otherinfo">报名方式</span></center>

请仔细阅读《[第一届基于情景的常识推理评测 SCoRE2026 参赛协议](https://github.com/PKU-SpaCE/SCoRE2026/tree/main/agreements/Agreement.md)》和《[第一届基于情景的常识推理评测 SCoRE2026 数据集使用许可](https://github.com/PKU-SpaCE/SCoRE2026/tree/main/agreements/LICENSE.md)》，然后点击进入 [报名链接](https://docs.qq.com/form/page/DVURKQ3NGcmtEZmxu)

### <center>8.  <span id="committee">评测委员会</span></center>

单位：北京大学、华为技术有限公司
主席：詹卫东、穗志方
工作人员：胡楠，肖力铭，秦宇航，邓思锐，崔香，蔡奇栩，姜秀旻，丁锦坤，张子涵，王希豪，孙春晖，邢丹，杨奕欣，马敬原，李政，王悦


