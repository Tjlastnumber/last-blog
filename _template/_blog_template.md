<%*
let categories = await tp.system.prompt("categories", "")
let name = await tp.system.prompt("name:", "")
let title = await tp.system.prompt("title:", "")
let date = tp.date.now("YYYY/MM/DD")
let createTime = tp.file.creation_date()
let path = "/posts/" + name

tp.hooks.on_all_templates_executed(async () => {
	const tfile = tp.file.find_tfile(tp.file.path(true))
	await app.fileManager.renameFile(tfile, path + ".qmd")
})
-%>
---
title: <% title %>
date: <% date %>
categories: 
  - <% categories %>
description: 
author: lastnumber

---
# <% title %>

<%* 
tp.file.cursor() 
-%>