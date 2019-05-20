## pdx-i18n
![](https://img.shields.io/github/package-json/v/Tinalst/pdx-i18n.svg)
![](https://img.shields.io/bundlephobia/minzip/pdx-i18n.svg)
### what is this?
  If you need a translation tool in your H5 project, try this

### demo 
Please link [demo](https://github.com/Tinalst/learn-webpack4.x/tree/master/dynamic-import)

### feature
Support translate
  1. html
  2. placeholder
  3. variable
  
### how to use?
 + install pxd-i18n package
 ```
 npm i pdx-i18n
 ```
 + before use this ,add translate js file
 ```
|-src
  |-i18n
    |-en
      |-module.js
    |-zh-cn
      |-module.js
    |-zh-hant
      |-module.js
    |-...
```
Please make sure the file name of en/zh-ch/... are same
  +  import the module into main.js
  ```
  import pdxI18n from 'pdx-i18n';
  window.onload = function () {
    // Instantiation internationalization
    const myI18n = initI18N('zh-hant', 'add');
  
    // Simplified Chinese
    document.querySelector('#cn').addEventListener('click', ()=>{
      myI18n.setInnerHtml('zh-cn');
    });
  
    // traditional Chinese
    document.querySelector('#hant').addEventListener('click', ()=>{
      myI18n.setInnerHtml('zh-hant');
    });
  
    // english
    document.querySelector('#en').addEventListener('click', ()=>{
      myI18n.setInnerHtml('en');
    })
  };
  
  // Initialization internationalization
  function initI18N(currentlang, currentFile) {
    const i18n =  new pdxI18n({
      currentLang: currentlang,
      useFileName: currentFile
    });
    i18n.setInnerHtml();
    return i18n;
  }

```

index.html
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title></title>
</head>
<body>
<section>
  <div class="icon-bg"></div>
  <div id="create" class="lx-button lx-button-black i18n" data-i18n="btnCreate"><!--Create wallet--></div>
  <div id="import" class="lx-button i18n" data-i18n="btnImport"><!--Import wallet--></div>
  <button id="cn">zh-cn</button>
  <button id="hant">zh-hant</button>
  <button id="en">english</button>
  <br>
</section>
  <script src="./main.js"></script>
</body>
</html>

```

### api
#### new pdxI18n（{currentLang: string,useFileName: string}）
currentLang： the name of you create to put deffirent language file name .
              for example: en/zh-cn/zh-hant
              
useFileName: the name of module.js .
              for example: /en/module.js
              the useFileName is 'module'
```
   const i18n =  new pdxI18n({
      currentLang: currentlang,
      useFileName: currentFile
    });
```
#### setInnerHtml(lang: string)
  translate html tag innerText value 
  lang: currentLang
```
i18n.setInnerHtml('en');
or
i18n.setInnerHtml();
```
#### setPlaceholderLang(lang: string)
  translate the placeholder of the element
```
  i18n.setPlaceholderLang('en');
  or
  i18n.setPlaceholderLang();
```
  
#### setObjsLang(variableName: string, lang: string, callback)
  translate variable
  lang: needn't pass
```
const i18nObj = {};
i18n.setObjsLang('i18nObj', currentlang, data => {
    console.log(data);
});
or
myI18n.setObjsLang('i18nObj', 'en', data => {
   console.log(data);
});
```

the complete guide check the dome,please. 
