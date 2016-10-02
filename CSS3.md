结构性伪类选择器：

:root选择器
“:root”选择器等同于<html>元素

:root{background:orange}
html {background:orange;}
得到的效果等同。
建议使用:root方法。
另外在IE９以下还可以借助“:root”实现hack功能

:not选择器称为否定选择器
栗子：

    html
        <div id="header">页头</div>
        <div id="page">页体</div>
        <div id="footer">页脚</div>

    CSS
    div{
        padding: 10px 20px;
        min-height: 50px;
    }
    div:not([id="footer"]){
        background: orange;
    }


:empty选择器表示的就是空
栗子：

    html
        <p>我是一个段落</p>
        <p> </p>
        <p></p>​

    CSS
        p{
         background: orange;
         min-height: 30px;
        }
        p:empty {
          display: none;
        }​


:target选择器称为目标选择器
栗子：1

    html
        <div class="menuSection" id="brand">
            <h2><a href="#brand">Brand</a></h2>
            <p>content for Brand</p>
        </div>

    CSS
        :target p {
          background: orange;
          color: #fff;
        }

栗子：2

    html
        <h2><a href="#brand">Brand</a></h2>
        <div class="menuSection" id="brand">
          content for Brand
        </div>
        <h2><a href="#jake">Brand</a></h2>
        <div class="menuSection" id="jake">
         content for jake
        </div>
        <h2><a href="#aron">Brand</a></h2>
        <div class="menuSection" id="aron">
            content for aron
        </div>

    CSS
        #brand:target {
          background: orange;
          color: #fff;
        }
        #jake:target {
          background: blue;
          color: #fff;
        }
        #aron:target {
          background: red;
          color: #fff;
        }



“:first-child”选择器表示的是选择父元素的第一个子元素的元素E
栗子:

    html
        <ul>
            <li><a href="##">Link1</a></li>
            <li><a href="##">Link2</a></li>
            <li><a href="##">Link3</a></li>
            <li><a href="##">Link4</a></li>
            <li><a href="##">Link5</a></li>
        </ul>

    CSS
        ul > li:first-child {
         color: red;
        }


“:last-child”选择器与“:first-child”选择器作用类似，不同的是“:last-child”选择器选择的是元素的最后一个子元素
栗子：

    html
        <ul>
            <li>Item1</li>
            <li>Item2</li>
            <li>Item3</li>
            <li>Item5</li>
            <li>Item6</li>
        </ul>

    CCS
        ul {
          border: 1px solid #ccc;
          list-style: none outside none;
          width: 220px;
          margin: 20px auto;
          padding: 0;
        }
        ul > li {
          list-style: none outside none;
          margin:0;
          padding: 10px;
          border-bottom: 3px solid #ccc;
        }
        ul > li:last-child{
          border-bottom: none;
        }


“:nth-child(n)”选择器用来定位某个父元素的一个或多个特定的子元素
栗子:
html

    <ol>
        <li>item1</li>
        <li>item2</li>
        <li>item3</li>
        <li>item4</li>
        <li>item5</li>
        <li>item6</li>
        <li>item7</li>
        <li>item8</li>
        <li>item9</li>
        <li>item10</li>
    </ol>

    CSS
        ol > li:nth-child(2n+1){
          background: green;
        }

经验与技巧:当“:nth-child(n)”选择器中的n为一个表达式时，其中n是从0开始计算，当表达式的值为0或小于0的时候，不选择任何匹配的元素
样式列表:

    <table>
        <tr>
            <th>n</th>
            <th>2n+1</th>
            <th>4n+1</th>
            <th>4n+4</th>
            <th>4n</th>
            <th>5n-2</th>
            <th>-n+3</th>
        </tr>
        <tr>
            <td>0</td>
            <td>1</td>
            <td>1</td>
            <td>4</td>
            <td></td>
            <td></td>
            <td>3</td>
        </tr>
        <tr>
            <td>1</td>
            <td>3</td>
            <td>5</td>
            <td>8</td>
            <td>4</td>
            <td>3</td>
            <td>2</td>
        </tr>
        <tr>
            <td>2</td>
            <td>5</td>
            <td>9</td>
            <td>12</td>
            <td>8</td>
            <td>8</td>
            <td>1</td>
        </tr>
        <tr>
            <td>3</td>
            <td>7</td>
            <td>13</td>
            <td>16</td>
            <td>12</td>
            <td>13</td>
            <td>0</td>
        </tr>
        <tr>
            <td>4</td>
            <td>9</td>
            <td>17</td>
            <td>20</td>
            <td>16</td>
            <td>18</td>
            <td>-1</td>
        </tr>
        <tr>
            <td>5</td>
            <td>11</td>
            <td>21</td>
            <td>24</td>
            <td>20</td>
            <td>23</td>
            <td>-2</td>
        </tr>
    </table>


“:nth-last-child(n)”选择器和前面的“:nth-child(n)”选择器非常的相似，只是这里多了一个“last”，所起的作用和“:nth-child(n)”选择器有所区别，从某父元素的最后一个子元素开始计算，来选择特定的元素
栗子:

    html
        <ol>
          <li>item1</li>
          <li>item2</li>
          <li>item3</li>
          <li>item4</li>
          <li>item5</li>
          <li>item6</li>
          <li>item7</li>
          <li>item8</li>
          <li>item9</li>
          <li>item10</li>
        </ol>

    CSS
        ol > li:nth-last-child(5){
          background: orange;
        }


“:first-of-type”选择器类似于“:first-child”选择器，不同之处就是指定了元素的类型,其主要用来定位一个父元素下的某个类型的第一个子元素
栗子:

    html
        <div class="wrapper">
            <p>我是第一个段落</p>
            <p>我是第二个段落</p>
            <div>我是第一个Div元素</div>
            <div>我是第二个Div元素</div>
            <p>我是第三个段落</p>
            <p>我是第四个段落</p>
            <div>我是第三个Div元素</div>
            <div>我是第四个Div元素</div>
        </div>

    CSS
        .wrapper {
          border: 1px solid #ccc;
          padding: 10px;
          width: 500px;
          margin: 20px auto;
        }
        .wrapper > p,
        .wrapper > div {
          margin: 10px 0;
          background: green;
          color: #fff;
          padding: 5px;
        }
        .wrapper > div:first-of-type {
          background: orange;
        }


“:nth-of-type(n)”选择器和“:nth-child(n)”选择器非常类似，不同的是它只计算父元素中指定的某种类型的子元素。当某个元素中的子元素不单单是同一种类型的子元素时，使用“:nth-of-type(n)”选择器来定位于父元素中某种类型的子元素是非常方便和有用的。在“:nth-of-type(n)”选择器中的“n”和“:nth-child(n)”选择器中的“n”参数也一样，可以是具体的整数，也可以是表达式，还可以是关键词
栗子:

    html
        <div class="wrapper">
            <div>我是一个Div元素</div>
            <p>我是一个段落元素</p>
            <div>我是一个Div元素</div>
            <p>我是一个段落</p>
            <div>我是一个Div元素</div>
            <p>我是一个段落</p>
            <div>我是一个Div元素</div>
            <p>我是一个段落</p>
            <div>我是一个Div元素</div>
            <p>我是一个段落</p>
            <div>我是一个Div元素</div>
            <p>我是一个段落</p>
            <div>我是一个Div元素</div>
            <p>我是一个段落</p>
            <div>我是一个Div元素</div>
            <p>我是一个段落</p>
        </div>

    CSS
        .wrapper > div:nth-of-type(7),
        .wrapper > p:nth-of-type(2n){
          background: orange;
        }
        /*或者*/
        .wrapper > div:nth-of-type(13),
        .wrapper > p:nth-of-type(2n){
          background: orange;
        }
        /*或者*/
        .wrapper > div:nth-of-type(2n+1),
        .wrapper > p:nth-of-type(even){
          background: orange;
        }   


“:last-of-type”选择器和“:first-of-type”选择器功能是一样的，不同的是他选择是父元素下的某个类型的最后一个子元素
栗子:

    html
        <div class="wrapper">
            <div>我是第一个Div元素</div>
            <div>我是第二个Div元素</div>
            <div>我是第三个Div元素</div>
            <p>我是第一个段落</p>
            <p>我是第二个段落</p>
            <p>我是第三个段落</p>
        </div>

    CSS
        .wrapper > div:last-of-type{
          background: orange;
        }


“:nth-last-of-type(n)”选择器和“:nth-of-type(n)”选择器是一样的，选择父元素中指定的某种子元素类型，但它的起始方向是从最后一个子元素开始，而且它的使用方法类似于上节中介绍的“:nth-last-child(n)”选择器一样
栗子:

    html
        <div class="wrapper">
            <p>我是第一个段落</p>
            <p>我是第二个段落</p>
            <div>我是第一个Div元素</div>
            <div>我是第二个Div元素</div>
            <div>我是第三个Div元素</div>
            <p>我是第三个段落</p>
            <p>我是第四个段落</p>
            <p>我是第五个段落</p>
            <div>我是第四个Div元素</div>
            <div>我是第五个Div元素</div>
            <p>我是第六个段落</p>
        </div>

    CSS 
        .wrapper > div:nth-last-of-type(5){
          background: orange;
        }


“:only-child”选择器选择的是父元素中只有一个子元素，而且只有唯一的一个子元素
栗子:1

    html
        <div class="post">
            <p>我是一个段落</p>
            <p>我是一个段落</p>
        </div>
        <div class="post">
            <p>我是一个段落</p>
        </div>

    CSS
        .post p {
          background: green;
          color: #fff;
          padding: 10px;
        }
        .post p:only-child {
          background: orange;
        }

栗子:2

    html
        <ul>
          <li>Item1</li>
          <li>Item2</li>
          <li>Item3</li>
        </ul>
        <ul>
          <li>Item1</li>
        </ul>
        <ol>
          <li>Item1</li>
        </ol>
        <ol>
          <li>Item1</li>
          <li>Item2</li>
          <li>Item3</li>
        </ol>

    CSS
        li {
          background: green;
          padding: 10px;
          margin-bottom: 5px;
        }
        li:only-child{
          background: orange;
        }


“:only-of-type”是表示一个元素他有很多个子元素，而其中只有一种类型的子元素是唯一的，使用“:only-of-type”选择器就可以选中这个元素中的唯一一个类型子元素
栗子:

    html
        <div class="wrapper">
          <p>我是一个段落</p>
          <p>我是一个段落</p>
          <p>我是一个段落</p>
        </div>
        <div class="wrapper">
          <p>我是一个段落</p>
        </div>
        <div class="wrapper">
          <div>我是一个Div元素</div>
          <p>我是一个段落</p>
          <div>我是一个Div元素</div>
        </div>

    CSS
        .wrapper {
          border: 1px solid #ccc;
          padding: 10px;
          width: 500px;
          margin: 10px auto;
        }
        .wrapper p:only-of-type{
          background: orange;
        }


通过伪选择器“:enabled”对这些表单元素设置样式
栗子:

    html
        <form action="#">
          <div>
            <label for="enabled">可用输入框:</label>
            <input type="text" id="enabled" />
          </div>
          <div>
            <label for="disabled">禁用输入框:</label>
            <input type="text" id="disabled" disabled="disabled" />
          </div>
        </form>  

    CSS
        div {
          margin: 30px;
        }
        input[type="text"]:enabled {
          border: 1px solid #f36;
          box-shadow: 0 0 5px #f36;
        }
        input[type="text"]:disabled{
          box-shadow: none;
        } 


“:disabled”选择器刚好与“:enabled”选择器相反，用来选择不可用表单元素,
要正常使用“:disabled”选择器，需要在表单元素的HTML中设置“disabled”属性
栗子: 

    html
        <form action="#">
          <div><input type="text" /></div>
          <div>
            <input type="submit" value="我要回到上一步" />
            <input type="submit" value="禁止点下一步" disabled />
          </div>
        </form> 

    CSS
        form {
          margin: 30px;
        }
        div {
          margin: 10px;
        }
        input {
          padding: 10px;
          border: 1px solid orange;
          background: #fff;
          border-radius: 5px;
        }
        input[type="submit"] {
          background: orange;
          color: #fff;
        }
        input[type="submit"]:disabled  {
          background: #eee;
          border-color: #eee;
          color: #ccc;
        }


“:checked”表示的是选中状态,在表单元素中，单选按钮和复选按钮都具有选中和未选中状态
栗子:

    html
        <form action="#">
          <div class="wrapper">
            <div class="box">
              <input type="checkbox" checked="checked" id="usename" /><span>√</span>
            </div>
            <lable for="usename">我是选中状态</lable>
          </div>
          <div class="wrapper">
            <div class="box">
              <input type="checkbox"  id="usepwd" /><span>√</span>
            </div>
            <label for="usepwd">我是未选中状态</label>
          </div>
        </form> 

    CSS
        form {
          border: 1px solid #ccc;
          padding: 20px;
          width: 300px;
          margin: 30px auto;
        }
        .wrapper {
          margin-bottom: 10px;
        }
        .box {
          display: inline-block;
          width: 20px;
          height: 20px;
          margin-right: 10px;
          position: relative;
          border: 2px solid orange;
          vertical-align: middle;
        }
        .box input {
          opacity: 0;
          position: absolute;
          top:0;
          left:0;
        }
        .box span {
          position: absolute;
          top: -10px;
          right: 3px;
          font-size: 30px;
          font-weight: bold;
          font-family: Arial;
          -webkit-transform: rotate(30deg);
          transform: rotate(30deg);
          color: orange;
        }
        input[type="checkbox"] + span {
          opacity: 0;
        }
        input[type="checkbox"]:checked + span {
          opacity: 1;
        }


“::selection”伪元素是用来匹配突出显示的文本(用鼠标选择文本时的文本)
栗子:

    html
        <p>“::selection”伪元素是用来匹配突出显示的文本。浏览器默认情况下，选择网站文本是深蓝的背景，白色的字体，</p>

    CSS
        ::selection{
          background: orange;
          color: white;
        }
        ::-moz-selection{
          background: orange;
          color: white;
        }


“:read-only”伪类选择器用来指定处于只读状态元素的样式
栗子:

    html
        <form action="#">
          <div>
            <label for="name">姓名:</label>
            <input type="text" name="name" id="name" placeholder="大漠" />
          </div>
          <div>
            <label for="address">地址:</label>
            <input type="text" name="address" id="address" placeholder="中国上海" readonly="readonly" />
          </div>
          <div>
            <label for="comment">评论：</label>
            <textarea name="comment" id="" cols="30" rows="10" readonly="readonly"></textarea>
          </div>
        </form>

    CSS
        form {
          width: 300px;
          padding: 10px;
          border: 1px solid #ccc;
          margin: 50px auto;
        }
        form > div {
          margin-bottom: 10px;
        }
        input[type="text"]{
          border: 1px solid orange;
          padding: 5px;
          background: #fff;
          border-radius: 5px;
        }
        input[type="text"]:-moz-read-only{
          border-color: #ccc;
        }
        input[type="text"]:read-only{
          border-color: #ccc;
        }
        textarea:-moz-read-only{
          border: 1px solid #ccc;
          height: 50px;
          resize: none;
          background: #eee;
        }
        textarea read-only {
          border: 1px solid #ccc;
          height: 50px;
          resize: none;
          background: #eee;
        }


“:read-write”选择器刚好与“:read-only”选择器相反，主要用来指定当元素处于非只读状态时的样式
栗子:

    html
        <form action="#">
          <div>
            <label for="name">姓名:</label>
            <input type="text" name="name" id="name" placeholder="大漠" />
          </div>
          <div>
            <label for="address">地址:</label>
            <input type="text" name="address" id="address" placeholder="中国上海" readonly="readonly" />
          </div>
        </form>  

    CSS
        form {
          width: 300px;
          padding: 10px;
          border: 1px solid #ccc;
          margin: 50px auto;
        }
        form > div {
          margin-bottom: 10px;
        }
        input[type="text"]{
          border: 1px solid orange;
          padding: 5px;
          background: #fff;
          border-radius: 5px;
        }
        input[type="text"]:-moz-read-only{
          border-color: #ccc;
        }
        input[type="text"]:read-only{
          border-color: #ccc;
        }
        input[type="text"]:-moz-read-write{
          border:2px solid red;
        }
        input[type="text"]:read-write{
          border:2px solid red;
        }


::before和::after这两个主要用来给元素的前面或后面插入内容，这两个常和"content"配合使用，使用的场景最多的就是清除浮动
栗子:1 阴影效果

    html
        <div class="box effect">
        <h3>Shadow Effect </h3>

    CSS
        .box h3{
            text-align:center;
            position:relative;
            top:80px;
        }
        .box {
            width:70%;
            height:200px;
            background:#FFF;
            margin:40px auto;
        }
        .effect{
            position:relative;       
            box-shadow:0 1px 4px rgba(0, 0, 0, 0.3),0 0 40px rgba(0, 0, 0, 0.1) inset;
            }  
        .effect::before, .effect::after{
            content:"";
            position:absolute; 
            z-index:-1;
            box-shadow:0 0 20px rgba(0,0,0,0.8);
            top:50%;
            bottom:0;
            left:10px;
            right:10px;
            border-radius:100px / 10px;
        }

栗子:2 清除浮动

    CSS
        .clearfix::before,
        .clearfix::after {
            content: ".";
            display: block;
            height: 0;
            visibility: hidden;
        }
        .clearfix:after {clear: both;}
        .clearfix {zoom: 1;}

