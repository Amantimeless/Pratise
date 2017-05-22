# Hna_CouponView_record
### The UI_Controls that have been refered to are follow
#### 1,UITableView
1)Use the method called **registerClass** to reuse the customcell.

```
tableViewForTest.registerClass(SuperCustomTableViewCell.self, forCellReuseIdentifier: identifier)
```
2)use this method to get the indexPath outside the tableview datasource method.
```
let indexPath=tableViewForTest.indexPathForCell(cell)
```
#### 2,Use "aotulayout" instead of frame to fix the UIControl on the superView.Learn to use the "Snapkit" or others third-party-rack.
#### 3,Use optional value to define a variable.And when you use this variable.You can use "!",but try to use "guard" sentence  to open it.
```
guard let indexPath = tableViewForTest.indexPathForCell(cell) else { return }
```
#### 4,Method "UIColor.clearColor()" makes the transparent color.

