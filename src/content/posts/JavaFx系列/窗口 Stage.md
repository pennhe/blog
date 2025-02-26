---
title: 窗口Stage
published: 2025-02-26
description: JavaFx笔记
tags: [Java, JavaFx]
category: JavaFx系列
draft: false
lang: zh_CN
---

### 窗口的基础设置

#### 1. 设置标题

```java
stage.setTitle("第一个JavaFx窗口");
```

#### 2. 设置图标

```java
stage.getIcons().add(new Image("img.png"));
```

#### 3. 设置最小化

- true 开启最小化
- false 关闭最小化

```java
stage.setIconified(true);
```

#### 4. 设置最大化

- true 开启最大化
- false 关闭最大化

```java
stage.setMaximized(false);
```

#### 5. 设置宽度和高度

```java
stage.setWidth(500);
stage.setHeight(500);
```

#### 6. 设置最大宽度和最大高度

```java
stage.setMaxWidth(800);
stage.setMaxHeight(800);
```

#### 7. 设置最小宽度和最小高度

```java
stage.setMinWidth(100);
stage.setMinHeight(100);
```

#### 8. 设置固定窗口大小

- true    开启 
- false    关闭

```java
stage.setResizable(true);
```

#### 9. 设置全屏

- 设置画布， 下一篇说，但是要想设置全屏生效，就必须要先设置画布

```java
stage.setScene(new Scene(new Group()));
stage.setFullScreen(true);
```

#### 10. 设置x轴和y轴坐标

```java
stage.setX(800);
stage.setY(800);
```

#### 11. 设置窗口透明度
> 取值为 0 - 1 之间

```java
stage.setOpacity(0.5);
```

#### 12. 设置窗口置顶

```java
stage.setAlwaysOnTop(true);
```

#### 13. 获取宽度和高度
> 如果设置了宽和高，那么会输出你设置的宽和高，如果没有设置，那么有可能输出NaN
> 要注意获取宽和高的代码位置，如果在show()方法之前，那么此时stage窗口还没有显示出来，自然没有宽和高

``` java
stage.getHeight();
stage.getWidth();
```

#### 14. 获取x轴和y轴坐标

``` java
stage.getX();
stage.getY();
```

#### 15. 显示窗口

``` java
stage.show();
```

#### 16. 关闭窗口

``` java
stage.close();
```

### 窗口样式

#### DECORATED  
默认窗口样式，一个带有系统默认装饰的窗口，包含标题栏、最小化按钮、最大化按钮和关闭按钮等标准的窗口控制元素。

``` java
stage.initStyle(StageStyle.DECORATED);
```

#### TRANSPARENT  
创建一个透明的窗口，不仅没有窗口装饰，而且窗口的背景也是透明的。常用于创建一些特效窗口。

> 如果不设置画布(Scene),那么运行时是透明的，如果设置了画布，则和UNDECORATED效果一样。因为画布是不透明的

``` java
s2.initStyle(StageStyle.TRANSPARENT);
```

#### UNDECORATED 
创建一个没有任何窗口装饰的窗口，即没有标题栏和窗口控制按钮。通常用于自定义窗口外观的场景。

> 需要设置画布(Scene)才能看到效果

``` java
s5.setScene(new Scene(new Group()));
stage.initStyle(StageStyle.UNDECORATED);
```

#### UNIFIED 
创建一个实用工具类型的窗口，通常具有简化的窗口装饰，没有最大化按钮，标题栏也可能更简洁。

``` java
stage.initStyle(StageStyle.UNIFIED);
```

#### UTILITY
工具类型的窗口，类似与弹窗消息，仅有关闭按钮

``` java
stage.initStyle(StageStyle.UTILITY);
```

### 监听器

#### 高度监听器

``` java
stage.heightProperty().addListener(new ChangeListener<Number>() {
    @Override
    public void changed(ObservableValue<? extends Number> observable, Number oldValue, Number newValue) {
        System.out.println("高度为：" + newValue.doubleValue());
    }
});
```

#### 宽度监听器

``` java
stage.widthProperty().addListener(new ChangeListener<Number>() {
    @Override
    public void changed(ObservableValue<? extends Number> observable, Number oldValue, Number newValue) {
        System.out.println("宽度为：" + newValue.doubleValue());
    }
});
```

#### X轴坐标监听器

``` java
stage.xProperty().addListener(new ChangeListener<Number>() {
    @Override
    public void changed(ObservableValue<? extends Number> observable, Number oldValue, Number newValue) {
        System.out.println("X:" + newValue.doubleValue());
    }
});
```

#### Y轴坐标监听器

``` java
stage.yProperty().addListener(new ChangeListener<Number>() {
    @Override
    public void changed(ObservableValue<? extends Number> observable, Number oldValue, Number newValue) {
        System.out.println("Y:" + newValue.doubleValue());
    }
});
```