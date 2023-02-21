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
