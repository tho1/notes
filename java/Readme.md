This folder contains sample jrxml file to generate jasper file.

### Tips

```
 <parameter name="DateFormat" class="java.lang.String">
                <defaultValueExpression><![CDATA["yyyy/MM/dd"]]></defaultValueExpression>
 </parameter>
  <parameter name="ReportDateFrom" class="java.lang.String"/>
 ```
To use the parameter inside the sql query

```
    trunc(to_date($P{ReportDateFrom}, 'yyyy/MM/dd'))
```


### Replacing quotes.

https://stackoverflow.com/questions/5361971/replace-all-double-quotes-within-string?rq=3
https://stackoverflow.com/questions/10580985/replace-two-quotes?rq=3
https://stackoverflow.com/questions/14895477/java-regex-replacing-double-and-single-quotes?rq=3
