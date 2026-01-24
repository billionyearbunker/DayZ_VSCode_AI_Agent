# Vehicle Guide

## Contents

- [Car Keys](#car-keys)
- [Lockpicking](#lockpicking)
- [Towing](#towing)
- [Vehicle Cover](#vehicle-cover)
- [Player Attachment](#player-attachment)

---

## Car Keys

**Video:** https://www.youtube.com/watch?v=2e_Afz2NIiU

### How does it work?

Have the car keys in your hands and go to your car and now you should have the option.

However, server hosters can tweak its behavior:

```json
"VehicleRequireKeyToStart": 1,
"VehicleRequireAllDoors": 1,
"VehicleLockedAllowInventoryAccess": 0,
"VehicleLockedAllowInventoryAccessWithoutDoors": 1,
```

---

## Lockpicking

Showcase video soon.

### How does it work?

You need to hold in your hands the lockpicking tool(s) configured by the server. By default it should be the **Lockpick** item. The lockpicking difficulty can change from vehicles to vehicles and is purely luck based.

However, server hosters can tweak its behavior:

```json
"CanPickLock": 0,
"PickLockTools": [
    "Lockpick"
],
"PickLockChancePercent": 40.0,
"PickLockTimeSeconds": 120,
"PickLockToolDamagePercent": 10.0,
```

And also its lock complexity in the `vehiclesconfig`:

```json
"VehiclesConfig": [
    {
        "ClassName": "ExpansionMh6",
        "CanPlayerAttach": 0,
        "LockComplexity": 3.0
    }
]
```

---

## Towing

**Video:** https://www.youtube.com/watch?v=wkWsDXuGnMU

### What are the requirements to have the option to tow a vehicle?

**A car can tow another car:**
- The car should not be locked
- The car should not be already be towed or towing another car

**A Helicopter can tow any types of vehicles:**
- The vehicle should not be locked
- The vehicle should not be already be towed or towing another vehicle
- The vehicle you are trying to tow should have nobody onboard

### How does it work?

While in the driver seat of your vehicle, look at the vehicle you want to tow. If all the conditions listed above are correct, you will get the option to **"Tow"** the vehicle with `[F]` (you will see the prompt on the bottom left corner of your screen).

To Untow the vehicle, the action will also be with `[F]` and you will maybe need to use scrollwheel to see the action.

---

## Vehicle Cover

Showcase video soon.

### How does it work?

You can cover your vehicle with a camo net, however some servers might require you to empty your vehicle inventory first (`CanCoverWithCargo`). However, depending on the configuration of the server, some vehicles might not be coverable at all if they spawned naturally or from a vehicle trader or other modded event like spawned with admin tools. "Natural" vehicles are called **"DEvehicles"** for Dynamic Event which is what DayZ uses to spawn vehicles all around the map in vanilla. If you can't cover one of these vehicles, it might be because `AllowCoveringDEVehicles` isn't enabled.

Vehicles can also be automatically covered after a defined amount of seconds. By default this feature is disabled.

```json
"EnableVehicleCovers": 1,
"AllowCoveringDEVehicles": 0,
"CanCoverWithCargo": 1,
"UseVirtualStorageForCoverCargo": 0,
"VehicleAutoCoverTimeSeconds": 0.0,
"VehicleAutoCoverRequireCamonet": 0,
"EnableAutoCoveringDEVehicles": 0,
"CFToolsHeliCoverIconName": "helicopter",
"CFToolsBoatCoverIconName": "ship",
"CFToolsCarCoverIconName": "car",
```

---

## Player Attachment

Showcase video soon.

### How does it work?

Some vehicles will still allow you to freely interact with the world around you while standing and moving on the vehicle even if this one is moving. Modders can specify in their vehicle class if this one can allow what we call **"player attachment"** but it can also be changed by the server itself as shown here:

```json
"VehiclesConfig": [
    {
        "ClassName": "ExpansionUAZCargoRoofless",
        "CanPlayerAttach": 1,
        "LockComplexity": 1.0
    },
    {
        "ClassName": "ExpansionUAZ",
        "CanPlayerAttach": 0,
        "LockComplexity": 1.0
    },
    {
        "ClassName": "ExpansionBus",
        "CanPlayerAttach": 1,
        "LockComplexity": 1.5
    }
]
```
    