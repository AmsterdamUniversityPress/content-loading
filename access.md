# Access

## Access types
Access types determine the conditions under which users can access and use the content. Subscribed means users need to be logged-in. OA and Free means users need not be logged-in. 

### AUP business models
AUP business models have three types of access

1. Subscribed (customer pays)
2. Open Access (author/institution pays)
3. Free (AUP pays)

### AUP ONline
The platform supports four types of access

1. S = Titles Subscribed To
2. OA = Open Access Content = content will be shown to users as Open Access on the platform.
3. T = Free Trial Content = content will be shown to users as indefinitely Free on the platform.
4. F = Free Content

## XML
The access type is included in the XML - both JATS and BITS - through `<license>` and its `@license-type` attribute in  the `<permissions>` element.

### Subscribed to
Omit `<license>` from `<permissions>`.

Example from `10.5117.ANTW2023.1.007.LEEZ`:

```xml
<permissions>
<copyright-statement>&#x00a9; Michiel Leezenberg</copyright-statement>
<copyright-year>2023</copyright-year>
<copyright-holder>Michiel Leezenberg</copyright-holder>
</permissions>
```

### Free content
Use "free" or "FREE" as the value of the @license-type attribute.

Example from `10.5117.ANTW2023.1.001.DORR`:

```xml
<permissions>
<copyright-statement>&#x00a9; Steven Dorrestijn &#x0026; Herman Westerink</copyright-statement>
<copyright-year>2023</copyright-year>
<copyright-holder>Steven Dorrestijn &#x0026; Herman Westerink</copyright-holder>
<license license-type="free"><license-p></license-p></license>
</permissions>
```

### Open Access 
Use "open-access" or "OPEN-ACCESS" as the value of the @license-type attribute. Also, add a link to the appropriate _Creative Commons_ license using the @xlink:href attribute.

Example from `10.5117.QUE2022.1.001.KLEI`:

```xml
<permissions>
<copyright-statement>&#x00a9; Ru Klein</copyright-statement>
<copyright-year>2022</copyright-year>
<copyright-holder>Ru Klein</copyright-holder>
<license license-type="open">
<license-p>This is an open access article distributed under the terms of the CC BY-NC 4.0 license. <ext-link ext-link-type="uri" xlink:href="http://creativecommons.org/licenses/by/4.0/">http://creativecommons.org/licenses/by/4.0</ext-link></license-p>
</license>
</permissions>
```

This is displayed as follows on the platform:
```
© Ru Klein. This is an open access article distributed under the terms of the CC BY-NC 4.0 license. http://creativecommons.org/licenses/by/4.0
```

### the other elements in `<permissions>`
These elements are NOT nested and NOT (?) mandatory.
1. `<copyright-statement>`
2. `<copyright-year>`
3. `<copyright-holder>`
The copyright statement is displayed below the abstract (or one-page PDF if there is no abstract) on the article or chapter page. Copyright year and copyrioght holder are NOT displayed. Make sure to include that information in the copyright statement.
