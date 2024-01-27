"use strict";Object.defineProperty(exports, "__esModule", {value: true});var _core = require('@orval/core');var W=[{exports:[{name:"axios",default:!0,values:!0,syntheticDefaultImport:!0},{name:"AxiosRequestConfig"},{name:"AxiosResponse"}],dependency:"axios"}],c=new Map,O= exports.getAxiosDependencies =e=>[...e?[]:W],z=({headers:e,queryParams:s,operationName:n,response:i,mutator:a,body:o,props:l,verb:r,override:t,formData:G,formUrlEncoded:S},{route:g,context:$})=>{var A,T;let p=(t==null?void 0:t.requestOptions)!==!1,u=(t==null?void 0:t.formData)!==!1,f=(t==null?void 0:t.formUrlEncoded)!==!1,m=!!((T=(A=$.tsconfig)==null?void 0:A.compilerOptions)!=null&&T.exactOptionalPropertyTypes),E=_core.isSyntheticDefaultImportsAllow.call(void 0, $.tsconfig),y=_core.generateFormDataAndUrlEncodedFunction.call(void 0, {formData:G,formUrlEncoded:S,body:o,isFormData:u,isFormUrlEncoded:f}),F=_core.VERBS_WITH_BODY.includes(r);if(a){let h=_core.generateMutatorConfig.call(void 0, {route:g,body:o,headers:e,queryParams:s,response:i,verb:r,isFormData:u,isFormUrlEncoded:f,isBodyVerb:F,hasSignal:!1,isExactOptionalPropertyTypes:m}),q=p?_core.generateMutatorRequestOptions.call(void 0, t==null?void 0:t.requestOptions,a.hasSecondArg):"";c.set(n,C=>`export type ${_core.pascal.call(void 0, n)}Result = NonNullable<Awaited<ReturnType<${C?`ReturnType<typeof ${C}>['${n}']`:`typeof ${n}`}>>>`);let P=a.bodyTypeName&&o.definition?_core.toObjectString.call(void 0, l,"implementation").replace(new RegExp(`(\\w*):\\s?${o.definition}`),`$1: ${a.bodyTypeName}<${o.definition}>`):_core.toObjectString.call(void 0, l,"implementation");return`const ${n} = (
    ${P}
 ${p&&a.hasSecondArg?`options?: SecondParameter<typeof ${a.name}>,`:""}) => {${y}
      return ${a.name}<${i.definition.success||"unknown"}>(
      ${h},
      ${q});
    }
  `}let I=_core.generateOptions.call(void 0, {route:g,body:o,headers:e,queryParams:s,response:i,verb:r,requestOptions:t==null?void 0:t.requestOptions,isFormData:u,isFormUrlEncoded:f,isExactOptionalPropertyTypes:m,hasSignal:!1});return c.set(n,()=>`export type ${_core.pascal.call(void 0, n)}Result = AxiosResponse<${i.definition.success||"unknown"}>`),`const ${n} = <TData = AxiosResponse<${i.definition.success||"unknown"}>>(
    ${_core.toObjectString.call(void 0, l,"implementation")} ${p?`options?: AxiosRequestConfig
`:""} ): Promise<TData> => {${y}
    return axios${E?"":".default"}.${r}(${I});
  }
`},B= exports.generateAxiosTitle =e=>{let s=_core.sanitize.call(void 0, e);return`get${_core.pascal.call(void 0, s)}`},D= exports.generateAxiosHeader =({title:e,isRequestOptions:s,isMutator:n,noFunction:i})=>`
${s&&n?`// eslint-disable-next-line
  type SecondParameter<T extends (...args: any) => any> = T extends (
  config: any,
  args: infer P,
) => any
  ? P
  : never;

`:""}
  ${i?"":`export const ${e} = () => {
`}`,R= exports.generateAxiosFooter =({operationNames:e,title:s,noFunction:n,hasMutator:i,hasAwaitedType:a})=>{let o="";return n||(o+=`return {${e.join(",")}}};
`),i&&!a&&(o+=`
type AwaitedInput<T> = PromiseLike<T> | T;

    type Awaited<O> = O extends AwaitedInput<infer T> ? T : never;

`),e.forEach(l=>{c.has(l)&&(o+=c.get(l)(n?void 0:s)+`
`)}),o},w= exports.generateAxios =(e,s)=>{let n=_core.generateVerbImports.call(void 0, e);return{implementation:z(e,s),imports:n}},L= exports.generateAxiosFunctions =async(e,s)=>{let{implementation:n,imports:i}=w(e,s);return{implementation:"export "+n,imports:i}},X={client:w,header:D,dependencies:O,footer:R,title:B},Y={client:L,header:e=>D({...e,noFunction:!0}),dependencies:O,footer:e=>R({...e,noFunction:!0}),title:B},J={axios:X,"axios-functions":Y},K= exports.builder =({type:e="axios-functions"}={})=>()=>J[e],ae= exports.default =K;exports.builder = K; exports.default = ae; exports.generateAxios = w; exports.generateAxiosFooter = R; exports.generateAxiosFunctions = L; exports.generateAxiosHeader = D; exports.generateAxiosTitle = B; exports.getAxiosDependencies = O;
