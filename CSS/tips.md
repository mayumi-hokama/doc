# Tips
#### z-indexが効かないとき

```
#header {
  z-index: 10;
}

↑これだけだと効かない場合

#header {
  position: relative;
  z-index: 10;
}
```
