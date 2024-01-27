"use strict";Object.defineProperty(exports, "__esModule", {value: true});var _core = require('@orval/core');var V=[{exports:[{name:"HttpClient",values:!0},{name:"HttpHeaders"},{name:"HttpParams"},{name:"HttpContext"}],dependency:"@angular/common/http"},{exports:[{name:"Injectable",values:!0}],dependency:"@angular/core"},{exports:[{name:"Observable",values:!0}],dependency:"rxjs"}],d=new Map,j= exports.getAngularDependencies =()=>V,M= exports.generateAngularTitle =n=>{let t=_core.sanitize.call(void 0, n);return`${_core.pascal.call(void 0, t)}Service`},U= exports.generateAngularHeader =({title:n,isRequestOptions:t,isMutator:a,isGlobalMutator:r,provideIn:s})=>`
${t&&!r?`type HttpClientOptions = {
  headers?: HttpHeaders | {
      [header: string]: string | string[];
  };
  context?: HttpContext;
  observe?: any;
  params?: HttpParams | {
    [param: string]: string | number | boolean | ReadonlyArray<string | number | boolean>;
  };
  reportProgress?: boolean;
  responseType?: any;
  withCredentials?: boolean;
};`:""}

${t&&a?`// eslint-disable-next-line
    type ThirdParameter<T extends (...args: any) => any> = T extends (
  config: any,
  httpClient: any,
  args: infer P,
) => any
  ? P
  : never;`:""}

@Injectable(${s?`{ providedIn: '${_core.isBoolean.call(void 0, s)?"root":s}' }`:""})
export class ${n} {
  constructor(
    private http: HttpClient,
  ) {}`,N= exports.generateAngularFooter =({operationNames:n})=>{let t=`};

`;return n.forEach(a=>{d.has(a)&&(t+=d.get(a)+`
`)}),t},_=({headers:n,queryParams:t,operationName:a,response:r,mutator:s,body:i,props:l,verb:o,override:e,formData:h,formUrlEncoded:O},{route:$,context:B})=>{var f,T;let p=(e==null?void 0:e.requestOptions)!==!1,c=(e==null?void 0:e.formData)!==!1,u=(e==null?void 0:e.formUrlEncoded)!==!1,y=!!((T=(f=B.tsconfig)==null?void 0:f.compilerOptions)!=null&&T.exactOptionalPropertyTypes),D=_core.VERBS_WITH_BODY.includes(o),C=_core.generateFormDataAndUrlEncodedFunction.call(void 0, {formData:h,formUrlEncoded:O,body:i,isFormData:c,isFormUrlEncoded:u}),g=r.definition.success||"unknown";if(d.set(a,`export type ${_core.pascal.call(void 0, a)}ClientResult = NonNullable<${g}>`),s){let b=_core.generateMutatorConfig.call(void 0, {route:$,body:i,headers:n,queryParams:t,response:r,verb:o,isFormData:c,isFormUrlEncoded:u,hasSignal:!1,isBodyVerb:D,isExactOptionalPropertyTypes:y}),A=p?_core.generateMutatorRequestOptions.call(void 0, e==null?void 0:e.requestOptions,s.hasThirdArg):"",E=s.bodyTypeName&&i.definition?_core.toObjectString.call(void 0, l,"implementation").replace(new RegExp(`(\\w*):\\s?${i.definition}`),`$1: ${s.bodyTypeName}<${i.definition}>`):_core.toObjectString.call(void 0, l,"implementation");return` ${a}<TData = ${g}>(
    ${E}
 ${p&&s.hasThirdArg?`options?: ThirdParameter<typeof ${s.name}>`:""}) {${C}
      return ${s.name}<TData>(
      ${b},
      this.http,
      ${A});
    }
  `}let H=_core.generateOptions.call(void 0, {route:$,body:i,headers:n,queryParams:t,response:r,verb:o,requestOptions:e==null?void 0:e.requestOptions,isFormData:c,isFormUrlEncoded:u,isAngular:!0,isExactOptionalPropertyTypes:y,hasSignal:!1});return` ${a}<TData = ${g}>(
    ${_core.toObjectString.call(void 0, l,"implementation")} ${p?`options?: HttpClientOptions
`:""}  ): Observable<TData>  {${C}
    return this.http.${o}<TData>(${H});
  }
`},W= exports.generateAngular =(n,t)=>{let a=_core.generateVerbImports.call(void 0, n);return{implementation:_(n,t),imports:a}},k={client:W,header:U,dependencies:j,footer:N,title:M},z= exports.builder =()=>()=>k,ne= exports.default =z;exports.builder = z; exports.default = ne; exports.generateAngular = W; exports.generateAngularFooter = N; exports.generateAngularHeader = U; exports.generateAngularTitle = M; exports.getAngularDependencies = j;
