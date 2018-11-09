# Coding Guidelines for Objective-C Development for Mac

## Introduction

This Objective-C guide aims to keep the code across all Objective-C files or projects consistent.
It extends or emphasizes with examples some of the conventions mentioned in Apple's Cocoa Coding guidelines.
Prerequisite for this guide is [Cocoa Coding Guidelines from Apple](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html).

## Coding Conventions

### Naming Conventions

Apple naming conventions should be adhered to wherever possible.

* Use Pascal Casing for Class, Protocol, enum names
* Use Camel Casing for variables, properties, and parameter names.
* Avoid using underscores in any names

#### Naming Classes

Add a prefix `ACRO` to all the class names (except framework class names).

#### Naming Methods

* Don't start getter methods with the word `get`.
* Declare private methods in the class extension.
* Don't use `and` to link keywords that are attributes of the receiver.

```objectiveC
- (int)runModalForDirectory:(NSString *)path file:(NSString *) name types:(NSArray *)fileTypes;
/* Ok */
```

```ObjectiveC
- (int)runModalForDirectory:(NSString *)path andFile:(NSString *)name andTypes:(NSArray *)fileTypes;
/* Not Good */
```

* Use keywords before all arguments

```objectiveC
- (void)sendAction:(SEL)aSelector toObject:(id)anObject forAllCells:(BOOL)flag;
/* Ok */
```

```ObjectiveC
- (void)sendAction:(SEL)aSelector :(id)anObject :(BOOL)flag;
/* Not Good */
```

#### Properties

* Avoid using `iVar` where a property can be used.

#### Protocols

* Declare private protocols in the class extension

### Methods

* Start writing the method name after one space such as

```ObjectiveC
- (BOOL)methodName {
```

* Use "{" in the same line with one space for all (method/conditions and so on)
* Use pragma mark to group related methods.
* Proper format to use pragma mark is:

```objectiveC
#pragma mark - <group description>
```

### Enumerations

* Always add prefix to your enumeration and to enumeration's keys
* Start enumeration items with the same name as your enumeration name.

### Literals

Use `NSString`, `NSDictionary`, `NSArray`, and `NSNumber` literals whenever creating immutable instances of those objects.
To avoid crashes, ensure that null values aren't passed into `NSArray` and `NSDictionary` literals.

### UI

* Follow Apple's [HIG for Mac](https://developer.apple.com/macos/human-interface-guidelines/overview/themes/).
* Always use auto layouts.
* Don't recreate standard controls.

## Best Practices

### General Best Practice

* Use Automatic Reference Counting: Always use ARC.
  All new code must be written using ARC and legacy code must be updated to use ARC.

### Coding Best Practice

* Create a property for every `iVar` and use self to access it.
* Always declare `atomic` and `nonatomic` attribute.
* Use literals and modern Objective-C syntactic sugar.

## Commenting

* Use appledoc format for your comments.

## XCode Project Folder Structure

* Map all XCode group folders to the file system directory:
  XCode group folder doesn't represent a physical folder.
  The physical files must be kept in sync with the XCode project files to avoid file sprawl.
* Folders must reflect any XCode groups created in the file system.
* The code must be grouped not only by type but also by feature for greater Clarity.
* Example Folders and file placements
    + Application: specific app-related stuff like `Appdelegate`, `Main.m`, `.pch` and so on.
    + Controllers: view (`.xib`) and view controller stuff.
    + Library: Specific application classes like helpers, services, base classes.
    + Models: Application domain models and entities. Core Data Model.
    + Resources: Assets like images, fonts, sounds.
    + Vendors: Third-Party Libs and frameworks

## Unit Tests

Name your test suite after the class you're testing:

```objectiveC
// The class

@interface SecureStorage : NSObject

@end

// The corresponding test suite

@interface SecureStorage_Tests : XCTestCase

@end
```