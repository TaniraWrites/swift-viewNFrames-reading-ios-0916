# Frames & Bounds

![](http://i.imgur.com/0gf2IgJ.jpg)  

> When someone says: 'I want a programming language in which I need only say what I wish done', give him a lollipop. -[Alan Perlis](https://en.wikipedia.org/wiki/Alan_Perlis)

## Overview

In this lesson, we'll introduce the view hierarchy as well as frames and bounds. 

## Learning Objectives

* Describe the view hierarchy
* Explain how views are laid out according to a coordinate system
* Explain how frames describe a view's location and size
* Describe how frames and bounds are used in iOS

## User Interface Layouts

In the old days of iOS programming, laying out a user interface was easy: You just popped open Interface Builder and arranged your UI elements (buttons, labels, and so on). It would look good (or at least the _same_) whether you ran it on an iPhone or an iPod Touch.

Then the iPad came along. Then the iPhone 5 was released, with a larger screen size. Then came the iPhone 6 and the iPhone 6+, and suddenly iOS programmers had a plethora of screen sizes to worry about. Something that looked good on the iPhone 4S might not look quite right on the iPhone 5 or iPhone 6+, let alone the iPad. iOS programmers now faced the same problem that plagued web developers: designing applications for radically different screen sizes.

Luckily, Apple had a solution to this problem: Autolayout and constraints. Now iOS programmers could go back to laying out their UIs so they looked right on the myriad screens that their users might have.

Unfortunately, this made UI design in iOS a bit more complicated. But over time, autolayouts and constraints became fine-tuned, so it was once again easy to design an interface for different screens.

Before we go into the nitty-gritty of autolayouts and constraints, though, let's talk about frames and bounds.

## Frames & Bounds

Before we talk about frames and bounds, though, let's first talk a bit about how the _view hierarchy_ in iOS works. You've already worked with a few views in previous lessons, such as `UIView`s, `UITableView`s, and even `UILabel`s and `UIButton`s (which are also views). In iOS, everything you see on the screen has a main view of some sort. This main view takes up the entire screen. Within this view, you can have _subviews_. Subviews are views placed within another view. For example, if you drag a button into your UI, that button (a `UIButton` instance) is a _subview_ of the main view. Conversely, the _parent view_ of the `UIButton` is the main view. Views can have any number of subviews, but a subview only has one parent view. (The main view does not have a parent view at all, of course.)

Views are laid out according to a coordinate system. The coordinate system is an X-Y grid in which every pixel on the screen is a number, which allows the view to reference any point on the screen. The top-left corner of the view is the origin of the coordinate system, which is referred to by the point (0,0). The coordinate system extends to the right and down, so (10,20) refers to the pixel 10 pixels from the left of the screen and 20 pixels from the top.

Now let's talk about _frames_ and _bounds_.

In a nutshell, a _frame_ describes a view's location and size in reference to the _parent view's_ coordinate system. _Bounds_ describe a view's location and size in reference to _its own_ coordinate system.

Since you haven't worked with iOS coordinate systems at all, that may be a bit confusing, so let's use a real-world example to illustrate.

Say you have a pretty painting that you want to hang on your wall. The wall is much like the screen or main view in your iOS application. You can describe points on that wall using a coordinate system. If you hang the painting right up in the top left corner of the wall, you're hanging it at (0,0) _in reference to the wall's coordinate system_. Obviously, it would look pretty stupid to have your painting jammed up in the top left corner, so perhaps you moved it down and to the right a bit, so it's no longer at (0,0).

The wall represents a _frame_. The painting is arranged at some point in that frame. It _may_ be at (0,0) in the frame's coordinate system, or it may be at another point entirely. Regardless, it lies within that frame, which is to say it's hanging on the wall somewhere.

The painting itself has a size and location too, though. Its size is much smaller than that of the wall. It also has a top left corner (which is independent of the top left corner of the wall). The picture that is painted on the canvas lies entirely within the _bounds_ of that painting.

The painting can be said to have its own coordinate system, too. Within the _bounds_ of the painting, (0,0) refers to the top left corner _of the painting_.

Let's say you put something on the painting, like a sticker of a cat (because you thought that would be funny). You could describe the position of that sticker relative to the painting. Now the painting also has a frame, which is totally different from its parent's frame (the wall), and the sticker has a location relative to the painting's frame. The sticker also has its own bounds, too, which describe the dimensions of the sticker itself.

You could keep doing this—sticking things within the _frame_ of some larger thing, like a painting or a wall—but we'll stop there for now, since you can probably see that this could go on forever.

So how are frames and bounds used in iOS? It's pretty simple: When you create a new view (a `UIView` or a subclass), it is positioned _within a parent view_ (i.e., relative to that parent view) using a _frame_. When you want to draw something in that view (or add more subviews, like a label or button), you use the _bounds_ of that view to know where you can draw or position subviews.

You'll see frames and bounds in action much more in subsequent lessons, when you start to lay out more complicated views.

<a href='https://learn.co/lessons/ViewsNframes' data-visibility='hidden'>View this lesson on Learn.co</a>
