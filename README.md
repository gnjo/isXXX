# isXXX
javascript isXXX  knowledge

```
let is=(this)? this.is||{}: window.is||{}
;
is.dark=(d)=>{
 //https://www.w3.org/TR/AERT/#color-contrast 
 let c=d,f=(c)=>{return ((c[0] * 299 + c[1] * 587 + c[2] * 114) / 1000)}
 if(c.charAt(5)=='') return; 
 c=c.replace('#','').match(/.{2}/g).map(d=>parseInt(d,16))
 return (f(c)<128)
}
/**/
//nihongo
//include one is true
is.katakana=(d)=>{return /[\u30a0-\u30ff]/.test(d)}
is.hiragana=(d)=>{return /[\u3040-\u309f]/.test(d)}
is.kanji=(d)=>{return /[\u3005-\u3006\u30e0-\u9fcf]/.test(d)}
is.kannji=is.kanji;
is.nihongo=(d)=>{return (is.katakana(d)|is.hiragana(d)|is.kanji(d))}
//hard check
is.katakanaOnly=(d)=>{return /^[\u30a0-\u30ff]+$/.test(d)}
is.hiraganaOnly=(d)=>{return /^[\u3040-\u309f]+$/.test(d)}
is.kanjiOnly=(d)=>{return /^[\u3005-\u3006\u30e0-\u9fcf]+$/.test(d)}
is.kannjiOnly=is.kanjiOnly;
is.nihongoOnly=(d)=>{return (is.katakanaOnly(d)|is.hiraganaOnly(d)|is.kanjiOnly(d))?true:false}
//multibyte
if(window){
 if(window.atob){
 is.utf8=(d)=>{try{window.atob(d);return true}catch(e){return false}}
}}
;
//url
is.url=(d)=>{return /^(?:(?:https?|ftp):\/\/)?(?:(?!(?:10|127)(?:\.\d{1,3}){3})(?!(?:169\.254|192\.168)(?:\.\d{1,3}){2})(?!172\.(?:1[6-9]|2\d|3[0-1])(?:\.\d{1,3}){2})(?:[1-9]\d?|1\d\d|2[01]\d|22[0-3])(?:\.(?:1?\d{1,2}|2[0-4]\d|25[0-5])){2}(?:\.(?:[1-9]\d?|1\d\d|2[0-4]\d|25[0-4]))|(?:(?:[a-z\u00a1-\uffff0-9]-*)*[a-z\u00a1-\uffff0-9]+)(?:\.(?:[a-z\u00a1-\uffff0-9]-*)*[a-z\u00a1-\uffff0-9]+)*(?:\.(?:[a-z\u00a1-\uffff]{2,})))(?::\d{2,5})?(?:\/\S*)?$/i.test(d)}
is.subLink=(d)=>{return /\#/.test(d)}
is.urlParam =(d)=>{return /\?./.test(d)}
//
is.fileString=(s=>!/[\\\/\:\*\?\"\<\>\|\0]|^\.{1,2}$|^.{0,0}$/.test(s))
//is.fileString=(s=>!/[\\\/\:\*\?\"\<\>\|\0]|^\.{1,2}$/.test(s))
//is.fileString=(s=>!/[\\\/\:\*\?\"\<\>\|]/.test(s))
if(JSON){
 is.jsonString =function(d){ try{JSON.parse(d);return true}catch(e){return false} }
 is.JSONString=is.jsonString;
}
//element
is.prop=function(o,p){for(const a in o){if(p === a) return true};return false}
is.element=function(o){return !!(o && o.nodeType === 1)} 
is.attr=function(o,a){return is.element(o)?o.hasAttribute(a):false}

is.undefined =function(obj){return obj === void 0}
//is.equal = function(a, b){return eq(a, b)}
is.object = function(obj){var type = typeof obj;return type === 'function' || type === 'object' && !!obj}
is.null = function(obj){return obj === null}
is.array = Array.isArray || function(obj){return toString.call(obj) === '[object Array]'}

is.has = function(obj, key) {return obj != null && hasOwnProperty.call(obj, key)};
is.arguments = function(obj){return toString.call(obj) === '[object Arguments]'||is.has(obj, 'callee')}
is.function = function(obj){return toString.call(obj) === '[object Function]'}
if(typeof /./ != 'function' && typeof Int8Array != 'object'){
/*localize under safari 8, under ie 11*/
 is.function = function(obj){return typeof obj == 'function' || false}
}
is.string = function(obj){return toString.call(obj) === '[object String]'}
is.number = function(obj){return toString.call(obj) === '[object Number]'}
is.date = function(obj){return toString.call(obj) === '[object Date]'}
is.regExp = function(obj){return toString.call(obj) === '[object RegExp]'}
is.error = function(obj){return toString.call(obj) === '[object Error]'}
is.finite = function(obj){return isFinite(obj) && !isNaN(parseFloat(obj))}
is.NaN = function(obj){return is.number(obj) && obj !== +obj}
is.nan =is.NaN;
is.boolean = function(obj){return obj === true || obj === false || toString.call(obj) === '[object Boolean]'}
is.bool=is.boolean;
is.arrayLike = function(collection) {
 var length = (collection == null)?void 0:collection['length'];
 return typeof length == 'number' && length >= 0 && length <= (Math.pow(2, 53) - 1);
}
is.collection = is.arrayLike;
is.empty = function(obj) {
    if (obj == null) return true;
    if (is.arrayLike(obj) && (is.array(obj) || is.string(obj) || is.arguments(obj))) return obj.length === 0;
    return Object.keys(obj).length === 0;
}


/*test code*/
let log=(d)=>{console.log(d)}
,test=(d)=>{ const data='https://wwwwww.aaaaaa/xyz.js?ss';return d +':'+is[d](data)}
;

Object.keys(is).map(test).map(log)
console.log( is.katakanaOnly('カタカナ') )
console.log(is.utf8('あいうえ...right正誤'))

```
or is.is
https://github.com/arasatasaygin/is.js
```
/*description by http://spacekey.info/blog/archives/835*/
Type checks
is.arguments……argumentsオブジェクトか
is.array……配列か
is.boolean……bool型か
is.date……日付型か
is.error……Errorオブジェクトか
is.function……関数か
is.nan……NaNか
is.null……nullか
is.number……数値か
is.object……objectか
is.json……jsonか
is.regexp……正規表現か
is.string……文字列か
is.char……charか
is.undefined……undefinedか
is.sameType……２つの引数が同じ型か
Presence checks
is.empty……emptyか
is.existry……nullでもundefinedでもないか
is.truthy……trueと判断される内容か
is.falsy……falseと判断される内容か
is.space……空白か
RegExp checks
is.url……URLか
is.email……メールアドレスか
is.creditCard……クレジットカード番号か
is.alphaNumeric……英数字か
is.timeString……時刻を表す文字列か
is.dateString……日付を表す文字列か
is.usZipCode……アメリカの郵便番号を表す文字列か
is.caPostalCode……カナダの郵便番号を表す文字列か
is.ukPostCode……イギリスの郵便番号を表す文字列か
is.nanpPhone……北米形式の電話番号を表す文字列か
is.eppPhone……extensible provisioning protocol phoneか(なにこれ?)
is.socialSecurityNumber……社会保障番号か
is.affirmative……肯定的か(true,t,yes,y,ok,okayとかにまっちします)
is.hexadecimal……16進表現か
is.hexColor……16進の色表現か
is.ip……IPアドレスか
is.ipv4……IPv4アドレスか
is.ipv6……IPv6アドレスか
String checks
is.include……対象の文字列に指定した文字列が含まれるか
is.upperCase……文字列が全て大文字か
is.lowerCase……文字列が全て小文字か
is.startWith……文字列が指定した文字列で始まるか
is.endWith……文字列が指定した文字列で終わるか
is.capitalized……先頭大文字で記載されているか
is.palindrome……回文かどうか
Arithmetic checks
is.equal……２つの引数がイコールかどうか
is.even……偶数かどうか
is.odd……奇数かどうか
is.positive……正の数か
is.negative……負の数か
is.above……最初の引数が、あとの引数より大きいか
is.under……最初の引数が、あとの引数より小さいか
is.within……最初の引数が、あとの２つの引数以内か
is.decimal……decimal型か
is.integer……整数型か
is.finite……有限数か
is.infinite……無限数か
Object checks
is.propertyCount……プロパティの数が指定した数か
is.propertyDefined……指定したプロパティが定義されているか
is.windowObject……windowオブジェクトか
is.domNode……domノードか
Array checks
is.inArray……指定した値が配列に存在するか
is.sorted……配列がソートされているか
Environment checks
is.ie……IEかどうか
is.chrome……Chromeか
is.firefox……Firefoxか
is.opera……Operaか
is.safari……Safariか
is.ios……iOSか
is.iphone……iPhoneか
is.ipad……iPadか
is.ipod……iPodか
is.android……Androidか
is.androidPhone……Android Phoneか
is.androidTablet……Android Tabletか
is.blackberry……BlackBerryか
is.windowsPhone……WindowsPhoneか
is.windowsTablet……Windows Tabletか
is.windows……Windowsか
is.mac……Macか
is.linux……Linuxか
is.desktop……デスクトップデバイスか
is.mobile……モバイルデバイスか
is.tablet……タブレットか
is.online……オンラインか
is.offline……オフラインか
Time checks
is.today……指定日付が本日か
is.yesterday……指定日付が昨日か
is.tomorrow……指定日付が明日か
is.past……指定日付が過去か
is.future……指定日付が未来か
is.day……日付が指定した曜日か
is.month……日付が指定した月か
is.year……日付が指定した年か
is.leapYear……閏年か
is.weekend……土日か
is.weekday……月～金か
is.inDateRange……日付が指定した2つの日付以内か
is.inLastWeek……日付が先週のものか
is.inLastMonth……日付が先月のものか
is.inLastYear……日付が去年のものか
is.inNextWeek……日付が来週のものか
is.inNextMonth……日付が来月のものか
is.inNextYear……日付が来年のものか
is.quarterOfYear……日付が指定した四半期か
is.dayLightSavingTime……日付が夏時間の期間か
```
