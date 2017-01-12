[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://beta.webcomponents.org/element/polymerEl/default-value)

# \<default-value\>

`<default-value>` is a a web-component for handling default values with firebase

`data` property is equal to `input` property (usually bound to `data` property of `<firebase-document>`) when different from `null` or `{}`. Otherwise, it returns `default-value`.
A `default-type` allows to properly serialize default-value.

Example Usage:

<!--
```
<custom-element-demo>
  <template>
    <link rel="import" href="default-value.html">
    <link rel="import" href="../polymerfire/firebase-document.html">
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<firebase-document 
   path="/settings/termsVersion" 
  data="{{fbTermsVersion}}"></firebase-document>
<!-- termsVersion will be equal to "" when fbTermsVersion is null or {}. Otherwise it is "v0" (primitive, data stored at "settings/termsVersion")-->
<default-value 
  data="{{termsVersion}}"
   input="{{fbTermsVersion}}" 
   default-value=""></default-value>

<firebase-document 
  path="/userData/terms/[[user.uid]]/[[termsVersion]]"  
  data="{{userTerms}}"></firebase-document>
<!-- userTimersSigned is false whenever userTerms id null or {}. Note "object" default-type so that "false" is parsed to false -->
<default-value 
  data="{{userTermsSigned}}" 
  input="{{userTerms}}" 
  default-type="object" 
  default-value="false"></default-value>

```

