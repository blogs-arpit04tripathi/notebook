---
layout: post
title: Attributes - @Component
permalink: /:collection/angular/component/attributes
---

```ts
@Component({ 
  changeDetection?: ChangeDetectionStrategy
  viewProviders?: Provider[]
  moduleId?: string
  templateUrl?: string
  template?: string
  styleUrls?: string[]
  styles?: string[]
  animations?: any[]
  encapsulation?: ViewEncapsulation // Emulated (default), None, Native
  interpolation?: [string, string]
  entryComponents?: Array<Type<any> | any[]>
  preserveWhitespaces?: boolean
  // inherited from core/Directive
  selector?: string
  inputs?: string[]
  outputs?: string[]
  providers?: Provider[]
  exportAs?: string
  queries?: {...}
  host?: {...}
  jit?: boolean
})
```

![component-attributes]({{site.cdn}}/angular/component.png)

|properties|  |
|---|---|
| changeDetection | change the detection strategy used by this component.                                                                        |
| viewProviders   | list of providers available for this component and the view of their children.                                               |
| inputs          | it is property within one component (child component) to receive a value from another component (parent component).          |
| outputs         | it is property of a component to send data from one component (child component) to calling component (parent component).     |
| providers       | Providers are usually singleton objects (an instance), to which other objects have access through dependency injection (DI). |
| jit             | if true, the AOT compiler will ignore this directive/component and will therefore always be compiled using JIT.              |

# View Encapsulation
- component.css styles are applied to elements of that component only, known as Style encapsulation.
- All elements of a component are assigned a specific attribute, ex. _ngcontent-ejo-2.
- this is how angular emulates shadow DOM, as shadow DOM is not supported by all browsers.
- encapsulation
  - *ViewEncapsulation.Emulated* - default
  - *ViewEncapsulation.None* - css applied globally
  - *ViewEncapsulation.Native* - view encapsulation only for browsers supporting shadow DOM technology.
