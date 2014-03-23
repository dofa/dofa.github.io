---
layout: post
title: "SublimeTableEditor的使用"
date: 2014-03-19 14:50:39 +0000
comments: true
categories: SublimeText
tags: sublime-text
---

## 基本的使用方法

要使用该插件 ，需要用 *ctrl+shift+p* 打开 *Table Editor: Enable for current syntax* 来激活 插件。

#### 创建表头
输入：

    | Name | Phone |
    |

然后按下 *Tab*，插件帮你完成表头格式化：

    | Name | Phone |
    |------|-------|
    |      |       |

更快的创建表头方法：

    |Name|Phone

然后按下 *ctrl+k, enter*，你会得到：

    | Name | Phone |
    |------|-------|
    |      |       |
如果按下 *ctrl+k, -*，你会得到：

    | Name | Phone |
    |------|-------|

#### 新建行、在table中移动和输入文字后的对其

*tab* 为向后移动，*shift+tab* 向后移动，并且可以完成对其和新建行

## 对列的操作

*alt+shift+right*完成新建列，*alt+shift+left*删除列，*alt+right*和*alt+left*完成交换列。

#### 新建列

    |    Name   |   Phone   |
    |-----------|-----------|
    | Anna      | 123456789 |
    | Alexander | 987654321 |
    |           | _         |

如果按下 *alt+shift+right*，你会得到：
    |    Name   |   |   Phone   |
    |-----------|---|-----------|
    | Anna      |   | 123456789 |
    | Alexander |   | 987654321 |
    |           | _ |           |

#### 删除列

继续按下 *alt+shift+left*，你会得到：

    |    Name   |   Phone   |
    |-----------|-----------|
    | Anna      | 123456789 |
    | Alexander | 987654321 |
    |           | _         |

#### 交换列

    |    Name   | Age |   Phone   |
    |-----------|-----|-----------|
    | Anna      |  32 | 123456789 |
    | Alexander |  28_| 987654321 |
    |           |     |           |

继续按下 *alt+left*，你会得到：

    |    Name   | Age |   Phone   |
    |-----------|-----|-----------|
    | Anna      | 32  | 123456789 |
    | Alexander | 28_ | 987654321 |
    |           |     |           |
继续按下 *alt+right*，你会得到：

    |    Name   | Age |   Phone   |
    |-----------|-----|-----------|
    | Anna      | 32  | 123456789 |
    | Alexander | 28_ | 987654321 |
    |           |     |           |

## 对行的操作

#### 插入新行

    |    Name   |   Phone   | Age |
    |-----------|-----------|-----|
    | Anna      | 123456789 | 32_ |
    | Alexander | 987654321 | 28  |
    |           |           |     |

如果按下 *alt+shift+down*，你会得到：

    |    Name   |   Phone   | Age |
    |-----------|-----------|-----|
    |           |           |     |
    | Anna      | 123456789 | 32_ |
    | Alexander | 987654321 | 28  |
    |           |           |     |

#### 删除行

移动到要删除的行，

    |    Name   |   Phone   | Age |
    |-----------|-----------|-----|
    |           |           | _   |
    | Anna      | 123456789 | 32  |
    | Alexander | 987654321 | 28  |
    |           |           |     |

按下 *alt+shift+up*，你会得到：

    |    Name   |   Phone   | Age |
    |-----------|-----------|-----|
    | Anna      | 123456789 |  32 |
    | Alexander | 987654321 |  28 |
    |           |           |     |

#### 插入分割线

    |    Name   |   Phone   | Age |             Position             |
    |-----------|-----------|-----|----------------------------------|
    | Anna      | 123456789 |  32 | Senior Software Engineer_        |
    | Alexander | 987654321 |  28 | Senior Software Testing Engineer |
    |           |           |     |                                  |

按下 *ctrl+k,-*，得到：
    |    Name   |   Phone   | Age |             Position             |
    |-----------|-----------|-----|----------------------------------|
    | Anna      | 123456789 |  32 | Senior Software Engineer_        |
    |-----------|-----------|-----|----------------------------------|
    | Alexander | 987654321 |  28 | Senior Software Testing Engineer |
    |           |           |     |                                  |

#### 单元中内容分行

    |    Name   |   Phone   | Age |              Position             |
    |-----------|-----------|-----|-----------------------------------|
    | Anna      | 123456789 |  32 | Senior Software Engineer          |
    | Alexander | 987654321 |  28 | Senior Software _Testing Engineer |
    |           |           |     |                                   |

按下 *alt+enter*，得到：

    |    Name   |   Phone   | Age |         Position         |
    |-----------|-----------|-----|--------------------------|
    | Anna      | 123456789 |  32 | Senior Software Engineer |
    | Alexander | 987654321 |  28 | Senior Software          |
    |           |           |     | Testing Engineer         |

#### 单元中内容合并

命令为：*ctrl+j*

