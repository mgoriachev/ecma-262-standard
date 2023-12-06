# ECMA 262 СТАНДАРТ

**Конспект**

source: https://262.ecma-international.org/

**Метаязык описания(?)**

`::` - Произведения лексической и RegExp грамматик отличаются наличием двух двоеточий `::` в качестве разделительной пунктуации.

`:::` - Произведения грамматики числовых строк отличаются наличием трех двоеточий `:::` в качестве пунктуации и никогда не используются для разбора исходного текста.

`:` - Произведения синтаксической грамматики отличаются наличием только одного двоеточия `:` в качестве пунктуации.

`<>` - В лексической грамматике и грамматике RegExp кодовые точки Юникода, не имеющие обычного печатного представления, вместо этого отображаются в форме `<ABBREV>`, где `ABBREV` - это мнемоника для кодовой точки или набора кодовых точек.

*`курсив`* - В синтаксической грамматике некоторые терминальные символы (например, *`IdentifierName`* и *`RegularExpressionLiteral`*) выделены курсивом, поскольку они относятся к одноименным нетерминальным символам в лексической грамматике.

***`opt`*** - Подстрочный суффикс ***`opt`***, который может появляться после терминала или нетерминала, указывает на необязательный символ. Альтернатива, содержащая необязательный символ, фактически задает две правые стороны: одну, которая опускает необязательный элемент, и другую, которая включает его.

***`[parameters]`*** - Это сокращение для набора продакшнов, определяющих все комбинации имен параметров, которым предшествует знак подчеркивания, добавляемый к параметризованному символу нетерминала.


**Пример #1:**
<pre>
<i>WhileStatement</i>:
    <b>while</b>( <i>Expression</i> ) <i>Statement</i></pre>

нетерминал WhileStatement представляет собой лексему while, за которой следует левая скобка, за которой следует Expression, за которой следует правая скобка, за которой следует Statement. Вхождения Expression и Statement сами по себе являются нетерминалами.

**Пример #2:**
<pre>
<i>ArgumentList</i> :
    <i>AssignmentExpression</i>
    <i>ArgumentList , AssignmentExpression</i></pre>

ArgumentList может представлять собой либо одно AssignmentExpression, либо ArgumentList, за которым следует запятая, а затем AssignmentExpression. Это определение ArgumentList является рекурсивным, то есть оно определяется в терминах самого себя. В результате ArgumentList может содержать любое положительное число аргументов, разделенных запятыми, где каждое выражение аргумента является выражением Назначения (AssignmentExpression). Такие рекурсивные определения нетерминалов встречаются часто.

**Пример #3:**
<pre>
<i>VariableDeclaration</i> :
    <i>BindingIdentifier Initializeropt</i><sub>opt</sub></pre>

является удобным сокращением для

<pre>
<i>VariableDeclaration</i> :
    <i>BindingIdentifier</i>
    <i>BindingIdentifier Initializer</i>
</pre>

**Пример #4:**
<pre>
<i>ForStatement</i> :
<b>for</b> ( <i>LexicalDeclaration Expression</i><sub>opt</sub> ; Expression</i><sub>opt</sub> ) <i>Statement</i>
</pre>
удобная аббревиатура для:
<pre>
<i>ForStatement</i> :
<b>for</b> ( <i>LexicalDeclaration ; Expression</i><sub>opt</sub> ) <i>Statement</i>
<b>for</b> ( <i>LexicalDeclaration Expression ; Expression</i><sub>opt</sub> ) <i>Statement</i>
</pre>
что, в свою очередь, является аббревиатурой для:
<pre>
<i>ForStatement</i> :
<b>for</b> ( <i>LexicalDeclaration ; ) Statement</i>
<b>for</b> ( <i>LexicalDeclaration ; Expression ) Statement</i>
<b>for</b> ( <i>LexicalDeclaration Expression ; ) Statement</i>
<b>for</b> ( <i>LexicalDeclaration Expression ; Expression ) Statement</i>
</pre>

**Пример #5:**
<pre>
<i>StatementList</i><sub>[Return]</sub> :
<i>ReturnStatement
ExpressionStatement</i>
</pre>

удобная аббревиатура для:

<pre>
<i>StatementList :
ReturnStatement
ExpressionStatement

StatementList_Return :
ReturnStatement
ExpressionStatement</i>
</pre>

**Пример #6:**
<pre>
<i>StatementList</i><sub>[Return, In]</sub> :
<i>ReturnStatement
ExpressionStatement</i>
</pre>

удобная аббревиатура для:

<pre>
<i>StatementList :
ReturnStatement
ExpressionStatement

StatementList_Return :
ReturnStatement
ExpressionStatement

StatementList_In :
ReturnStatement
ExpressionStatement

StatementList_Return_In :
ReturnStatement
ExpressionStatement</i>
</pre>
