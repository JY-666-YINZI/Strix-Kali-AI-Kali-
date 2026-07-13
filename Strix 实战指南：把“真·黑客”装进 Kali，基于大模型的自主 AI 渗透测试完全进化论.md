<font style="color:rgb(36, 41, 47);"></font>

<font style="color:rgb(36, 41, 47);">Strix 是行为和</font>**<font style="color:rgb(36, 41, 47);">真实黑客一模一样的自主AI代理</font>**<font style="color:#DF2A3F;">——</font><font style="color:rgb(36, 41, 47);">它们</font>**<font style="color:rgb(36, 41, 47);">动态运行</font>**<font style="color:rgb(36, 41, 47);">你的代码，</font>**<font style="color:rgb(36, 41, 47);">发现漏洞</font>**<font style="color:rgb(36, 41, 47);">，并通过实际概念</font>**<font style="color:rgb(36, 41, 47);">验证（PoC）验证漏洞</font>**<font style="color:rgb(36, 41, 47);">。它专为需要快速、准确安全测试的开发人员和安全团队打造，</font>**<font style="color:rgb(36, 41, 47);">无需手动</font>**<font style="color:rgb(36, 41, 47);">渗透测试的额外开销，也</font>**<font style="color:rgb(36, 41, 47);">不会像静态分析工具那样产生大量误报</font>**<font style="color:rgb(36, 41, 47);">。</font>

****

**（↓****<font style="color:#DF2A3F;">安装</font>****↓）**

# windows：ᴺᵒ ʳᵘˢʰ


# Linux非企业版安装及操作：（kali）BB教程
## <font style="color:#1DC0C9;">1</font>.本机下载
[https://gitcode.com/GitHub_Trending/strix/strix/?utm_source=gitcode_aigc_v1_t0&index=top&type=card&&uuid_tt_dd=10_37470957630-1781750863573-656892&isLogin=9&from_id=154807907&from_link=5b155bd21a64eb4335dd6f2811da7f83](https://gitcode.com/GitHub_Trending/strix/strix/?utm_source=gitcode_aigc_v1_t0&index=top&type=card&&uuid_tt_dd=10_37470957630-1781750863573-656892&isLogin=9&from_id=154807907&from_link=5b155bd21a64eb4335dd6f2811da7f83)

然后**拖进kali，解压**。

## <font style="color:#1DC0C9;">2</font>.安装语言环境^^
**sudo apt install -y python3 python3-pip python3-venv**安装语言环境。（可能报错某几个会连接不到，需要在后面加参数--fix-missing）

**sudo apt install -y python3 python3-pip python3-venv --fix-missing**

## <font style="color:#1DC0C9;">3</font>.安装python包packages
**cd /home/zss/strix-main	**先切到strix-main目录下进行下一步

在这个目录下安装python的包packages： **pip3 install -e . --break-system-packages**

****

（注意如果有大片红字只是告警不用慌！虽然满屏幕红字看着吓人，但请注意最开头的一句话：

`ERROR: pip's dependency resolver does not currently take into account...`

这其实是 `pip` 的一个**警告/冲突提示**，意味着 **Strix 本身已经安装成功了**！）



（如果报错，尝试加参数--ignore-installed rpds-py）

**pip3 install -e . --break-system-packages --ignore-installed rpds-py**

****

## <font style="color:#1DC0C9;">4</font>.运行（但是第一次会很慢）：
**strix --help弹出strix帮助菜单	**看结果是否会爆出长串字符。

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782211613644-ffe4c2b6-d38b-4cb5-9ac6-6918032546ee.png)

## <font style="color:#1DC0C9;">5</font>.配置（因为strix是多功能集成并且<font style="color:rgb(36, 41, 47);">和真实黑客一模一样的自主AI代理</font>）
**1.export STRIX_LLM="openai/deepseek-chat"**	（**<font style="color:#DF2A3F;">""</font>**里面是服务商/大模型，选择的一个AI，比如openai/gpt-5；具体名称要在购买完的大模型看，<font style="color:#DF2A3F;">如果是中转那也尽量用openai/</font>）

**2.export LLM_API_KEY="你的密钥"	**（**<font style="color:#DF2A3F;">""</font>**里面是**购买后获得的key**，需要通过key来使用对应的大模型）

（**export LLM_API_KEY="**s*-***************************************"）



**3.export STRIX_API_BASE="https://**后台提供的中转接口地址/v1"  **这个是如果有中间商而不是直接官网购买的要填写中间商地址**；这个用于local models部署，配合"openai/你的大模型"。（****<font style="color:#DF2A3F;">由于第三方中转站也是属于local models，所以不用特定服务商，而是统统基于openai</font>****）**

（比如**图书馆:export STRIX_API_BASE="https://api.**/v1"）



**4.export STRIX_REASONING_EFFORT="high" 或者quick设置扫描方式**

****

**5.strix --target **[**https://**](https://47.110.93.100)**testip **（target后填写**渗透测试目标ip**<font style="color:#DF2A3F;">：</font>如果是http就+http头部协议，https同理<font style="color:#DF2A3F;">；</font>如果两个如果不填端口默认分别是80/443<font style="color:#DF2A3F;">；</font>需要改写端口在后面加比如*.*.*.*:8080**<font style="color:#DF2A3F;">；</font>**如果要**全端口/主机渗透测试**直接填写ip比如**.**.**.**，strix会先进行启动类似nmap工具全面扫描该 IP 开放了哪些端口和服务，再展开后续攻击）（前提是：<font style="color:#DF2A3F;">！！！确定目标，获取授权！！！</font>）





**6.**如果网速问题：（export http_proxy=[http://192.168.物理机ip:7890](http://192.168.7.49:7890)

   export https_proxy=[http://192.168.物理机ip:7890](http://192.168.7.49:7890)）虚拟机开代理



**7.export STRIX_REASONING_EFFORT="high"**  

调整模式，你可以修改为以下任意一种（此处借鉴ai生成）

+ **日常极速测试（省钱、看下有没有低级漏洞）**：
+ 扫描模式：`quick`
+ 脑力配置：`medium` 或 `none`
+ **全面挖洞、死磕 WAF 绕过（极限测试）**：
+ 扫描模式：`deep`
+ 脑力配置：`high`（用 `GLM-5.2` 的高智商去拆解对方的防御机制）

**<font style="color:rgb(36, 41, 47);">推荐模型，获得最佳效果：</font>**

+ [<font style="color:rgb(9, 105, 218);">OpenAI GPT-5</font>](https://openai.com/api/)<font style="color:rgb(36, 41, 47);"> </font><font style="color:rgb(36, 41, 47);">—</font><font style="color:rgb(36, 41, 47);"> </font>`<font style="color:rgb(199, 37, 78);background-color:rgba(175, 184, 193, 0.2);">openai/gpt-5</font>`
+ [<font style="color:rgb(9, 105, 218);">Anthropic Claude Sonnet 4.6</font>](https://claude.com/platform/api)<font style="color:rgb(36, 41, 47);"> </font><font style="color:rgb(36, 41, 47);">—</font><font style="color:rgb(36, 41, 47);"> </font>`<font style="color:rgb(199, 37, 78);background-color:rgba(175, 184, 193, 0.2);">anthropic/claude-sonnet-4-6</font>`
+ [<font style="color:rgb(9, 105, 218);">Google Gemini 3 Pro Preview</font>](https://cloud.google.com/vertex-ai)<font style="color:rgb(36, 41, 47);"> </font><font style="color:rgb(36, 41, 47);">—</font><font style="color:rgb(36, 41, 47);"> </font>`<font style="color:rgb(199, 37, 78);background-color:rgba(175, 184, 193, 0.2);">vertex_ai/gemini-3-pro-preview</font>`

<font style="color:rgb(36, 41, 47);"></font>

<font style="color:rgb(36, 41, 47);">如需查看所有支持的服务商（包括Vertex AI、Bedrock、Azure和本地模型），请查看</font>[<font style="color:rgb(9, 105, 218);">大语言模型服务商文档</font>](https://docs.strix.ai/llm-providers/overview)**<font style="color:rgb(36, 41, 47);">↓↓↓</font>**<font style="color:rgb(36, 41, 47);">。</font>

**<font style="color:rgb(36, 41, 47);">支持的服务商（同一个服务商可选择不同版本大模型尝试）：</font>**

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782214322561-e8eea7e6-f7d9-4eb7-ab5f-476cd67bd828.png)

**<font style="color:rgb(36, 41, 47);">注意：图中没出现的大模型未尝不可↓↓↓</font>**

**<font style="color:rgb(36, 41, 47);">1.因为OpneRouter：</font>**<font style="color:rgb(36, 41, 47);">不是和其他一样是具体的服务商，而是指</font>**<font style="color:rgb(36, 41, 47);">大模型聚合服务商</font>**<font style="color:rgb(36, 41, 47);">（ 支持超过 100 种大模型通过同一个接口访问 ）。</font>**<font style="color:rgb(36, 41, 47);">最重要的是</font>**<font style="color:rgb(36, 41, 47);"> 还能调用诸如</font>**<font style="color:rgb(36, 41, 47);"> DeepSeek</font>**<font style="color:rgb(36, 41, 47);">、</font>**<font style="color:rgb(36, 41, 47);">Qwen</font>**<font style="color:rgb(36, 41, 47);">（通义千问）、</font>**<font style="color:rgb(36, 41, 47);">GLM</font>**<font style="color:rgb(36, 41, 47);">（智谱，最近上新glm</font>开源最强模型glm-5.2已上架，说是**性能直逼claude-4.8-opus，性价比极高，国产Coding之王**，但是相比其他还是”**略贵**“我还**没进行测试**<font style="color:rgb(36, 41, 47);">）等各种好用的国内外模型，省去了去每个平台挨个注册账号的麻烦。</font>

<font style="color:rgb(207, 34, 46);background-color:rgb(11, 12, 14);">export</font><font style="color:rgb(31, 35, 40);background-color:rgb(11, 12, 14);"> STRIX_LLM</font><font style="color:rgb(207, 34, 46);background-color:rgb(11, 12, 14);">=</font><font style="color:rgb(10, 48, 105);background-color:rgb(11, 12, 14);">"openrouter/openai/gpt-5.4"</font>

<font style="color:rgb(207, 34, 46);background-color:rgb(11, 12, 14);">export</font><font style="color:rgb(31, 35, 40);background-color:rgb(11, 12, 14);"> LLM_API_KEY</font><font style="color:rgb(207, 34, 46);background-color:rgb(11, 12, 14);">=</font><font style="color:rgb(10, 48, 105);background-color:rgb(11, 12, 14);">"sk-or-..."</font>

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782369334973-841386e5-6ed2-49b7-8bd3-c0bf9837c227.png)

**<font style="color:rgb(36, 41, 47);">2.</font>**<font style="color:rgb(36, 41, 47);"> </font>**<font style="color:rgb(36, 41, 47);"> !Local Models</font>**<font style="color:rgb(36, 41, 47);">（</font>**<font style="color:rgb(36, 41, 47);">这个就是strix能兼容100+模型的原因</font>**<font style="color:rgb(36, 41, 47);">）：</font><font style="color:#DF2A3F;">本地部署过的/属于本机第三方的中转站的</font><font style="color:rgb(36, 41, 47);">，相当于自己随便曾经部署过哪些大模型都可以调用，比如”豆包“可能不在支持的聚合服务商行列，可先base=本地部署/使用中转站接口，再进行调用。</font>

<font style="color:rgb(36, 41, 47);"></font>

**<font style="color:rgb(36, 41, 47);">3.综上：</font>**

+ <font style="color:rgb(36, 41, 47);">想要最高精度的自动化黑客攻击，首选 </font>**OpenAI (GPT-5.4)**<font style="color:rgb(36, 41, 47);"> 或 </font>**Anthropic (Claude Opus)**<font style="color:rgb(36, 41, 47);">。</font>
+ <font style="color:rgb(36, 41, 47);">如果想审计非常大的网站源码，可以考虑 </font>**Google (Gemini 3)**<font style="color:rgb(36, 41, 47);">。</font>
+ <font style="color:rgb(36, 41, 47);">如果是囊中羞涩或者研究用，可以使用 </font>**OpenRouter**<font style="color:rgb(36, 41, 47);"> 去接入一些性价比超高的大模型。</font>

<font style="color:rgb(36, 41, 47);"></font>

<font style="color:rgb(36, 41, 47);">然后配置好大模型、key、target目标ip后，进行第一次运行，第一次会很慢，它会卡在 </font>`<font style="color:rgb(36, 41, 47);">Progress: 0/32 layers complete</font>`<font style="color:rgb(36, 41, 47);"> 这样类似的界面很久。  </font>

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782216097544-5e392163-4bcc-4c38-94bf-b1f42e40afc9.png)

**如果太慢可Ctrl+C退出，然后可进行换源，换成国内的：**

**1. 修改（或创建）Docker 的加速配置文件：**

```plain
sudo nano /etc/docker/daemon.json
```

_(如果打开是空白的也没关系)_

**2. 把下面的国内主流 Docker 加速镜像地址复制并粘贴进去：**

```plain
{
  "registry-mirrors": [
    "https://docker.m.daocloud.io",
    "https://noohzoba.mirror.aliyuncs.com",
    "https://dockerproxy.com"
  ]
}
```

_(粘贴完成后，按下 _`_Ctrl + O_`_ 保存，再按回车确认，最后按下 _`_Ctrl + X_`_ 退出 nano 编辑器。)_

**3. 刷新配置并重启 Docker 服务：**

```plain
sudo systemctl daemon-reload
sudo systemctl restart docker
```

**4.****🎯**** 搞定后再重新启动测试：**

现在回到你之前的 `strix-main` 文件夹下，再次敲下你的启动命令：

```plain
strix --target 你的测试目标
```

 只要这第一次把庞大的沙箱环境成功下载到你的电脑里，**以后每一次运行都不需要再经历这个下载过程了**，拿起来就能直接秒启动、秒开打。  



#### ！如果一直卡在*/33并且每步耗时非常长，<font style="color:#DF2A3F;">强烈建议下方进一步↓↓↓6.</font>
## 6.究极拉0/33沙箱


**国内提供的手动拉沙箱的国内镜像网址：**

[https://docker.aityp.com/r/ghcr.io/usestrix/strix-sandbox](https://docker.aityp.com/r/ghcr.io/usestrix/strix-sandbox)

不同版本（可选用[https://docker.aityp.com/image/ghcr.io/usestrix/strix-sandbox:1.0.0](https://docker.aityp.com/image/ghcr.io/usestrix/strix-sandbox:1.0.0)）

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782302213611-b7465a27-5775-493c-9131-341bd2bda4ff.png)

接下来使用国内镜像地址手动拉取（拉取的视觉上也会好很多）：**docker pull swr.cn-north-4.myhuaweicloud.com/ddn-k8s/ghcr.io/usestrix/strix-sandbox:1.0.0**

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782302284467-4df957cf-8921-4a9b-a199-b22e3865edab.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782302370649-c3a2d03b-5b50-4b53-a931-a259271d640e.png)

**下载完后**，要给拉完的国内镜像改Tag，变成Strix官方脚本能识别的名字：

**docker tag swr.cn-north-4.myhuaweicloud.com/ddn-k8s/ghcr.io/usestrix/strix-sandbox:1.0.0 ghcr.io/usestrix/strix-sandbox:1.0.0**

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782302760392-de0d3866-1b4a-4bd9-83b8-099700f45f87.png)

接下来终于步入正式测试↓

## <font style="color:#1DC0C9;">7</font>.正式测试


**输入测试的ip：strix --target Yoururl.com**

启动界面：还没试过好不好用，部署半天最终情绪价值算是给满了，非常的炫酷呐。

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782302824075-8558e919-2c53-4852-a396-f0631024ee30.png)

然后就是开始AI自动跑：**刚开始如果没给端口没给协议会先自动进行类似nmap的端口扫描。**

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783933740754-a019fdb1-777c-46f3-bfa8-c4aa3876d348.png)

然后可以看到这边的token也开始燃烧了：（我暂时用的deepseek/deepseek-v4-pro适用于测试，**真正跑用国外的服务商下的大模型**，前文也介绍过）

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782303027706-80801fbb-96ef-4247-827a-a44adb7da8df.png)



### Eg1.
经过前期第一步端口扫描，现在进入网站的扫描：

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782378989189-d31ee9c4-8743-46d2-a348-614e8453ace0.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934034434-1c5c2900-3700-43b6-9543-28fa1225c619.png)



<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782379612419-52dba350-3d19-4c4b-892d-9b1fa97830ea.png)

### Eg2.（仅仅为了测试cloude的模型们能否使用，grox暂时测不出）
这次尝试使用**local models**中转站的大模型：**export STRIX_LLM="openai/Claude Opus 4.6"**

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783933762898-6705781c-8cb6-4e6d-914f-3ff8d49afedc.png)

可以使用。

### Eg3.使用deepseekv4pro


**export STRIX_REASONING_EFFORT="high"**

先看最终消耗:基于"high"模式测试下的消耗<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782530795349-dd7585fd-4e9d-41e0-9b8c-f45a19fd5ec2.png)等价中转站额度消耗:<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782532208770-2e885456-0b1b-4050-aa7a-c7931f50eeae.png)

****

最终报告会自动生成：

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934076749-e0df2813-cb19-41ff-b57e-8cc6925fa3c3.png)

然后这里会需要一段时间整理存放到kali......

**存放位置**：不是strix-main，而是另一个strix_runs目录下

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782532104927-b43fdb65-d81e-4948-8c53-bc5a3f78cb9d.png)

### Eg4.继续ds-v4-pro:henanjigang
<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782731355769-4b5cd832-ed6e-44d6-9dac-2f9bc8c06d7c.png)

每次打完要先导出md文档查看验证，看需不需要strix进一步深度验证文档中提到的。



Eg5.

使用火山引擎协助计划的免费tokens（据说是2000w/day并且返还）



<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783933839766-dccf26fc-4dcc-4a22-afff-16ed4c29cd4f.png)

## <font style="color:#1DC0C9;">8</font>.进阶（哈基米ai生成）：操纵灵活运用
**！刚开始前要让他再加一条：完成操作要进行漏洞如何利用验证及详细步骤或者证明步骤，要写入报告。**



**1.****🛠️**** 怎么用指令操纵 AI 的“注意力”（高级测试场景）**

有时候 AI 像个无头苍蝇一样乱撞，效率太低。你可以通过 `--instruction`（给 AI 下达小纸条指令）来指挥它：

**你想测试登录后的页面（带账号密码）：** 普通的扫描器进不去登录墙，你可以直接用大白话塞给 AI 账号密码，AI 自己会去摸索怎么登录、怎么拿 Cookie：

+ Bash

```plain
strix -t http://yourTestIP --instruction "用这个账号测试登录后页面：admin / pass123"
```

**你想让它专攻某一个方向：** 比如你觉得这个中间件的业务逻辑有问题，或者想让它狂刷越权漏洞（IDOR）：

+ Bash

```plain
strix -t http://yourTestIP --instruction "重点帮我挖掘越权（IDOR）和越权逻辑漏洞"
```

****

**2.****🤖**** 什么是“无头模式”和“CI/CD”？（小白可以先跳过）**

+ **无头模式 (**`**-n**`**)：** * 默认情况下，Strix 运行起来会有一个非常漂亮的动态交互界面（像游戏菜单一样）。
    - 如果加上 `-n`（比如 `strix -n -t ...`），它就变成了**纯文本冷酷输出模式**。这通常是高手把它装在云服务器上，或者写成自动化脚本时用的，平时你自己在 Kali 里玩，**不加 **`**-n**`** 体验更好**。
+ **CI/CD (GitHub Actions)：** * 这是给开发团队用的。意思是每次程序员往 GitHub 提交新代码时，服务器会自动触发 Strix 帮他审一遍代码，如果有漏洞就拒绝合并代码。现阶段你作为个人研究，**完全不需要管这个**。



**3.进行增强，给strux进一步赋能“”  
**

 uv run strix --target https://example.com --prompt vuln-research  

如果太慢换：

uv run --index-url [https://mirrors.aliyun.com/pypi/simple/](https://mirrors.aliyun.com/pypi/simple/) strix --target [https://](https://www.jiyuan.gov.cn)example.com --prompt vuln-research

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934143020-7f955bfe-ce52-455c-a88f-22101dfbdcdd.png)

虽然下载完成，但是抛出一个错误：`strix` 这个工具并不支持 `--prompt` 这个参数。  

尝试换：

```plain
uv run strix -t https://yourTestIP --instruction "vuln-research"
```

如果你想跑得更深一些，可以加上 `-m` 参数（例如 `quick` 或 `deep`）：

```plain
uv run strix -t https://yourTestIP --instruction "vuln-research" -m quick
```

**启动！开始新的尝试：

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782377851068-7c97eeab-cdba-4222-b7a8-2a2f1d61da58.png)

发现比以前更加规整（可以说以前是盲目的”智能大脑“只会胡思乱想，现在给了一本“特种作战书”可以参考并且进行按部就班）

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934198480-2448aff4-05a4-438d-abf0-d6ef85080589.png)

如果不想进行nmap，可以直接跳过进行主域名下的渗透。

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934217618-84a0e7ef-223f-4c0f-aaa6-bbfb1fddba1b.png)

然后我们可以腾出手找别的，并且如果发现可疑或者想进行渗透的手工或者工具无法获利，就给striX吱一声。

## 9.总结评价
**1**.刚开始使用还没跑完一个网站，但是给我的第一印象就是“智能”“UI可调节”

测试中文”交流“，可以在下方进行输入，就像与人对话，他在干活，你给命令：比如觉得开始的信息收集太慢，端口扫描很慢，尝试让他跳过直接漏洞扫描，发现可以进行智能交流。

他会自动跳过第一步：

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934258200-a9580296-c34a-47f6-af2f-6d84a36ba667.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934279460-2cd5d5e4-65f4-4865-aeea-d32f4e68275e.png)



可以和他交流，发现他在ssh的爆破，可以跟他说下回不要进行密码爆破，既很智能又减少token和时间，更精准，这都是后话，慢慢开发研究strix。

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1783934313393-b062efce-b583-44d2-baa4-7eb1f9c2816e.png)

**2**.消耗

刚开始摸索，接触最多的就是strix的初级阶段：类似端口扫描等等......

会报不少无法访问到的，但是放心这些不消耗token，只有ping通的才会。

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/66872828/1782378434674-5d95bf92-fec0-4af9-b910-7b3cb682b509.png)

10.各服务商/平台大模型调用

包括**官方**或者**集成平台**比如火山引擎、讯飞星火平台或者**中转站。**

**01.[火山引擎**[**https://ark.cn-beijing.volces.com/api/v3**](https://ark.cn-beijing.volces.com/api/v3')**】**

