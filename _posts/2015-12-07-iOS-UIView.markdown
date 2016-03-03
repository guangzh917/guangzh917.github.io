---
layout: post
title: UIView控件
date: 2015-12-07 20:39:40.000000000 +08:00
tags: UI
---

## UIView控件
- 什么是控件？
    - 屏幕上所有UI元素都叫做控件(也有叫做视图、组件)
    - 比如按钮`UIButton`文本`UILabel`都是控件


- 控件的共同属性有那些？
    - 尺寸
    - 位置
    - 背景色
    - 、、、


- 苹果将控件的共同属性都抽取到`UIView`中
    - 所有的控件都继承自`UIView`
    - `UIButton`、`UILabel`、`UIImageview`等都继承自UIView(可以查看头文件验证)


- 父控件.子控件
    - 每个控件都是一个容器，能容纳其他控件
    - 内部小控件是大控件的子控件
    - 大控件是内部小控件的父控件
    - 每个容器控制器`UIViewController`内部都有一个默认的UIView属性

```ojct
/*控制器中管理的其他控件都是这个view的子控件(直接或者间接)*/
@property(nonatomic, retain) UIView *view;

```

## UIView的常见属性
- NSArray *subviews
    - 所有的子控件
    - 数组元素的顺序决定着子控件的显示层级顺序（下标越大的，越显示在上面）

```objc
    /*获得自己的父控件属性*/
   @property(nonatomic, readonly) UIView *superview;
   
   /*获得自己的所有子控件对象*/
   @property(nonatomic, readonly, copy) NSArray *subviews;
   
   /*控件的ID(标识)，父控件可以通过tag来找到对应的子控件*/
   @property(nonatomic) NSInteger tag;
   
   /*控制的形变属性(可以设置旋转角度、比例缩放、平移等属性)*/
   @property(nonatomic) CGAffineTransform transform;
```

##UIView的常见方法

```objc
    /*添加一个子控件*/
   - (void)addSubview:(UIView *)view;
   
   /*将子控件view插入到subviews数组的index位置*/
   - (void)insertSubview:(UIView *)view atIndex:(NSInteger)index;

  /*将子控件view显示到子控件siblingSubview的下面*/
  - (void)insertSubview:(UIView *)view belowSubview:(UIView *)siblingSubview;
  
  /*将子控件view显示到子控件siblingSubview的上面*/
  - (void)insertSubview:(UIView *)view aboveSubview:(UIView *)siblingSubview;

  /*将子控件view放到数组的最后面，显示在最上面*/
  - (void)bringSubviewToFront:(UIView *)view;
  
  /*将子控件view放到数组的最前面，显示在最下面*/
  - (void)sendSubviewToBack:(UIView *)view;
   
   /*从父控件中移除*/
   - (void)removeFromSuperview;
     
   /*根据一个tag标识找出对应的控件(一般都是子控件)*/
   - (UIView *)viewWithTag:(NSInteger)tag;
```

##UIView的位置尺寸
- frame
```objc
  /*控件矩形框在父控件中的位置和尺寸(以父控件的左上角为坐标原点)*/
  @property(nonatomic) CGRect frame;
  
  struct CGRect {
    CGPoint origin;
    CGSize size;
  };
  typedef struct CGRect CGRect;
  
  struct CGPoint {
    CGFloat x;
    CGFloat y;
  };
  typedef struct CGPoint CGPoint;

  struct CGSize {
    CGFloat width;
    CGFloat height;
  };
  typedef struct CGSize CGSize;
```  

    

```  
  /*控件矩形框的位置和尺寸(以自己左上角为坐标原点，所以bounds的x、y一般为0)
*/
  @property(nonatomic) CGRect bounds;
  
  /*控件中点的位置(以父控件的左上角为坐标原点)
*/
  @property(nonatomic) CGPoint center;

```