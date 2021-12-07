# Translation

In index.html adding `.i18n` class to an element makes the i18n library translate the text of that element on the fly. Using the `data-i18n` attribute, we can define which property to be used from the translations config.

```
//sample config
translations: {
    'en': {
      'Point Mapper': 'Services'
    }
  },
```

```
<!-- sample html -->
<div data-i18n="Point Mapper" id="test" class="i18n">Point Mapper</div>
```

In a loop,

* We check all the elements that have `.18n` class&#x20;
* Search their `data-i18n` attribute value in the translations config(i.e "Point Mapper" in the sample code above)&#x20;
* Modify the element's text using the value that corresponds to the key(i.e "Services" in the sample code above)&#x20;
* The modified `#test` element will look like :

```
<div id="test" class="i18n">Services</div>
```
