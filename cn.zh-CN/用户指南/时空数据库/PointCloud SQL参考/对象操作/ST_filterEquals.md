# ST\_filterEquals {#reference_dwb_mxn_qfb .reference}

指定pcpoint某一维度的固定值，过滤出pcpatch中所有该维度值等于该固定值的pcpoint，并以新的pcpatch对象返回。

## 语法 {#section_ysj_vhn_qfb .section}

```
pcpatch ST_filterEquals(pcpatch pc, text dimname, float8 value);
```

## 参数 {#section_gyb_phn_qfb .section}

|参数名称|描述|
|:---|:-|
|pc|pcpatch对象。|
|dimname|指定的属性维名称。|
|value|属性固定值。|

## 示例 {#section_cxp_4jn_qfb .section}

```
SELECT ST_AsText(ST_FilterEquals(pa, 'y', 45.57)) FROM patches WHERE id = 7;
------------------------------------------------------------
 {"pcid":1,"pts":[[-126.42,45.57,58,5],[-126.41,45.57,59,5]]}
```

