好的，以下是详细整理的标签及其属性和用途，确保不遗漏任何内容：

### 1. 根标签
- **`<EPRDocument>`**
  - **属性**:
    - `version`: 版本号（默认2.01）
    - `PaperSize`: 纸张类型（0：默认，1：A4，2：16K，3：B5，4：自定义）
    - `PaperWidth`: 纸张宽度（mm，仅当`PaperSize=4`时有效）
    - `PaperHeight`: 纸张高度（mm，仅当`PaperSize=4`时有效）
    - `PaperLeftMargin`: 左边距（mm）
    - `PaperRightMargin`: 右边距（mm）
    - `PaperTopMargin`: 上边距（mm）
    - `PaperBottomMargin`: 下边距（mm）
    - `landscape`: 纸张方向（0：纵向，1：横向）
    - `AloneHeader`: 独立页眉（1：每页页眉独立）
    - `AloneFooter`: 独立页脚（1：每页页脚独立）
    - `BasePageNo`: 开始页码（默认从第1页开始）
    - `HeaderLineType`: 页眉分割线类型（0：无，1：虚线，2：实线）
    - `HeaderLineColor`: 页眉分割线颜色（默认黑色）
    - `HeaderLineWidth`: 页眉分割线宽度
    - `RowLineType`: 主题部分分割线类型
    - `RowLineColor`: 主题部分分割线颜色
    - `RowLineWidth`: 主题部分分割线宽度
    - `FooterLineType`: 页脚分割线类型
    - `FooterLineColor`: 页脚分割线颜色
    - `FooterLineWidth`: 页脚分割线宽度
    - `RowSpace`: 默认行间距（倍数，例如：0.6）

### 2. 文档部件
- **`<Header>`**
  - 页眉部分，必须包含段落标签`<P>`或强制换页标签`<PageBreak>`。

- **`<Body>`**
  - 主体内容部分，通常用于展示医疗记录的具体内容。

- **`<Footer>`**
  - 页脚部分，通常用于展示页码或其他信息。

### 3. 段落标签
- **`<P>`**
  - **属性**:
    - `Align`: 水平对齐方式（1：左对齐，2：居中对齐，3：右对齐）
    - `RowSpace`: 行间距（标准行距的倍数，例如0.6）
    - `BeforeSpace`: 段落前间隔（像素）
    - `AfterSpace`: 段落后间隔（像素）
    - `IdentMode`: 缩进方式（1：首行缩进，2：悬挂缩进）
    - `IdentNum`: 缩进字符数
    - `AllowEnter`: 是否允许回车（建立新段落）

#### 示例
```xml
<P Align="2" RowSpace="0.9">
    <Text Style="2" ReadOnly="true">门 诊 病 历</Text>
</P>
```

### 4. 强制换页标签
- **`<PageBreak>`**
  - **属性**:
    - `PageMode`: 页码编码方式（1：重新开始编码，2：继第一节编码，3：续前节编码）
    - `BasePageNo`: 开始页码

### 5. 数据元素节点
- **`<Node>`**
  - **属性**:
    - `Name`: 结构化节点名称
    - `Description`: 节点描述
    - `Hide`: 隐藏条件（例如：`Sex=女`，`Sex=男`等）
    - `Label`: 标签显示内容（为空时显示虚拟字符`{}`）
    - `LabelMode`: 标签模式（0：不显示，1：先显示，2：独立行显示）
    - `Identical`: 强制一致性检查（值为1时表示同名称节点内容必须一致）
    - `Style`: 显示样式
    - `AllowEmpty`: 是否允许空值
    - `Format`: 显示格式
    - `Type`: 数据类型（0：字符型，1：整数型，2：数值型，3：日期型）

#### 示例
```xml
<Node Name="主诉" Label="主诉：" LabelMode="1" Style="3">
    <Text Style="4">测试</Text>
</Node>
```

### 6. 单选文本元素
- **`<RadioText>`**
  - **属性**:
    - `Selected`: 选择的元素值
    - `Items`: 选项内容（默认使用`;`分开）
    - `SplitChar`: 分割字符（默认`;`，一般不重新定义）
    - `BindData`: 绑定基础值域字典

#### 示例
```xml
<RadioText Style="1" BindData="CV5302.01"></RadioText>
```

- **`<RadioSelect>`**
  - **属性**:
    - `DisplayStyle`: 显示方式（1：使用连接字符，2：固定宽度）
    - `ConnectStr`: 使用的连接字符（例如：空格）
    - `ItemWidth`: 单选项显示宽度（像素）
    - `ColumnCount`: 单行显示选项个数
    - `SelectedStyle`: 选择方式（1：选项前勾选，2：选项后勾选，3：直接在文本上勾选）

#### 示例
```xml
<RadioSelect Style="1" Items="选项1;选项2;选项3"></RadioSelect>
```

### 7. 多选文本元素
- **`<CheckText>`**
  - 继承自`RadioText`，允许选择多个值。

#### 示例
```xml
<CheckText Style="1" BindData="CV5302.01"></CheckText>
```

- **`<CheckSelect>`**
  - 继承自`RadioSelect`，用于多选。

#### 示例
```xml
<CheckSelect Style="1" Items="选项1;选项2;选项3"></CheckSelect>
```

### 8. 表格元素
- **`<Table>`**: 普通表格。
- **`<EmptyTable>`**: 定位表格，不显示网格线，仅用于元素显示定位。
- **`<RecordTable>`**: 记录式表格，用于构建数据。

**属性**:
- `HeaderRow`: 标题行数（用于跨页时复制标题行）
- `MaxDataRow`: 最多行数
- `InnerTable`: 是否嵌套表格（用于表格嵌套表格）

#### 示例
```xml
<EmptyTable RowSpace="0.7">
    <Row>
        <Cell Width="120">
            <Text Style="103" ReadOnly="true">科室：</Text>
            <DataBind ReadOnly="true" Style="103" Data="科室" Type="0" />
        </Cell>
    </Row>
</EmptyTable>
```

- **`<Row>`**: 表格行元素。
- **`<Cell>`**: 表格单元格元素。
  - **属性**:
    - `CellMerge`: 向右合并单元格数
    - `RowMerge`: 向下合并行数
    - 边框属性（左、右、上、下的边线宽度和颜色）

#### 示例
```xml
<Cell Width="100" CellMerge="1" RowMerge="1">
    <Text Style="103">示例文本</Text>
</Cell>
```

### 9. 签名和日期元素
- **`<Sign>`**
  - **属性**:
    - `OperatorId`: 操作员编号
    - `OperatorName`: 操作员名称
    - `OperateDate`: 签名日期
    - `SignEvent`: 签名事件（0：无，1：病历完成，2：主治签审，3：主任签审）
    - `IsPrint`: 是否打印
    - `Scale`: 签名图片显示缩放大小

#### 示例
```xml
<Sign Style="4" SignEvent="1" ShowRate="0.6">&lt;签名&gt;</Sign>
```

- **`<Date>`**
  - **属性**:
    - `Format`: 日期显示格式（如：`YYYY-MM-DD HH:NN:SS`）

#### 示例
```xml
<Date Style="21" Format="YYYY-MM-DD HH:NN">2018-09-02 10:00</Date>
```

### 10. 其他元素
- **`<Image>`**
  - **属性**:
    - `TextWrappingMode`: 文字环绕模式（1：普通，2：左侧环绕，3：右侧环绕，4：四周环绕）
    - `Data`: 图像数据（Base64编码） 

- **`<Data

Bind>`**
  - 绑定数据元素，用于数据展示。

