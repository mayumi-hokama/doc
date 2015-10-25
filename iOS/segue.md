# 画面遷移
#### Modalにてナビゲーションバーを出す方法
 - objective-C

```
// Storyboard取得
UIStoryboard *storyboard = [UIStoryboard storyboardWithName:@"Main" bundle:nil];

// Identifierを指定してコントローラーを取得
CPPostCompleteViewController *postCompleteController = [storyboard instantiateViewControllerWithIdentifier:@"CPPostCompleteViewController"];

// 次のコントローラーに渡したい値を設定
postCompleteController.recipeId = result[@"recipeId"];

// 次のviewcontrollerのnavigationControllerを取得（ここが肝）
UINavigationController *navigationController = [[UINavigationController alloc] initWithRootViewController:postCompleteController];

// presentViewController
[self presentViewController:navigationController animated:YES completion:nil];
```  
#### root以外のviewから特定の画面へ遷移させる
 - objective-C

```
// rootViewController.m

// rootViewControllerに通知の登録
// ※通知の登録する場所はどのように動かすかで変わります。
-(void)viewWillAppear:(BOOL)animated{
    [super viewWillAppear:animated];
    // 通知登録
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(showDetailViewController) name:CPShowDetailNotificationName object:nil];  
}

// 通知の削除
// ※通知削除の場所はどのような動きをするかで変わります。
-(void)viewWillDisappear:(BOOL)animated{
    [super viewWillDisappear:animated];
    //通知を終了
    [[NSNotificationCenter defaultCenter] removeObserver:self];
}
```

```
// 通知するコントローラー
NSDictionary *dic = @{@"recipeId": self.recipeId};
[[NSNotificationCenter defaultCenter] postNotificationName:CPShowDetailNotificationName
                                                    object:self
                                                  userInfo:dic];
```
