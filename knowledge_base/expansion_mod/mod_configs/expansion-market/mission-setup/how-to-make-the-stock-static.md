# How to Make the Stock Static

---

## Overview

In this guide, we will explain what needs to be changed to make an item stock static and how to make all your items stock static using the software Visual Studio Code.

**Note**: This is also possible with Notepad++, SublimeText and many other text editors, however we will show you only with Visual Studio Code in this Guide.

---

## 0. Where Are My Market Items Configured?

In your `ServerProfile` (SC or Instance)`/ExpansionMod/Market` folder. Each file is a category of items.

For more information about what these files are for and what each line means, please read the information provided at [[Server Hosting] Adding a new Item to the market](adding-a-new-item-to-the-market.md)

---

## 1. How to Make an Item Have a Static Stock

Make sure these two lines have the same number:

```json
"MaxStockThreshold": 1,
"MinStockThreshold": 1,
```

---

## 2. How to Make All the Items Have a Static Stock

With Visual Studio Code, open the Market folder (you can also drag and drop the folder on the editor).

### Steps:

1. On the bar on the left, click on the **Search Icon**
2. Copy paste these lines inside **Search and Replace** as shown in this picture

**Search**:
```
"MaxStockThreshold": (.*),
            "MinStockThreshold": (.*),
```

**Replace**:
```
"MaxStockThreshold": 1,
            "MinStockThreshold": 1,
```

3. Make sure to click on the **Asterisk** (.*) as highlighted in the picture
4. Click on **"Replace All"**

All your items from all your files should now be static!
