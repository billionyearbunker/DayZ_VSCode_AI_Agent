# Adding Custom Icons

You can add your own icons which you can access by their name (must be unique!) in various systems like the map markers, notifications and market for categories/traders by overriding `ExpansionIcons::Generate` (don't forget to call super or you'll break icons elsewhere):

**Note:** This file needs to be inside `3_Game`

```cpp
modded class ExpansionIcons
{
    override void Generate()
    {
        super.Generate();

        //! "<Name>, "<Localisation>", "<Path>"
        AddIcon("My Icon 1", "", "Path/To/Your/Icon1");
        AddIcon("My Icon 2", "", "Path/To/Your/Icon2");
        //! Etc.
    }
}
```

**Note:** Localisation is currently not used, so just leave it empty.
