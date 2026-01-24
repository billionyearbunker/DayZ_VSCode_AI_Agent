# Creating a Custom Openable/Closable and/or Lockable Item

Creating a custom openable/closable and/or lockable item, or adding that support to an existing item, has become very easy with **Expansion 1.6.53**.

---

## Simple Examples

### Openable/Closable Container

An example for a container item that can be opened/closed and will allow access to its inventory accordingly (we will be using an existing item as a base, the vanilla `SeaChest`, note that this also means there will be no open/close animation because the SeaChest doesn't have them):

**config.cpp**

```cpp
class CfgVehicles
{
	class SeaChest;
	class ExpansionOpenableChest: SeaChest
	{
		expansionIsOpenable = 1;
	};
};
```

**ExpansionOpenableChest.c**

```cpp
class ExpansionOpenableChest: SeaChest {};  //! Only the class needs to exist for the functionality to work
```

### Lockable Container

Another example using the `SeaChest` as base class, this time making the item lockable with the Expansion codelock:

**config.cpp**

```cpp
class CfgVehicles
{
	class SeaChest;
	class ExpansionLockableChest: SeaChest
	{
		//! @note Att_CominationLock will also work if you want to support RoomService's CodeLock mod
		//! as well, but then you should disable the vanilla CombinationLocks from spawning
		attachments[] = {"Att_ExpansionCodeLock"};
	};
};
```

**ExpansionLockableChest.c**

```cpp
class ExpansionLockableChest: SeaChest {};  //! Only the class needs to exist for the functionality to work
```

### Openable and Lockable Container

And finally, a chest that can be opened/closed and is lockable with the Expansion codelock:

**config.cpp**

```cpp
class CfgVehicles
{
	class SeaChest;
	class ExpansionOpenableLockableChest: SeaChest
	{
		//! @note Att_CominationLock will also work if you want to support RoomService's CodeLock mod
		//! as well, but then you should disable the vanilla CombinationLocks from spawning
		attachments[] = {"Att_ExpansionCodeLock"};
		expansionIsOpenable = 1;
	};
};
```

**ExpansionOpenableLockableChest.c**

```cpp
class ExpansionOpenableLockableChest: SeaChest {};  //! Only the class needs to exist for the functionality to work
```

**Note:** All three examples exist in Expansion as spawnable items.

As you can see, the scripting required is minimal. You can of course still add (e.g.) your custom animations when opening/closing in script.

---

## Advanced Scripting

If you want certain actions to be only available when a player is aiming at a specific part of your custom item, you can use scripting to check for specific selections.

```cpp
class MyCustomOpenableLockableContainer: Container_Base
{
#ifdef EXPANSIONMODBASEBUILDING
    override bool ExpansionIsOpenable(string selection)
    {
        return selection == "my_custom_lid_selection";  //! Can only open/close if looking at lid
    }

    override bool ExpansionHasCodeLock(string selection)
    {
        if (!super.ExpansionHasCodeLock(selection))
            return false;
        return selection == "my_custom_codelock_selection";  //! Can only interact with codelock if looking at it
    }
#else
    //! If Expansion isn't loaded, you'll have to implement opening/closing/locking yourself
#endif
}
```

The `#ifdef` is there so you can make your modded item work without Expansion as well.
