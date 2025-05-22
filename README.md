# PKU本科毕业论文LaTeX模板2025修改版

## 简介

本项目是北京大学本科生毕业论文LaTeX模板，基于pkuthss 1.9.0版本修改而来。由于本科生毕业论文格式要求与博士学位论文有所不同，该模板对格式文件进行了多项修改和补充，包括字体字号的设置、页眉的设置、文献的排序、导师评阅表的添加等，以符合北京大学本科生毕业论文的格式规范。
参考项目：
[https://github.com/wongsingfo/pku-grad-thesis](https://github.com/wongsingfo/pku-grad-thesis)

[https://www.overleaf.com/latex/templates/2021-peking-university-undergraduate-thesis/bctgcdnckbdq](https://www.overleaf.com/latex/templates/2021-peking-university-undergraduate-thesis/bctgcdnckbdq)

[https://github.com/dromniscience/pku-undergraduate-thesis](https://github.com/dromniscience/pku-undergraduate-thesis)


## 适用对象

本模板适用于北京大学本科生撰写毕业论文使用。研究生（硕士/博士）请使用原版pkuthss模板。

## 环境配置（使用overleaf等可以跳过）

### 1. 安装中文字体

从[https://fontzone.net/](https://fontzone.net/)或其他可靠来源下载并安装以下中文字体文件：
- `SimSun.ttf`（宋体）
- `simfang.ttf`（仿宋体，搜索关键词"fangsong"） 
- `simhei.ttf`（黑体）
- `KaiTi.ttf`（楷体）

字体安装完成后可能需要重启系统才能生效。

### 2. 安装LaTeX环境

- **MacOS用户**：从[http://www.tug.org/mactex/](http://www.tug.org/mactex/)下载并安装MacTeX。
- **Windows用户**：从[https://www.tug.org/texlive/](https://www.tug.org/texlive/)下载并安装TexLive完整版。
- **Linux用户**：根据您的发行版使用包管理器安装TexLive。

## 编译方法

### 线上编译（推荐）

将本项目导入overleaf或PKU-latex项目中，修改主文件为`thesis.tex`，修改编译方式为`xelatex`，后直接编辑并保存即可。

### 命令行编译

在终端中，进入项目目录后执行以下命令：

```shell
# 切换到项目目录
cd 2025-PKU-undergraduate-thesis
# 编译论文
latexmk
```

清理编译过程中产生的中间文件：

```shell
latexmk -c
```

### 使用集成开发环境(IDE)

#### Visual Studio Code

1. 安装插件"LaTeX Workshop"
2. 在左侧的插件页面中，选择"Build LaTeX project"中的"Recipe: latexmk (latexmkrc)"

另：本项目中附有".vscode"文件，可以修改其中的settings.json来修改默认编译方式。

#### TeXstudio

1. 将选项的Build页面卡中"Build & View"修改为：
```
latexmk -silent -synctex=1 % | txs:///view-pdf
```
2. 点击"编译并查看"按钮进行编译

## 目录结构

```
├── chap/                   # 论文章节内容
│   ├── abs.tex             # 摘要
│   ├── ack.tex             # 致谢
│   ├── chap1.tex           # 第一章
│   ├── chap2.tex           # 第二章
│   ├── chap3.tex           # 第三章
│   ├── chap4.tex           # 第四章
│   ├── copy.tex            # 版权声明
│   ├── encl1.tex           # 附录1
│   └── origin.tex          # 原创性声明
├── others/                 # 其他相关文件
│   ├── end.pdf             # 结束页面（包含原创性声明等）
│   ├── sheet.docx          # 导师评阅表Word版
│   └── sheet.pdf           # 导师评阅表PDF版
├── pic/                    # 图片文件夹
│   └── pkulogo.pdf         # 北大校徽
├── ctex-fontset-pkuthss.def # 中文字体设置
├── ctexopts.cfg            # ctex配置文件
├── fc-list                 # 字体列表
├── KaiTi.ttf               # 楷体字体
├── latexmkrc               # latexmk配置文件
├── Make.bat                # Windows编译脚本
├── pkulogo.eps             # 北大校徽(EPS格式)
├── pkuthss-gbk.def         # GBK编码支持文件
├── pkuthss-utf8.def        # UTF-8编码支持文件
├── pkuthss.cls             # 模板主类文件
├── pkuword.eps             # 北大校名(EPS格式)
├── simfang.ttf             # 仿宋字体
├── simhei.ttf              # 黑体字体
├── SimSun.ttf              # 宋体字体
├── thesis.bib              # 参考文献数据库
├── thesis.pdf              # 生成的论文PDF
└── thesis.tex              # 论文主文件
```

## 论文内容编写

1. 论文的主体结构在`thesis.tex`文件中定义，包括论文标题、作者信息、摘要、章节等。
2. 各章节内容分别保存在`chap`目录下的tex文件中。其中有部分图片插入、图片绘制、表格插入、代码插入等等示例，可以对此修改。矢量图可以使用visio绘制后导出为pdf后插入。
3. 可以根据需要修改或添加章节文件，并在`thesis.tex`中引用。
4. 参考文献条目需添加到`thesis.bib`文件中。
5. 导师评阅表和最后的原创性说明由于每年可能不同，请参考教务邮件中的模板直接修改word文档后导出为pdf，并放入`/others`中。

## 格式说明

### 论文信息设置

在`thesis.tex`文件中修改以下内容以设置论文信息：

```latex
\pkuthssinfo{
    cthesisname = {本科生毕业论文}, ethesisname = {Thesis},
    thesiscover = {本科生毕业论文},
    ctitle = {论文中文标题},
    etitle = {Thesis Title in English},
    cauthor = {作者姓名}, eauthor = {Author Name}, date = {二〇二五~年~五~月},
    studentid = {学号}, school = {院系名称},
    cmajor = {专业名称}, emajor = {Major Name},
    cmentor = {导师姓名}, ementor = {Mentor Name},
    ckeywords = {关键词1，关键词2，关键词3},
    ekeywords = {keyword1, keyword2, keyword3},
}
```

### 特殊设置

- **双盲评审**：如需双盲评审版本，将`\blindfalse`修改为`\blindtrue`
- **文献排序**：
  - 西文文献在前，中文文献在后：`sorting = ecnyt`
  - 中文文献在前，西文文献在后：`sorting = cenyt`
  - 按引用顺序排序：`sorting = none`

- **单双面打印**：把oneside改为twoside则变为双面打印
- **修改标题下划线行数**：修改`pkuthss.cls`中的标题行数
- **代码块格式设置**：在`thesis.tex`开头部分自行修改

## 常见问题解决

1. **中文字体问题**：确保所有所需中文字体已正确安装并配置
2. **编译错误**：运行`latexmk -f`强制完整重新编译
3. **参考文献未显示**：检查是否已正确运行biber，或尝试手动运行`biber thesis`
4. **字体字号不符合要求**：检查`pkuthss.cls`中的字体字号设置

## 更新历史

本模板基于pkuthss 1.9.0修改而来，针对北京大学本科生毕业论文格式要求进行了调整。

## 致谢

本模板基于以下贡献者的工作：
- solvethis (2008-2009)
- Casper Ti. Vector (2010-2021)
- Kurapica (2021)
- dromniscience (2022)
- wongsingfo (2022)

## 许可证

本模板遵循LaTeX Project Public License (LPPL) 1.3c或更高版本许可。详细信息请参阅：[https://www.latex-project.org/lppl.txt](https://www.latex-project.org/lppl.txt)
