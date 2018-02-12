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
fn.isEmpty = function(obj) {
    if (obj == null) return true;
    if (fn.isArrayLike(obj) && (fn.isArray(obj) || fn.isString(obj) || fn.isArguments(obj))) return obj.length === 0;
    return Object.keys(obj).length === 0;
}

```
