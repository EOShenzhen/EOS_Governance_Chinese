版权声明：

以下内容来自微信公共帐号“EOS技术爱好者”，搜索“EOSTechLover”即可订阅，译者Fred，校对Lochaiching。转载必须保留以上声明。仅授权原文转载。

本文原文链接为<http://iang.org/papers/ricardian_contract.html> ， 作者Ian Grigg，由本号“EOS技术爱好者”翻译。

------

***The Ricardian Contract ***

**李嘉图合约**

*Ian Grigg*

*Systemics, Inc.*

*iang@iang.org*

**Abstract**

*Describing digital value for payment systems is not a trivial task. Simplistic methods of using numbers or country codes to describe currencies, and ticker tape symbols to issue bonds, shares, and other financial instruments soon run into shortcomings in their ability to handle dynamic and divergent demands. The seemingly arbitrary variations in the meanings of different instruments are best captured as contracts between issuers and holders. Thus, the digital issuance of instruments can be viewed as the issuance of contracts.*

*This paper proposes that the contract is the issue. A document form is described that encompasses the inherent contractual nature of the financial instrument yet copes with the requirements of being an integral part of a payment system.*

**摘要**

描述支付系统的数字价值并不是一项简单的任务。使用数字或国家代码来描述货币的简单方法，以及用于发行债券、股票和其他金融工具的代码带符号很快就会遇到处理动态和不同需求的能力方面的缺陷。不同工具含义看似随意的变化最好被视为发行人和持有人之间的合约。因此，工具的数字发行可以看作是合约的发行。

本文提出合约是发行。描述了一份文件表格，其中涵盖了金融工具的固有合约性质，但是却符合作为支付系统不可或缺部分的要求。

**1. Introduction**

*Little work has been done on classification and description of value in the field of financial cryptography. This paper presents the Ricardian Contract, a method to identify and describe issues of financial instruments as contracts [1]. It was originally developed by Ian Grigg and Gary Howland as part of the Ricardo payment system.*

**1. 介绍**

金融密码领域的价值分类和描述工作做得很少。本文介绍了李嘉图合约，这是一种识别和描述金融工具合约问题的方法 [ 1 ]。它最初由Ian Grigg和Gary Howland开发作为Ricardo支付系统的一部分。

**1.1. The Origins **

*The original application was a bond trading system [2]. For trading, a basic component is a transfer or payment system which receives and acts on transfer instructions to move instruments (cash, bonds) from one account to another. Each instruction therefore must identify the instrument.*

*A means was required to capture, identify, and describe the traded instruments. There are thousands of bonds, and potentially millions of other instruments that could be issued and traded, and each has unique characteristics that are not amenable to compression into databases. To such a system, cash is no different to bonds, and requires the same description.*

**1.1 起源**

最初的应用是债券交易系统 [ 2 ]。对于交易而言，基本组成部分是转账或支付系统，它接收并执行转账指令，将工具（现金，债券）从一个账户转移到另一个账户。因此每条指令都必须标识该工具。

需要一种手段来捕获、识别和描述交易工具。有数以千计的债券和潜在的数以百万计其他可以发行和交易的工具，并且每个都有独特的特征，不适合压缩到数据库中。对于这种制度，现金与债券没有区别，并且需要相同的描述。

**1.2. The Problem**

*When someone issues a currency (or bond or share) over the Internet, what is it? What does the recipient have?*

*Few systems for issuance of value (payment systems) treat these questions adequately. They generally refer to existing external units of currency and tidy up loose edges in a user agreement. For example, Paypal, an issuer of dollars, relies on the familiarity of the US dollar to define much of its service offering. Gold issuers lean more heavily on their user agreements as the metal unit is not so familiar.*

*For trading, it is not sufficient to refer to well-known familiar references, as each instrument is different in finicky ways and these differences matter to traders. Even with currencies, however, the user has difficulty in determining the security and safety of one dollar with respect to another.*

*Classification by numbers or symbols is a starting point. Almost all systems of digital issuance identify their basic issue by allocating numbers or letters as currencies (for example, 840, "USD", "AUG" [3]). These systems runs into trouble quickly.*

*An issuer with many currencies or many issuers with the same nominal currency raises difficult questions. Can an issuer have two or more dollar units? For example, within ISO3166-1, there are three different US dollars: 840/USD (cash), 998/USS (same day), and 997/USN (next day). Similarly, how does one Digital Gold Currency ("DGC") differentiate his gold over that of another issuer, when all are known as "AUG"?*

**1.2 问题**

当有人通过互联网发行货币（或债券或股票）时，它是什么？接收者得到什么？

很少有发行价值的系统（支付系统）充分处理这些问题。它们通常指的是现有的外部货币单位，并在用户协议中整理宽松的边界 。例如，美元发行人Paypal依赖美元的熟悉度来定义其大部分服务产品。由于金属计量单位并不那么相关，黄金发行人更依赖于他们的用户协议。

对于交易而言，仅仅提及众所周知的熟悉的参考资料是不够的，因为每一种工具都有着不同需要注意的方式，而这些差异对贸易商来说都很重要。但是，即使使用货币，用户也很难确定一美元相对于另一美元的保障性和安全性。

按数字或符号分类是一个起点。几乎所有的数字发行系统都通过分配数字或字母作为货币来识别他们的基本问题（例如，840，“USD”，“AUG” [ 3 ]）。这些系统很快就会遇到麻烦。

许多货币或许多发行人使用相同名义货币的发行人提出了难题。发行人可以有两个或更多的美元单位？例如，在ISO3166-1中，有三种不同的美元：840美元（现金），998 美元（当天）和997 美元（第二天）。同样，当所有人都称黄金为“AUG”时，数字黄金货币（DGC）如何将他的黄金与另一个发行人的黄金区分开来？

**1.3. The Solution**

*As bonds are, at their essence, contracts between issuers and users, our problem reduces to one of issuing contracts. Whereas other issues have contracts, our issues are contracts.*

*Our innovation is to express an issued instrument as a contract, and to link that contract into every aspect of the payment system. By this process, a document of some broad utility (readable by user and program) is drafted and digitally signed by the issuer of the instrument. This document, the Ricardian Contract, forms the basis for understanding an issue and every transaction within that issue.*

*By extension, all issues of value, such as currencies, shares, derivatives, loyalty systems and vouchers, can benefit from this approach.*

**1.3 解决方式**

由于债券本质上是发行人和用户之间的合约，我们的问题也可以归结为发行合约。鉴于其他债券有合约，我们的发行也是合约。

我们的创新是将发行的工具表示为合约，并将该合约链接到支付系统的各个方面。在此过程中，由该工具的发行者起草并数字化签署了一份具有广泛用途的文件(由用户和程序可读)。该文件，即李嘉图合约，构成了理解这个发行以及该发行中每项交易的基础。

通过扩展，所有的价值问题，如货币、股票、衍生品、忠诚系统和凭证，都可以从这种方法中受益。

**1.4. Structure**

*This paper is structured as follows. In Section 2, we discuss conventional approaches to identifying and describing issuance, and explore questions and doubts surrounding these approaches. Then, in Section 3, a design to express issuance as a contract is presented. Finally, in Section 4, concluding remarks are added.*

**1.4 结构**

此篇文章的结构如下。在第2节中，我们讨论了识别和描述发行的传统方法，并探讨了这些方法的问题和疑问。在第3节中，提出了一个设计来表达发行合约。最后，在第4节中，添加结束语。

**2. Issues of Value as Contracts**

**2.1. A First Generation Scheme**

*Consider the case of the pioneering digital cash scheme, eCash, as originally fielded by DigiCash BV. The first valuable currency, issued by Mark Twain Bank of the USA, was identified with the number 4. Lore has it that the early system allocated a small sequential number to each currency. Test systems had already acquired 0,1,2,3 and thus 4 was the next. DigiCash's marketing assumptions then changed to assume one issue per country. In time, this scheme was adjusted to issue currencies numbered after international dialling codes (e.g., 49 for Germany, 61 for Australia). The shortfalls of this scheme became apparent, so a new design was created [4]. One 32 bit number to describe the issue was used, on the pragmatic assumption that this would be large enough to cover foreseeable eventualities.*

*Yet the strains of one issuer, one currency were obvious almost immediately. A more advanced scheme could use a tuple of (issuer, currency) to describe a system whereby each issuer is empowered in some sense to issue multiple competing currencies [5]. It is easy to generalise this system by adding additional elements to the tuple: (issuer, type, identifier) tuple [6]. For example, a zero coupon bond issued by the Joint Universal and Nationwide Keiretsu that pays out in January of 2100 might have a tuple of (JUNK, zero, Jan_2100).*

**2.作为合约的价值问题**

**2.1 第一代计划**

考虑 DigiCash BV最初采用的开创性数字现金计划eCash的案例。美国马克吐温银行发行的第一个有价值的货币被确定为4号。知道早期的系统为每种货币分配了一个小的连续数字。测试系统已经获得了0,1,2,3，因此接下来的是4。DigiCash的策略为假设每个国家都是一个发行编号。随着时间的推移，该计划进行了调整，以发行按国际拨号代码编号的货币（例如，德国49，澳大利亚61）。这种方案的不足之处变得明显，因此创建了一个新的设计 [ 4 ]。在实用的假设中，一个32位的数字将大到足以涵盖可预见的可能性。

发行越多，只有一种货币不够用的压力很快就显而易见。一个更先进的方案可以使用（发行者，货币）元组来建立一个新的系统，每个发行者在某种意义上被授权发行多种竞争货币 [ 5 ]。通过向元组添加附加元素来简化这个系统：元组（发行者，类型，标识符） [ 6 ]。例如，由Joint Universal和Nationwide Keiretsu在2100年1月发行的兑付零息债券形成一个元组为（JUNK，0，Jan_2100）。

**2.2. The trouble with Numbers**

*Numbers as a space for identifying digital instruments are limiting, and having tuples as an extension is not really an answer.*

*Firstly, what do they describe? In the case of electronic cash systems, they can describe currencies and issuers. Is it one or both, and how do we generalise to other aspects? Secondly, what surety do we have that what is described is accurate? Whilst a lot can be achieved by simply relying on the reputation of the issuer, financial insiders know that the real value is expressed in the detail and the reliability of the claim. Thirdly, how are the numbers derived? Is a central registry required, or can any issuer of digital value acquire a number as per local requirements? Finally, is there a limit to the space? Integer numbers as expressed in packets are generally limited to some quantity of bits, such as 32. For practical software engineering, there need to be limits, but do these limits need to limit the business possibilities?*

**2.2 数字的麻烦**

数字作为识别数字工具的空间是有限的，而将元组作为扩展并不是真正的答案。

首先，他们描述了什么？在电子现金系统的情况下，它们可以描述货币和发行者。它是一个还是两个，我们如何概括其他方面？其次，我们用什么保证所描述的是准确的？虽然仅凭依赖发行人的声誉就可以实现很多目标，但财务内部人士知道，真正的价值体现在索赔的细节和可靠性上。第三，这些数字是如何得出的？是否需要一个中央注册机构，或者任何数字价值发行机构能否根据当地要求获取一个数字？最后，空间是否有限制？以数据包表示的整数通常限于一些bit，例如32。对于现实中的软件工程，需要有限制，但是这些限制需要限制业务的可能性吗?

**2.3. The Challenge of Success**

*Any successful system will be used in ways that make it appear to be broken. As software engineers, we need to present our inventions with the humility of toolmakers for future generations of builders, not as bureaucrats planning the zoning of the digital commerce space.*

*What happens when we have gone through the early adopters, dominated the moms and pops, and competition is fiercely turning onto our elderly retired set? Imagine mints in the pockets of billions of idle game-playing senior citizens. Or, imagine a world with an issuer of digital loyalty points on every parking meter, or where students must pay for tuition with shares of future earnings. Already we have seen popular musicians selling bonds backed by their music [7], and proposals for software bug fixes financed by securitized issues to anonymous users [8].*

**2.3 成功的挑战**

任何成功的系统都将以使其看起来被破坏的方式使用。作为软件工程师，我们需要向我们的下一代建造者展示工具制造者的谦逊，而不是规划数字商务空间分区的官僚。

当我们早期的采用者主宰了妈妈和流行音乐的内容，并且竞争激烈地转向了我们的退休老人组时，会发生什么？想象一下这个世界：数以亿计的闲暇游戏老人的口袋里的钱财，或者在每个停车计时器上都有一个数字忠诚点，又或者学生必须支付未来收入份额的学费。我们已经看到了流行歌手向粉丝销售某些金融债券 [ 7 ]，并提出了通过证券化问题为匿名用户提供资金软件缺陷修复的建议 [ 8 ]。

**2.4. The Zero Coupon Bond**

*Consider the zero coupon bond, an instrument that pays a face value of a currency on a given date. The zero is perhaps the simplest general financial instrument in common use, and it formed the benchmark for our design.*

*To describe the face value, the currency of the face value, and the expiry date of this bond, we would add additional elements to the above tuple. But this is only a beginning. In his description of Eurobonds, Noel Clarke expects dozens or hundreds of fields [9]. If we examine just one of these characteristics, for example Event-Related Put Options, we find that a bond needs to describe what happens in the event of:*

*a hostile or friendly takeover of the issuer,*

*a takeover by the issuer of another party,*

*a recapitalisation,*

*a repurchase program by the issuer of its own shares, or*

*a distribution of assets above a certain percentage of the issue's net worth.*

*These items bind tightly to the instrument in question, but they represent difficulties to the software architect. We can make a number of observations.*

*Firstly, each event is not simple. Today, one may be able to shoehorn the notion of "a hostile or friendly takeover" into a single name-value pair, but this would not survive the evolving scene of regulation and litigation that applies to such events.*

*Secondly, there is no reason to believe that the above list is complete.*

*Thirdly, not only is it going to be hard to design a single field of any sort to cope with these, they are mostly going to be full of legal text.*

*Consider a data layout point of view. To describe the document that forms the basis of a bond we will need a tree-structured database of tuples, as a minimum. More, that layout is only going to work for one instrument, or one extremely tight, nearly fungible set of instruments.*

**2.4 零息债券**

考虑零息债券，一种在给定日期支付货币面值的工具。这也许是广泛且最简单的金融工具，它是我们的设计基准。

为了描述面值，面值的货币和该债券的到期日期，我们会在上面的元组中添加额外的元素。但这只是一个开始。Noel Clarke在描述欧洲债券时预计有数十个或数百个领域 [ 9 ]。如果我们只考察其中一个特征，例如与事件相关的看跌期权，我们会发现债券需要描述在以下情况下会发生什么情况：

敌意或友善的发行人收购；

另一方的发行人收购；

资本重组；

发行人自己的股票回购计划；

或者超过净值一定比例资产分配。

这些情况密切反应在工具上，它们给软件架构师带来了困难。我们可以进行一些观察。

首先，每个事件都不简单。今天，人们可能会将 “敌对或友好收购” 的概念强加于单一的名称——价值对，但这无法适用于此类事件不断演变的法规和诉讼场景。

其次，没有理由相信上述清单是完整的。

第三，设计一个单一的领域来应对这些问题不仅很困难，而且他们大部分将会充满法律文本。

考虑数据布局的观点。为了描述构成债券基础的文档，我们至少需要一个树形结构的元组数据库。而且，这种布局只适用于一种工具，或者一种非常紧凑、几乎可以替代的工具。

**2.5. Cash is King**

*Currencies, or cash, might be that tight set. After all, a dollar is a dollar is a dollar. Can we describe money with some simple set of tuples? Even for cash, we argue that a layout of tuples is not sufficient.*

*Take the case of a digital dollar issued by a bank. The digital dollars would be derivatives, often backed by deposits in the same amount. This may be sufficient for marketing purposes but it would not survive a serious financial analysis.*

*Compare such derivative dollars to those issued by the US Federal Reserve Board. The Fed has yet to deny acceptance of its notes if presented with same, if only as a claim on another bunch of the same instrument, or for taxation liabilities. Radical interpretations aside, the Fed has never filed for bankruptcy and remains a pretty solid bet.*

*The same cannot be said of just any bank issuer of derivative dollars. Its digital dollars would be backed by deposits with ... the very same institution. Such a bank can close its doors at any time, and, given the history of the banking sector in the 20th Century, an analyst should take this risk seriously. Further, in the USA at least, the FDIC has already ruled that funds so held on a user's PC are considered to be uninsured deposits [10].*

*This is not to suggest that any given bank is about to close doors, but to ask what happens when an issuer does indeed default on its promise?*

*Any holder of any asset will carry a risk. A holder of electronic dollars will carry the risk that the issuer fails, and the holder of another issuer's dollars carries a similar, comparable, but distinct risk. Each of those risks result in a cost, which should be subtracted from the face value of the dollar to calculate a comparative value. In this risk distinction lies the inescapable fact that any given dollar is not of constant value, even when measured against some well-known dollar such as that issued by the Federal Reserve.*

**2.5 现金为王**

货币或现金可能就是那么紧张。毕竟，一美元始终只能是一美元。我们可以用一些简单的元组来描述货币吗？即使是现金，我们也认为元组的布局是不够的。

以银行发行的数字美元为例。数字美元将是衍生品，通常以相同数量的存款作为支持。这对于营销目的来说可能已经足够，但它不会在严肃的财务分析中生存。

相比之下，美国联邦储备委员会(Federal Reserve Board)发布的这类衍生品美元的价格是如此之高。如果它是相同的，只是作为对另一种相同工具的债权，或者是税收负债，美联储还没有拒绝接受它的票据。撇开激进的解释不谈，美联储从未申请破产，而且仍是一个相当可靠的赌注。

任何衍生品美元的银行发行人也不能这样说。它的数字美元将得到与......相同机构的存款支持。鉴于20世纪银行业的历史，这样的银行可以随时关门，分析师应该认真对待这种风险。此外，至少在美国，FDIC已经判定这样持有用户PC上的资金被认为是没有保险的存款 [ 10 ]。

这并不是说任何给定的银行即将关门，而是要问当发行人确实违约时会发生什么？

任何资产的任何持有人都将承担风险。电子货币持有人将承担发行人失败的风险，另一个发行人的美元持有人也承担类似可比较但独特的风险。每种风险都会产生成本，应该从美元面值中扣除成本来计算比较价值。在这种风险区分中存在一个不可避免的事实，即任何给定的美元都不具有恒定的价值，即使是用美联储发行的一些众所周知的美元来衡量。

**2.6. The Fine Print of the Contract**

*If there is no such thing as a single dollar, what is left? Clearly, we must describe each and every dollar for what it is. This would seem to be a task of fine print and detail, and, indeed, every distinct issued currency is a distinct contract between the issuer and the holder.*

*A contract can encapsulate the detail. Consider the original sovereign currency contracts, in which the issuer promised to pay the bearer in ounces of precious metal. That is four datum in the contract already: which sovereign, "pay to bearer," what to pay, and how much of it.*

*So it is with every bond, every currency, and any financial instrument of any complexity In fact, within the digital domain, the question of how to treat a financial instrument reduces in great part to how to treat a contract.*

*Or, an issue is a contract. Issues within other payment systems have contracts but only as adjunct documents such as user agreements. Often, their role and importance is subject to battles; Marketing wants them hidden, while Legal asks for them to be thrust in the user's face at all times.*

*Once we accept that the issue is a contract, the task becomes simple: create a contract that can be linked into the payment system as the centerpiece. That is the subject of the next section.*

**2.6 合约的细则**

如果没有美元这样的东西，那有什么？显然，我们必须描述每一个美元是什么。这似乎是一个细则和细节的任务，而且实际上， 每一种不同的发行货币都是发行人和持有人之间的明确合约。

合约可以概述细节。考虑原始主权货币合约，其中发行人承诺以每盎司贵金属支付给持有人。这是合约中的四个数据：谁是主权，“支付给谁”，支付什么，以及数量多大。

因此，每种债券、每种货币和任何复杂的金融工具都是如此。实际上，在数字领域，如何对待金融工具的问题在很大程度上减少了如何处理合约这个问题。

或者，一个发行物就是一个合约。其他支付系统中的发行物有合约，但只作为用户协议等辅助文件。他们的角色和重要性往往受到战争的影响; 市场营销部门希望他们隐藏起来，而法律部门则要求他们随时都能反应在用户的身上。

一旦我们接受这个发行物是一个合约，任务就变得简单了：创建一个可以链接到支付系统的合约作为核心。这是下一节的主题。

**3. A Digital Contracts System for Issuance**

*Almost all aspects of Ricardian Contracts are best seen by examining examples, and this section only briefly covers the salient details, before discussing the ramifications. Examples can be found atwebfunds.org/ricardo/contracts/ .*

**3. 发行数字合约制度**

李嘉图合约几乎所有内容都可以通过检验例子来展示，本节仅简要介绍明显的细节，然后再讨论分支。例子可以在 <http://webfunds.org/ricardo/contracts/> 找到 。

**3.1. Definition**

*A Ricardian Contract can be defined as a single document that is a) a contract offered by an issuer to holders, b) for a valuable right held by holders, and managed by the issuer, c) easily readable by people (like a contract on paper), d) readable by programs (parsable like a database), e) digitally signed, f) carries the keys and server information, and g) allied with a unique and secure identifier.*

*In the simplest possible terms, a Ricardian Contract is a document defining a type of value for issuance over the Internet [11]. It identifies the Issuer, being the signatory, and any terms and clauses the Issuer sees fit to add in to make the document stand as a contract.*

*The same document has to be both readable by people and parsable by programs. The Ricardian Contract is formatted as a text file that can be easily read (displayed or printed), and programs can convert it into internal forms for searching for name-value pairs. It includes a special section for each type of contract, such as bond, share, currency, etc. Further sections within describe, in program-parsable terms, usage of decimal points, titles, and symbols.*

*As legal signatory, the Issuer signs the document in the OpenPGP cleartext form with his contract signing key [12]. He includes the full chain of OpenPGP keys within the document to permit programs to directly verify and authenticate.*

*To uniquely identify the contract, any user can calculate a canonical message digest over the clearsigned document. This message digest is included in all records of transactions, and provides a secure (unforgeable) link from the document to the accounting of the issue.*

*E.g. e3b445c2a6d82df81ef46b54d386da23ce8f3775 is the full message digest for Systemics Inc's issue of prepaid services dollars. Commonly called a hash, the message digest is a cryptographic technique to create a relatively small number that is one to one with the document. That is, for each document, there is only one hash, and the hash refers uniquely to that document. The algorithm is the well-known standard, SHA1.*

**3.1 定义**

李嘉图合约可以被定义为一个文件，即a）发行人向持有人提供的合约，b）由持有人持有并由发行人管理的有价值的权利，c）人们易于阅读的文件（如合约），d）程序可读（数据库可解析），e）数字签名，f）携带密钥和服务器信息，g）与唯一安全的标识符结合。

用最简单的术语来说，李嘉图合约是一种定义了通过互联网发行的价值类型的文件 [ 11 ]。它标识发行人、签署人以及发行人认为适合添加的任何条款和条款，从而让该文件成为合约。

相同的文档必须能够被人读取，并可以被程序解析。李嘉图合约被格式化为可轻松阅读（显示或打印）的文本文件，程序可将其转换为用于搜索名称 - 值对的内部表格。它包括每种类型合约的特殊部分，例如债券，股票，货币等。其他部分用程序可解析的术语描述小数点、标题和符号的用法。

作为法定签字人，发行人用其合约签署密钥以 OpenPGP 明文形式签署文件 [ 12 ]。他在文档中包含了完整的 OpenPGP 密钥链，以允许程序直接验证和认证。

为了唯一标识合约，任何用户都可以在清单文件上计算“规范的消息摘要”。此消息摘要包含在所有交易记录，并提供从文档到问题记录的安全（不可伪造的）链接。

例如， e3b445c2a6d82df81ef46b54d386da23ce8f3775 是 Systemics Inc 预付费服务美元的完整信息摘要。通常称为哈希，这种消息摘要是一种加密技术，用于创建一个相对较小的、与文档一对一的数字。也就是说，对于每个文档，只有一个哈希，并且该哈希只指向该文档。该算法SHA1是众所周知的标准。

**3.2. Some Observations**

*The following observations highlight how strong the result is.*

*Hash Limits Frog-Boiling. A gradual change in contract by the stronger party over time is known as frog-boiling. The stronger party is generally the issuer, and can be expected to change the contract if there is a benefit. This is a frequent attack. One result of the use of the hash identifier is that neither party can change the contract arbitrarily or surreptitiously.*

*To see this is true, we need to examine the records that refer to the hash. An application can sign all important records (e.g., payments, tokens, receipts, balances), and these signed records include the hash of a Ricardian Contract. The hash within the record cannot be changed without losing its ability to pass a test of signature validity. Likewise, the contract cannot be changed without losing its relationship to records already signed and delivered. In other words, every record, held by every user, incorporates an unalterable copy of that hash. Any change to the contract creates a new hash, and that new hash is not the one which the users have or value.*

*This crystallises the contract for both parties, stopping the stronger party from modifying the contract subtly at some later stage. To some extent, this redresses the imbalance of power between provider and customer in the offering of a form contract. The lesser party has no option to negotiate, but neither has the greater party the option to claim a distinct contract at a later time. The limitation comes at some cost as it can be a nuisance for the support team of that financial instrument.*

*The Ricardian PKI Delivers Clarity. Ricardian Contracts carry their own Public Key Infrastructure ("PKI") with them. The Issuer's top level public key is included in the contract, and it signs his contract-signing key, also included. The contract-signing key signs the contract itself.*

*This achieves several things. Firstly, client software can check the entire digital signature chain in one automated sequence.*

*Secondly, there is no need for a complex multi-party PKI. All the keys are present, and there is no need to go looking for them on the net. This eliminates substitution attacks, whereby a key that might pass some checks could be inserted in some key lookup phase. It also reduces costs dramatically.*

*Thirdly, the canonical hash of the contract also represents a signature on the contract. It is recorded in all relevant records, and thus entangles the contract with those activities [13]. Once the contract has been in play for a while, it establishes its provenance through presence and reliance by the user public. This provides far more persuasive evidence than the issuer's signature itself; once the issuer and the public have spent time and money relying on the contract, via the hash, it is hard for the issuer to renege on the nature of the contract or his signature.*

*The result is a PKI that delivers strong end-to-end reliability, based on a single document. This is simply not present in other designs for PKIs [14]. This reliability pays off in the dispute resolution phase, where, we suggest, the Ricardian Contract can stand alone on its merits and requires no complex descriptions of PKI, digital signatures, or references to uncertain third parties to bolster its provenance. By including the keys, we can draw a couple of simple lines within the contract, asserting "this key signs that key, and that latter signs the contract. The first key is the top-level key of the individual that signed this contract. That's the whole story, mi'lud."*

*Validating the Issuer's Key. All good crypto protocols divide into two parts, the first of which says to the second, "trust this key completely."*

*The top-level key of the Issuer ultimately authenticates the contract. The keys and other information in the contract also permit a protocol such as SOX to bootstrap a strongly secured connection to the server [15].*

*How then to verify that this ultimate key is really the Issuer's? This is not difficult. The business process of digital issuance involves a great deal of relationship-building between Issuers and Users. Many different interactions involve chances to establish trust. For example, from his web site, the Issuer can publish the contract, keys and hashes, and have other sites mirror them. The value so issued will be distributed via payments that include the hash. An already trusted party usually delivers these payments. The payments validly identify the contract, and derive their own validity, via the hash.*

*Contrast this to assumptions in the x.509 PKI behind SSL/HTTPS browsing (the following is highly debatable, but is presented for comparison only). In that PKI, it was originally claimed that a user would present her credit card to sites with which she had no prior relationship and no way for her to establish the provenance of the site's key. Thus, a trusted third party, the Certificate Authority, was put in place to confirm the key.*

*Payments, trading and matters of finance are fundamentally relationship-rich. The nature of money and finance is that participants always conduct their own due diligence, they prefer to listen to peers they already trust, and do not readily accept the word of an independent party. Thus, there is no place for a central third party to stand in and authenticate players. Before the user desires to place any value on a given payment, she has almost certainly been made aware of the contract via other means.*

*Presumption of Possession. The use of the hash as an identifier is a compromise as it is unintelligible to humans [16]. Yet this very compromise delivers an unexpected benefit: Use of the issue leads to a presumption that the user has the contract. To use an issue of value, such as a currency, the user must have the hash in the applicable records. That is, if the user receives a payment, that payment record will include the hash. As the hash is not descriptive, this implies that the user has the contract in order to interpret the issue.*

*To see that this is true, imagine having a record with the hash but without having the contract. The first thing the user will need is a database of parameters telling her what the hash refers to. Unlike a payment in 10 of "GBP", a payment of 1000 in "972097bb..." is not intelligible.*

*Yet how could software predict what the user needs to know about the hash? Very quickly it becomes apparent that the software is better off storing the source of the information - the full contract itself - as it removes an unlimited degree of complexity in storing intermediate or secondary information.*

*Software can still function with only the hash. However, it would be entirely blind to the semantics of the instrument. Such a cavalier approach might be acceptable for communications and storage, but for user software, it is equivalent to a traumatic failure. To cope with this, the client-side software takes especial care to acquire and keep contracts. Hence, we can state the presumption with some degree of confidence: in a functioning system, the user has available the full Ricardian Contract (albeit under software control).*

*This is only a small step for the client software, but is a giant leap forward for the relationship between the issuer and the holder. Specifically, having a strong presumption that the user has the full contract available will simplify many legal aspects about the issuer's responsibilities. (We suggest and thus acknowledge the legal ramifications of the term presumption, but neither space nor expertise permits more in this paper.)*

**3.2 一些观察**

以下观察突出了结果的强度。

哈希限制Frog-Boiling。随着时间的推移，实力较强的一方的合约逐渐发生变化，被称为“frog-boiling”。较强的一方通常是发行者，如果有利益，可以期望变更合约。这是一次频繁的攻击。使用哈希标识符的一个结果是，任何一方都不能任意或秘密地更改合约。

为了证实这是真的，我们需要检查引用哈希的记录。应用程序可以签署所有重要记录（例如付款、代币、收据、余额），这些签名记录包含李嘉图合约的哈希。如果失去通过签名有效性测试的能力，记录中的哈希不能被改变。同样，如果与已经签署和交付记录的关系存在，合约就不能改变。换句话说，每个用户拥有的每一个记录都包含了不可更改的哈希副本。对合约的任何更改都会创建一个新的哈希（不是用户拥有或评估的）。

这为双方制定了合约，阻止了强大的一方在稍后的阶段巧妙地修改合约。在某种程度上，这纠正了提供表格合约的供应商与用户之间权力的不平衡。较小的一方没有选择进行谈判的权利，但是较大的一方也不可以在后面申请一项独立的合约。这种限制是有一定代价的，因为这对金融工具的支持团队来说可能是一个麻烦。

李嘉图PKI提供清晰。 李嘉图合约带有自己的公钥基础设施（“PKI”）。发行人的顶级公钥包含在合约中，也包含签署了合约签名密钥。合约签字秘钥需要自己签署。

这实现了几件事情。首先，客户端软件可以在一个自动序列中检查整个数字签名链。

其次，不需要复杂的多方PKI。所有秘钥都存在，并且不需要在网上寻找它们。这消除了替换攻击，由此可以在某个关键查找阶段插入可能通过一些检查的关键字，大大降低了成本。

第三，合约的规范哈希也代表合约上的签名。它记录在所有相关记录中，从而使合约与这些活动相关联 [ 13 ]。一旦合约生效了一段时间，它就通过用户公众的存在和依赖来确定其来源。这比发行人的签名本身提供了更有说服力的证据; 一旦发行人和公众因为合约花费了时间和金钱，发行人很难通过哈希违背合约的性质或签名。

其结果是基于单个文档的PKI提供了强大的端到端可靠性，这在PKI的其他设计中根本不存在 [ 14 ]。这种可靠性在争议解决的阶段得到了回报，我们认为，李嘉图合约可以独立于其优点，不需要对PKI、数字签名或对不确定第三方的引用进行复杂的描述以支持其来源。通过把秘钥包括在内，我们可以在合约中画出几条简单线条，断言：“这把秘钥签署着另一把秘钥，而后者签署合约，第一个秘钥是签署本合约的个人的顶级秘钥。这就是故事的全部内容。"

验证发行人的密钥。 所有好的加密协议分为两部分，第一部分对第二部分说“完全信任这个密钥”。

发行人的最高级别密钥的最终验证合约中，密钥和其他信息也允许像SOX这样的协议将一个强安全连接发送到服务器[ 15 ]。

那么如何验证这个最终的秘钥是发行人的呢？这并不困难。数字发行的业务流程涉及建设发行人和用户之间的大量关系，许多不同的互动涉及建立信任的机会。例如，在他的网站上，发行人可以发布合约、密钥和哈希值，并让其他站点对其进行镜像。这样发布的价值将通过包含哈希的付款进行分配，已经信任的一方通常会提供这些付款。付款有效识别合约，并通过哈希衍生自己的有效性。

与SSL / HTTPS浏览背后的x.509 PKI假设相比（以下内容具有很大的争议性，但仅供比较），在该PKI中，它最初声称用户会将自己的信用卡出示给她之前没有任何关系的站点，并且无法确定该站点密钥的出处。因此，一个受信任的第三方，即证书颁发机构来确认密钥。

支付、交易和财务事宜从根本上来说是关系丰富的。金钱和金融的本质是参与者总是进行自己的尽职调查，他们更愿意倾听已经信任的同事，而不愿意接受独立的一方。因此，没有一个地方可以让一个中心化的第三方来支持和认证玩家。用户希望在给定付款上有任何价值之前，通过其他方式了解合约。

占有的推定。 哈希作为标识符的使用是一种妥协，因为人类无法理解 [ 16 ]。然而，这种妥协带来了意想不到的好处： 使用该问题会导致用户拥有合约的推定。 要使用价值发行物（如货币），用户必须在可应用的记录中包含哈希。也就是说，如果用户收到付款，该付款记录将包含哈希。由于哈希不是描述性的，这意味着用户拥有合约来解释问题。

为了证明这是真的，假设有一个没有合约的哈希记录，用户首先需要的是一个参数数据库，告诉她哈希是什么。与10英镑的“GBP”付款不同，“972097bb ...”中的1000付款不易理解。

然而，软件如何预测用户需要了解哈希的内容？很快就会发现，软件最好将信息的来源——完整的合约存储起来——因为它可以在存储中间信息或辅助信息时移除不受限制的复杂性。

软件仍可以仅使用哈希运行。但是，这完全是盲目的文书的语义。这种傲慢的做法对于通信和存储来说可能是可以接受的，但对用户软件来说，这相当于创伤性失败。为了应对这种情况，客户端软件需要特别注意获取并保存合约。因此，我们可以有一定程度的信心陈述推定：在一个运作良好的系统中，用户可以使用完整的李嘉图合约（尽管在软件控制下）。

具体来说，有一个强大的假设，即用户拥有完整的合同可以简化许多关于发行人责任的法律方面(我们建议并因此承认“假设”的法律后果，但在本文中，空间和专业知识都不允许)。

**3.3. The Four Corners of the Page**

*The Ricardian Contract delivers a rich source of primary, complete information. The full story is right there in textual form, in parsable parameters, and in the signature chain. Thus, within a dispute, a hostile legal attack has less room to manoeuvre, and can only confirm the facts as laid out in the contract.*

*Our intent is that the contract is the beginning and the end of the discussion; we call this principle the rule of one contract. The legal fraternity refers to "the contract being bounded by the four corners of the page." By showing how we have carefully laid out a readable document, with a verifiable digital signature, and an unforgeable identifier linking to every record, we can more readily ask the judiciary to accept that the single document which is being presented is indeed the valid contract agreed to by the parties.*

**3.3 页面的四个角落**

李嘉图合约提供了丰富的原始信息。完整的故事以文本形式出现在可解析的参数和签名链中。因此，在争议中，敌对的法律攻击的回旋余地较小，只能确认合约中规定的事实。

我们的意图是，合约是讨论的开始和结束; 我们把这个原则称为一个合约的规则。法律是指“合约以页面的四个角落为界 ”。通过展示我们认真制定的一个可读文档，带有可验证的数字签名以及与每条记录链接的不可伪造的标识符，我们可以更容易要求司法部门接受所提交的单个文件确实是由各方同意的有效合约。

**4. Conclusion**

*The contract is the keystone of issuance [17]. Our innovation is to express all the salient details of an issuance as an unforgeable contract, unforgeably linked into every action within a payment system. In this way, financial innovation can develop along the lines it always has done - by means of innovation within contracts. By translating the institution of the contract into the digital domain, we build upon centuries' and even millenia' worth of experience in documenting, sharing and disputing the meaning of agreements between parties.*

**4. 结论**

合约是发行的基石 [ 17 ]。我们的创新是将发行的所有重要细节表达为不可伪造的合约，不可避免地与支付系统内的每一个行动联系起来。通过这种方式，金融创新可以沿着它始终完成的路线发展——通过合约之内的创新。通过将合约制度转化为数字化领域，我们建立了几个世纪甚至千年的记录，分享和争论各方之间协议意义的经验。

**4.1. The Challenge of Complexity**

*To capture complexity, we can put documents such as contracts into electronic form and sign them using digital signature technologies such as OpenPGP. The result is a reasonable analogue of the paper and ink contracts that most people and businesses are familiar with, bolstered with cryptographic integrity.*

*With the hash as the identifier, software can now uniquely identify a given financial arrangement and can confirm a strong chain of signatures. The hash strongly implies the user has the contract available at all times, and it cannot be changed without being noticed.*

*The Ricardian Contract delivers one huge benefit to the issuer - clarity in many legal and customer support questions. The user benefits from lower overall costs, and better presentation of information, within a more consistent framework.*

**4.1 复杂性的挑战**

为了捕捉复杂性，我们可以将合约等文档转换为电子格式，并使用OpenPGP等数字签名技术对其签名。其结果是大多数人和企业都熟悉的纸张和墨水合约的合理模拟，并具有密码完整性。

以哈希作为标识符，软件现在可以唯一地识别给定的财务安排，并且可以确认强大的签名链。哈希强烈暗示用户始终有合约可用，并且不会被发现而改变。

李嘉图合约为发行人带来了巨大的收益——明确了许多法律和客户支持问题。用户可以从更低的总体成本中受益，并且可以在更一致的框架内更好地呈现信息。

**4.2. Lessons Learnt**

*The form has been in successful use since 1996. Since that time, it has delivered about 20 financial instruments without failure.*

*Disputes. The Ricardian Contract has appeared in two distinct forums of dispute resolution to resolve claims [18]. Anecdotally, each claim was resolved directly and efficiently, and without undue fuss, simply by referring to the applicable Ricardian Contract.*

*Automation. Relatively little has needed to be automated. In practice, fields have been inserted and standardised so that programs can extract decimalisation (dollars versus cents), labels for units (USD versus $), and titles for the issuer and the issue. In contrast to expectations, there has been no demand to parse every field.*

*Cost. The cost of the concept has compared favourably with that incurred with other payment systems. The preparation of the contract text carries some costs, but no more so than a user agreement. OpenPGP infrastructure requirements (keys and signing) add some minor costs to issuers but they are easily offset by the benefits of risk reduction from contract distribution. Custom signing editors have helped to reduce those costs[19].*

**4.2 经验的学习**

该表格自1996年以来一直在成功使用。至今，它已交付约20种金融工具而没有失败。

争议： 李嘉图合约出现在两个不同的争议解决论坛上以解决索赔 [ 18 ]。有趣的是，每一项索赔都是直接而有效地解决的，不需要太多的争执，只需参考适用的李嘉图合约即可。

自动化： 需要自动化的东西相对较少。在实践中，字段被插入并标准化，以便程序可以提取十进制（美元与美分）、单位标签（美元与美元）以及发行人和发行人的头衔。与预期相反，没有要求解析每个领域。

成本： 这个概念的成本与其他支付系统的成本来说相对有利。合约文本的准备会带来一些成本，但不会超过用户协议。OpenPGP基础设施要求（密钥和签名）为发行人增加了一些小的成本，但很容易被合约分配降低风险的好处所抵消。定制签名编辑有助于降低这些成本 [ 19 ]。

**4.3. Challenges for the Future**

*Layering. Layering of contracts is an impending need. Many businesses can take a standard and defined set of terms and draw on them directly. Other contracts result from earlier contracts and need to reference them.*

*XML. Initial efforts suggested that XML would break the rule of one contract, but it seems that we will need something better than the archaic INI format [20]. One recent proposal, the XML Voucher, stops short of presenting itself as a contract [21].*

*Law of Contract. The treatment of the Ricardian Contract as a contract may raise more legal questions than it answers. For example, is this form indeed a contract? How do distinct jurisidictions view the concept (common law, civil law, UCC, Koranic code)? Is this a negotiated or a form contract? When did the user accept the contract? How strong, or rebuttable, is the presumption that the user has the contract?*

*Smart Contracts. By unifying all information in a program-readable file, there is the enhanced potential of smart contracts [22]. We have not gone further in this direction than methods to handle decimals. This is partly for lack of demand, and partly because it is not clear how a court would treat a computer program presented as a contract.*

**4.3 对未来的挑战**

分层: 合约的分层是一个迫在眉睫的需要。许多企业可以采用标准和定义的术语集并直接使用它们。其他合约来自早期合约，需要引用它们。

XML: 最初的努力表明，XML将打破一个合约的规则，但似乎我们需要比陈旧的INI格式更好的东西 [ 20 ]。最近的一个提案，即XML凭证，并没有将自己作为一份合同呈现出来 [ 21 ]。

合约法: 李嘉图合约作为“合约”的处理方式可能会引发比答案更多的法律问题。例如，这种形式确实是合约吗？独特的法理学如何看待这个概念（普通法，民法，UCC，古兰经代码）？这是谈判或表格合约吗？用户何时接受合约？用户拥有合约的假设有多强或可以反驳？

智能合约: 通过将所有信息统一到一个可编程的文件中，智能合约的潜力得到增强 [ 22 ]。在这方面，我们并没有比处理小数的方法更有进步。部分原因在于缺乏需求，或者是法院如何对待作为合约提交的计算机程序尚不清楚。

**5. References**

*[1] Originally introduced in Ian Grigg, "Financial Cryptography in 7 Layers," 4th Conference on Financial Cryptography, Anguilla, 2000, Springer-Verlag LNCS 1962. All papers are at <http://iang.org/papers/> *

*[2] Ian Grigg, "Digital Trading," Virtual Finance Report, November 1997. *

*[3] Country and Currency Codes, ISO3166-1. *

*[4] Bryce Wilcox, open design review, DigiCash's developer list, [ecash-dev@digicash.com](https://mailto:ecash-dev@digicash.com/), August 1997. *

*[5] Ibid, Rachel Willmer, 14 August 1997. *

*[6] Robert Hettinga, " What's a Digital Bearer Bond?" e$ rants , 19th November, 1995 *

*[7] Alex Tajirian, " David Bowie Bonds," *

*[8] Ian Grigg and C. Petro, "Using Electronic Markets Achieve Efficient Task Distribution," 1st Conference on Financial Cryptography , Anguilla, 1997, Springer-Verlag LNCS 1318. *

*[9] Noel Clarke, Guide to Eurobonds, The Economist Intelligence Unit, 1993. *

*[10] FDIC General Counsel's Opinion No. 8; Stored Value Cards, Federal Register, August 2, 1996. Also see the (readable) Press Release entitled FDIC will Continue to rely on General Counsel Opinion rather than issue rules on Stored-Value Cards, 24 June 97. *

*[11] Ian Grigg, Guide to Ricardian Contracts, WebFunds project. *

*[12] Jon Callas, et al, "OpenPGP Message Format," Internet Draft, RFC2440bis (-10 draft). *

*[13] Petros Maniatis, Mary Baker "Secure History Preservation through Timeline Entanglement" , 11th USENIX Security Symposium, San Francisco, USA. August 2002. *

*[14] Jane K. Winn, " Couriers without Luggage" 49 South Carolina Law Review 739 (1998) *

*[15] Gary Howland, "Development of an Open and Flexible Payment System" 1996. *

*[16] Bryce Wilcox, "Names: Decentralized, Secure, Human-Meaningful: Choose Two", 2003 *

*[17] Metaphor by Martin (Hasan) Bramwell. See "The Contract is the Keystone of Issuance," Financial Cryptography blog, 19th September 2003. *

*[18] DigiGold v. Systemics, before the Supreme Court of Anguilla (2001), and thereafter referred to the American Arbitration Association (2002). *

*[19] Edwin Woudt, ContractSignWizard, WebFunds project. *

*[20] Erwin van der Koogh, "Ricardian Contracts in XML," (presented at) Edinburgh Financial Cryptography Engineering (EFCE-2), 2001. *

*[21] Ko Fujimura and Masayuki Terada, XML Voucher: Generic Voucher Language, Internet Draft. *

*[22] Nick Szabo, " The Idea of Smart Contracts," 1997.*

------

本文原文链接为<http://iang.org/papers/ricardian_contract.html> ，作者Ian Grigg，译者Fred，校对Lochaiching。转载请参照本文文首说明。
