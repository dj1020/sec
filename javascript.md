## Engineer questionare

### what is this

```
.
在Javascript裡的this看的是究竟是誰調用該函式，而不是看該函式被定義在哪個物件內，
下面整理出Javascript中this的指向的五種不同情況，其中前三種屬於基本的情況，而後兩種情況可基於前三種情況的方式來進行思考。

第一種：this指向於調用該函式之物件
物件.函式(); //函式內的this指向該物件

第二種：this指向全域物件（瀏覽器：window物件 node.js:GLOBAL物件）
函式(); //函式內的this指向全域物件

第三種：this指向利用call或apply所指派給this的物件
1.(A物件.)函式.call(B物件,參數1,參數2,參數3, ......); //函式的this指向B物件(若B物件為null，則指向全域物件)
2.(A物件.)函式.apply(B物件,[參數1,參數2,參數3, ......]); //函式的this指向B物件(若B物件為null，則指向全域物件)

第四種：this指向new所產生之新物件
new 建構式(); //建構式內之this指向new所產生之新物件

第五種：callback函式內的this會指向於調用放入該callback的函式之this所指向之物件
.
.
.
.
.
.
.
.
.
.
.
.
```

### what difference are apply, call, bind?

```
.
.
1.call:可以用來代替另一個對象調用一個方法。call可以將一個函數的對象上下文從初始的上下文改變為由thisObj指定的對象。
如果沒有提供thisObj參數，那Global對象被用作thisObj。

2.apply:apply方法的第一個參數也是要傳入给當前對象的對象，即函數內部的this。後面的參數都是傳遞給當前對象的參數。
apply和call兩者在作用上是相同的，但兩者在參數上有區別，對於第一個參數意義都一樣，但對第二個參數：apply傳入的是一個參數數組，
也就是將多個參數組合成為一個數組傳入，而call則作為call的參數傳入（從第二個參數開始）。

3.call和apply可以改變被調用函數的上下文，但如果重複使用會不方便，因為每次都要把上下文對象作為參數傳遞，
而且還會使代碼便不直觀，針對這種情況，可以使用bind來永久綁定函數的上下文，使其無論被誰調用，上下文都是固定的。
.
.
.
.
.
.
.
.
.
.
.
```

### please write a function can execute like

```js
console.log(add(2,3)); // logs 5
console.log(add(2)(3)); // logs 5
```

```

function add(a,b){

if(b==null){
		return function(b){
			return a+b;
		};
	}
 	return a+b;
 }
.
.
.
.
.
.
.
.
.
.
```



### please explain css style priority

```
.
若一個 HTML 文件中包含有多個樣式表，那串接這個概念就非常重要。串接是指當不同樣式表中對相同屬性有不同定義時，
應該要用哪一個樣式表中的定義的規則。最基本的規則是，越接近 HTML 本身的樣式越有優先權。
因此，內行套用的樣式通常會有最高的優先權，因為它最接近 HTML 的元素。接下來的是嵌入套用的樣式表；
這一類的樣式表是在 <head> 內宣告的。再下來是匯入套用的樣式表。若有多個樣式表被匯入，越後被匯入的越有優先權。
優先權最低的是外部連接套用的樣式表。若有多個外部樣式表被連接，越後被匯入的越有優先權。另外，每一個瀏覽器也都有自己的樣式表，
這一類的樣式表優先權比以上的幾種都低。
所以，從最高優先權到最低優先權的排名如下：
內行套用的樣式表 (Inline stylesheet)
嵌入套用的樣式表 (Embedded stylesheet)
匯入套用的樣式表 (Imported stylesheet)
外部連接套用的樣式表 (Linked stylesheet)
瀏覽器本身的樣式表 (Browser's own stylesheet)
.
.

the answer ...

```

### please explain inline mode, block mode of css

```
inline mode - 所有文字或圖片均不換行，也就是全部都會是同一行的意思。
block mode - 區塊，元素會以區塊方式呈現，除非設定 position 或 float。
block 的特性是可以設定高度（height）、寬度（width）、上方與下方距離，像是 div、p、ul、li 均屬 block。
而 inline 高度與寬度都不能設定，文字或圖片所佔的寬度就是他的寬度，像是 span、a、input、img、em 均屬 inline。
.
.
.
.
```

### please introduce ORM, what is different between SQL select?

```
.
ORM (Object-relational mapping ) 是一種對映設關聯式資料與物件資料的程式技術。
物件導向和從數學理論發展出來的關聯式資料庫，有著顯著的區別，而 ORM 正是解決這個不匹配問題所產生的工具。
它可以讓你使用物件導向語法來操作關聯式資料庫，非常容易使用、撰碼十分有效率，不需要撰寫繁瑣的SQL語法，同時也增加了程式碼維護性。
ORM的優點來自於隱藏SQL語句及物件呈現上，雖說隱藏SQL語句，倒不如說是ORM自動產生SQL語句，所有自動產生的技術，都有其強與弱，
ORM強在自動產生SQL指令，將效率維持在一定程度上，但因自動產生技術的成熟度及對該資料庫的了解度，某些地方效率低落是必然的。
高效率並不是ORM標榜的優點，維持一定程度效率才是。ORM的效率與傳統SQL有差距，以批次更新來說，在ORM下必須一一建立物件來寫入，
這與SQL指令用一行UPDATE改動所有資料列的效率有天差地壤之別，另外，ORM多支援Stored Procedure的對應，用這種方式來進行批次更新，
是ORM的既定標準手法。
.
```

### please explain right join, left join and inner join.

```
1.LEFT JOIN 可以用來建立左外部連接，查詢的 SQL 敘述句 LEFT JOIN 左側資料表 (table_name1) 的所有記錄都會加入到查詢結果中，
即使右側資料表 (table_name2) 中的連接欄位沒有符合的值也一樣。

2.相對於LEFT JOIN，RIGHT JOIN 可以用來建立右外部連接，查詢的 SQL 敘述句 RIGHT JOIN 右側資料表 (table_name2) 的所有記錄
都會加入到查詢結果中，即使左側資料表 (table_name2) 中的連接欄位沒有符合的值也一樣。

3.INNER JOIN (內部連接) 為等值連接，必需指定等值連接的條件，而查詢結果只會返回符合連接條件的資料。
```

### what is your favorite SQL and why?

```
沒有，因為對資料庫不熟悉。
.
.
.
.
.
.
.
```

### how will you implement a API server? and if it should be connect via facebook, twitter data, how will you do?

```
不知道
.
.
.
.
.
.
.

```

### do you code for test? how do you feel test?

```
是的，必須花時間找錯，是個必要之路吧。
.
.
.
.
.
.
.

```

### a layout like that below, how will you implement it and tag naming, please explain

![](http://i.stack.imgur.com/GXLMT.png)

```
不太會
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
```

## Person:  ___周俊辰__________

## Date: ___7/28____________
