# isXXX
javascript isXXX  knowledge

```
let fn={};
fn.isJSON =function(d){ try{JSON.parse(d);return true}catch(e){return false} }
//element
fn.isProp=function(o,p){for(const a in o){if(p === a) return true};return false}
fn.isAttr=function(o,a){return o.hasAttribute(a)}
fn.isElement=function(o){return !!(o && o.nodeType === 1)} 

fn.isUndefined =function(obj){return obj === void 0}
fn.isEqual = function(a, b){return eq(a, b)}
fn.isObject = function(obj){var type = typeof obj;return type === 'function' || type === 'object' && !!obj}
fn.isNull = function(obj){return obj === null}
fn.isArray = Array.isArray || function(obj){return toString.call(obj) === '[object Array]'}
fn.isArguments = function(obj){return toString.call(obj) === '[object Arguments]'||fn.has(obj, 'callee')}
fn.isFunction = function(obj){return toString.call(obj) === '[object Function]'}
if(typeof /./ != 'function' && typeof Int8Array != 'object'){
/*localize under safari 8, under ie 11*/
 fn.isFunction = function(obj){return typeof obj == 'function' || false}
}
fn.isString = function(obj){return toString.call(obj) === '[object String]'}
fn.isNumber = function(obj){return toString.call(obj) === '[object Number]'}
fn.isDate = function(obj){return toString.call(obj) === '[object Date]'}
fn.isRegExp = function(obj){return toString.call(obj) === '[object RegExp]'}
fn.isError = function(obj){return toString.call(obj) === '[object Error]'}
fn.isFinite = function(obj){return isFinite(obj) && !isNaN(parseFloat(obj))}
fn.isNaN = function(obj){return _.isNumber(obj) && obj !== +obj}
fn.isBoolean = function(obj){return obj === true || obj === false || toString.call(obj) === '[object Boolean]'}

fn.isArrayLike = function(collection) {
 var length = (collection == null)?void 0:collection['length'];
 return typeof length == 'number' && length >= 0 && length <= (Math.pow(2, 53) - 1);
}
fn.isCollection = fn.isArrayLike;
fn.isEmpty = function(obj) {
    if (obj == null) return true;
    if (fn.isArrayLike(obj) && (fn.isArray(obj) || fn.isString(obj) || fn.isArguments(obj))) return obj.length === 0;
    return Object.keys(obj).length === 0;
}

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
