# DTPagerController

[![CI Status](http://img.shields.io/travis/tungvoduc/DTPagerController.svg?style=flat)](https://travis-ci.org/tungvoduc/DTPagerController)
[![Version](https://img.shields.io/cocoapods/v/DTPagerController.svg?style=flat)](http://cocoapods.org/pods/DTPagerController)
[![License](https://img.shields.io/cocoapods/l/DTPagerController.svg?style=flat)](http://cocoapods.org/pods/DTPagerController)
[![Platform](https://img.shields.io/cocoapods/p/DTPagerController.svg?style=flat)](http://cocoapods.org/pods/DTPagerController)

This is a control for iOS written in Swift. DTPagerController is simple to use and easy to customize. 

## Screenshot

* **Default segmented control**

<p align="left" >
  <img src="Screenshot.PNG" title="Default segmented control" width = "320">
</p> 


* **Custom segmented control**
<p align="left" >
  <img src="Screenshot2.png" title="Custom segmented control" width = "320">
</p> 

## Usage

DTPagerController is extremely easy to use. In order to display two view controllers inside a pager controller. All you have to do is this many lines of code.

```swift
let viewController1 = ViewController()
let viewController2 = ViewController()
let pagerController = DTPagerController(viewControllers: [viewController1, viewController2])
```

DTPagerController is also customizable in case you want to implement your own UI.

```swift

// Change the height of segmented control
pagerController.preferredSegmentedControlHeight = 60

// Change normal font of each segmented control
pagerController.font = UIFont.customFont(ofSize: 15)

// Change selected font of each segmented control
pagerController.selectedFont = UIFont.boldCustomFont(ofSize: 15)

// Change normal text color of each segmented control
pagerController.textColor = UIColor.black

// Change selected text color of each segmented control
pagerController.selectedTextColor = UIColor.red

// Change scroll indicator height
pagerController.perferredScrollIndicatorHeight = 3

```

From version 2.0.0, DTPagerController supports custom segmented control. Therefore, instead of using default DTSegmentedControl, you can provide your own SegmentedControl or a 3rd-party SegmentedControl available out there. All you have to do is making your custom SegmentedControl conform DTSegmentedControlProtocol. For example, as shown in sample project, HMSegmentedControl is made to conform DTSegmentedControlProtocol by using extension:

```swift

extension HMSegmentedControl: DTSegmentedControlProtocol {
    
    public func setImage(_ image: UIImage?, forSegmentAt segment: Int) {
        // Custom page control does not support
    }
    
    public func setTitle(_ title: String?, forSegmentAt segment: Int) {
        // Custom page control does not support
    }
    
    public func setTitleTextAttributes(_ attributes: [AnyHashable : Any]?, for state: UIControlState) {
        if state == UIControlState.normal {
            titleTextAttributes = attributes
        }
        else if state == UIControlState.selected {
            selectedTitleTextAttributes = attributes
        }
    }
    
}

```

Then we create new pager controller with the custom segmented control:

```swift

init(viewControllers controllers: [UIViewController]) {
        let segmentedControl = HMSegmentedControl(sectionTitles: ["Page 1", "Page 2", "Page 3"])
        super.init(viewControllers: controllers, pageSegmentedControl: segmentedControl!)
}

```

## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements
### iOS 9+

## Installation

DTPagerController is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'DTPagerController'
```

## Author

tungvoduc, tung98.dn@gmail.com

## License

DTPagerController is available under the MIT license. See the LICENSE file for more info.
