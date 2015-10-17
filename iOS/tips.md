# 私の私による私のためのiOS Tips
## Autolayout
### The view hierarchy is not prepared for the constraint エラー
```
The view hierarchy is not prepared for the constraint
```  
xcodeのlogにしれっと出てくるエラーメッセージ。この時の対処方。
```
[self.view addSubView:aaa] // addSubViewした後
[self.view addConstraint:bbb] // autolayoutの設定をする
```
