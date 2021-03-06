# WRUserSettings
Magical User settings class for iOS

## Installation with CocoaPods

[CocoaPods](http://cocoapods.org) is a dependency manager for Objective-C, which automates and simplifies the process of using 3rd-party libraries like AFNetworking in your projects. See the ["Getting Started" guide for more information](https://github.com/AFNetworking/AFNetworking/wiki/Getting-Started-with-AFNetworking).

#### Podfile

```ruby
pod 'WRUserSettings', '~> 1.0'
```

## Usage

To start using WRUserSettings just subclass ```WRUserSettings``` class and you are ready to go!!!

So every property you add to your subclass will be stored in NSUserDefaults. Default property is nil or filled by default system value for primitive types like NSInteger, BOOL, CGRect etc.

### Basic usage

To simple usage you only need add properties to header file of subclass:

```objective-c
@interface MyUserSetting : WRUserSettings

@property (nonatomic, assign) BOOL shouldShowTutorial;
@property (nonatomic, strong) NSString *temperatureUnit;
@property (nonatomic, assign) BOOL notyficationOn;

@end
```

From now every time you set property is automatically save it in NSUserDefaults for you.

### Setting value

Your class is singleton so you should use ```+shared``` method to get instance of it:

```objective-c
[MyUserSetting shared].shouldShowTutorial = NO;
```

Class will automatically save value ```NO``` to NSUserDefaults

### Getting value

To get value just get instance of class and property:

```objective-c
BOOL shouldItReallyShowTutorial = [MyUserSetting shared].shouldShowTutorial;
```

### Default values

To set default values just conform to protocol ```WRUserSettingsDefaultsProtocol``` and implement method ```-setDefaultsValues```. Inside this method you can set default values.

Header file:

```objective-c
@interface MyUserSetting : WRUserSettings <WRUserSettingsDefaultsProtocol>

@property (nonatomic, assign) BOOL shouldShowTutorial;
@property (nonatomic, strong) NSString *temperatureUnit;
@property (nonatomic, assign) BOOL notyficationOn;

@end
```

Implementation file:

```objective-c
@implementation MyUserSetting

- (void)setDefaultsValues {
    self.shouldShowTutorial = YES;
    self.temperatureUnit = @"C";
}

@end
```

### Reset settings

If you want reset settings call anywhere method ```-resetSettings``` on your singleton. This method iterate through all saved settings and delete it from NSUserDefaults and assign to properties default values.

### Printing description

To print description of stored values simply use ```-description``` method on your singleton. It prints only stored values so it don't show default values that you set in ```-setDefaultsValues``` method.

## Change log

#### 1.0.2

\- Add ```-resetSettings``` method

\- Add simple tests

\- Example now use pod instead of imported ```WRUserSettings``` files.

#### 1.0.1

\- Added support for structures like: ```CGPoint```, ```CGRect```, ```CGSize``` etc.

\- Modify example to show ```CGPoint``` usage.

#### 1.0.0

\- Basic stuff working

## TODO

* [x] Make example
* [x] Tests

## Requirements

WRUserSettings requires either iOS 6.0 and above. 

## License

WRUserSettings is available under the MIT license. See the LICENSE file for more info.

## ARC

WRUserSettings uses ARC.

## Contact

[Rafał Wójcik](http://github.com/rafalwojcik) 
