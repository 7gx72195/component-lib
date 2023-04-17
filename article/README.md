# 使用外掛
## Use CSS framework  
```
vuetify
```
## CDN(in index.html)
### icon
```
fontawesome
<script src="https://kit.fontawesome.com/cd51d51391.js" crossorigin="anonymous"></script>
```
### jquery
```
<script src="https://code.jquery.com/jquery-2.2.4.min.js"
    integrity="sha256-BbhdlvQf/xTY9gja0Dq3HiwQF8LaCRTXxZKRutelT44=" crossorigin="anonymous"></script>
```

# 修改主題色
## 路徑(src/components/article.vue)
```
<style lang="scss" scoped>
    $main-color: #568;
</style>
```
# 可用模塊
- title
- icon-title
- big-title
- img
- text
- nullData
- iframe
- pdf
- list
- hr

## title
帶有border-left的title
```
{
    "componentType": "title",
    "text": "教學特色"
}

```
## icon-title
帶有icon 的 title
icon 請上 fontawesome 官網查詢
```
 {
    "componentType": "icon-title",
    "icon":"fa-solid fa-folder-open",
    "text": "永續倡議"
},
```

## big-title
較大的title
```
{
    "componentType": "big-title",
    "text": "教學特色"
},

```
