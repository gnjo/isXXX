# isXXX
javascript isXXX  knowledge

```
let fn={};
fn.isProp=(o,p)=>{for(const a in o){if(p === a) return true};return false}
fn.isAttr=(o,a)=>{return o.hasAttribute(a)}
fn.isElement=(o)=>{return !!(o && o.nodeType === 1)}

```
