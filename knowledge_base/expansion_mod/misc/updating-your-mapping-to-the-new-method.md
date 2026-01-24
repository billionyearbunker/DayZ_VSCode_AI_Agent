# Updating Your Mapping to the New Method

## Converting to the New Format

You will need the software **Visual Studio Code** (also possible with Notepad++)

Once downloaded, create an empty file and paste all your `SpawnObject` lines inside it.

(You can also use this software made by Def or use the "DayZ Editor" from the workshop)

**SpawnObject list**

Then press `CTRL + H` and write the following as shown in the picture (make sure to click on the small asterisk on the right or press `ALT + R`):

```
SpawnObject\( "(.*)", "(.*)", "(.*)" \);

$1|$2|$3
```

**Convert example**

Click replace (or `CTRL + ALT + ENTER`) everything and Tada your mapping now follows the correct format!

**After converting**

---

## Where to Save?

Now you want to save your file in your mission `\Expansion.MyWorldName\expansion\objects\` and save your mapping in `.map` format as shown in this picture.

**mapping directory**

---

## How to Enable it?

It's enough for the files to be present in the folder.
