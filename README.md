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

# 5.26 pratising
```
extension CouponViewController{
    public enum CellType:Int {
        case Default
        case UsedTableViewCell
        case ExpiredTableViewCell
        case SelectCouponTableViewCell
    }
    /// model
    public class CouponUIModel {
        
        public var ticketNumber = ""
        public var validity = NSAttributedString()
        public var disCount = NSAttributedString()
        public var isExpend = Bool()
        public var customType = CellType.Default
        public var heightOfCell = 158.0
        
    }
    /// ViewModel
    public class ViewModel{
        public var datas = [CouponUIModel]()
        public var countOfCell = 4
        public init(){}
        
        
        /// 这里是嵌套闭包，可以传入参数和返回参数都为()即为Void，效果是可以实现像之前学oc的时候的uiview animationwithduration compeletion{    } 里面花括号里面可以在完成了函数之后完成某些内容的形式。
        public func fetchData(closure:()->()) {
            for _ in 0 ... countOfCell {
                let model = CouponUIModel()
                model.ticketNumber = "券号 : 123123"
                let validityText = creatValidityAttributedString()
                model.validity = validityText
                let discountText = creatDiscountAttributedString()
                model.disCount = discountText
                model.isExpend = false
                model.customType = CellType.ExpiredTableViewCell
                
                datas.append(model)
            
            }
            
            closure()
        }
        public func creatValidityAttributedString() -> NSMutableAttributedString {
            let validityText = NSMutableAttributedString(string: "有效期 : 2016.7.6 - 2016.10.10")
            validityText.addAttribute(NSForegroundColorAttributeName, value: UIColor.hna_ColorRed(68, green: 77, blue: 84), range: NSMakeRange(0,27))
            validityText.addAttribute(NSFontAttributeName, value: UIFont.havTextStyleRegular(12.0)!, range: NSMakeRange(0, 16))
            validityText.addAttribute(NSFontAttributeName, value: UIFont.havTextStyleMedium(12.0)!, range: NSMakeRange(16, 11))
            return validityText
        }
        public func creatDiscountAttributedString() ->NSMutableAttributedString {
            let discount = NSMutableAttributedString()
            let aStr = NSAttributedString(string: "立减", attributes: [NSFontAttributeName : UIFont.havTextStyleRegular(14.0)!])
            let bStr = NSAttributedString(string: " ¥50", attributes: [NSFontAttributeName : UIFont.havTextStyleRegular(18.0)!])
            discount.appendAttributedString(aStr)
            discount.appendAttributedString(bStr)
//            self.discountLabel.attributedText = discount
            return discount
        }
    }
```
