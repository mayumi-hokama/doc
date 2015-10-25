# 画面遷移
#### Modalにてナビゲーションバーを出す方法
```
ex) objective-C

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
