# I18nDemo

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.6.8.


## Running
```
npm install
npm start
```

## Assumptions

From my understanding, Angular i18n uses <x id="INTERPOLATION" /> <x id="INTERPOLATION_1" /> in the order the interpolations occur in the source language (in the template).

So a template that looks like this:
```
<p i18n>First {{firstName}} Last {{lastName}}</p>
```
will be represented in xliff as:
```
<target>First <x id="INTERPOLATION" /> Last <x id="INTERPOLATION_1" /></target>
```

So then if a language reverses the order of the interpolations they can be presented as:
```
<target>Last <x id="INTERPOLATION_1" /> First <x id="INTERPOLATION" /></target>

```

## Finding

While doing work transforming DotNet Resx files to Xliff, I found that the target Xliff files could also work with named interpolations. 

```
<target>Last <x id="INTERPOLATION_1" /> First <x id="INTERPOLATION" /> Middle {{middleName}}</target>
```

This was unexpected bonus if this is a supported feature going forward. 

Allowing double curly brace placeholders in translations will make transforming existing Resx locales (which have named placeholders as well as ordered placeholders) much easier. 

