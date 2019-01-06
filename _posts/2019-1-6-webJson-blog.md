---
layout: post
title:  "状态吗返回200却走向error"
categories: jekyll
tags:  web json
author: FoolHerb
---

* content
{:toc}

## java后台代码
```js
	@ResponseBody
	@RequestMapping("/getListLostData")
	public String getListLostData(@RequestBody Page page) {
		System.out.println(page.toString());
		List<Lost> losts =  lostService.list(page);
        JSONObject json= new JSONObject();
        json.put("losts" , JSONObject.toJSON(losts));
        return json.toJSONString();
	}
```

## web代码

```js
 $.ajax({
 		type:"post",
 		url: page,
 		data:jsonData,
		async:false,
 		cache:false,
 		dataType:"json",
		contentType:"application/json;charset=UTF-8",
	   	success:function(result){
			console,log(JSON.stringify(result));
        	},
		error:function(error){
			console,log(JSON.stringify(error));
		}
	});
```

返回值为200，却在error部分输出数据，因为它认为返回的数据不是标准的json数据，可修改为下边代码。

```js
dataType:"text"
```

水平有限，只能暂时这样修改。
