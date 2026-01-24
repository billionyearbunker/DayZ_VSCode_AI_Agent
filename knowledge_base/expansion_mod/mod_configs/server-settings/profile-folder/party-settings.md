# PartySettings

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`EnableParties`**
- **Type**: Bool
- **Values**:
  - `0` = Players won't be able to create parties
  - `1` = Allow players to create parties. (Open the book with B and go to the party tab)

---

### **`MaxMembersInParty`**
- **Type**: Integer
- **Description**: Maximum of players allowed in a single party. If <= 0, unlimited party size

---

### **`UseWholeMapForInviteList`**
- **Type**: Bool
- **Values**:
  - `0` = You can only invite players near you
  - `1` = You can invite everyone from anywhere regardless of the distance

---

### **`ShowPartyMember3DMarkers`**
- **Type**: Bool
- **Values**:
  - `0` = You can't see any markers above the head of your teammates (sims style)
  - `1` = You can see a marker above the head of your teammates who joined your party

---

### **`ShowDistanceUnderPartyMembersMarkers`**
- **Type**: Bool
- **Requirements**: Require `ShowPartyMember3DMarkers` to be set to 1
- **Values**:
  - `0` = Players won't be able to see the distance under the PartyMember marker above the head of your teammates
  - `1` = The distance will be displayed under each PartyMember markers

---

### **`ShowNameOnPartyMembersMarkers`**
- **Type**: Bool
- **Requirements**: Require `ShowPartyMember3DMarkers` to be set to 1
- **Values**:
  - `0` = Players won't be able to see the name under the PartyMember marker above the head of your teammates
  - `1` = The name will be displayed under each PartyMember markers

---

### **`EnableQuickMarker`**
- **Type**: Bool
- **Values**:
  - `0` = You can't create quickmarkers
  - `1` = You can create a quickmarker (only works if you are in a party). Use the H key to create a quickmarker, to remove the quickmarker use the H or the delete key when looking at the quickmarker. You can also look at the sky and tap H

---

### **`ShowDistanceUnderQuickMarkers`**
- **Type**: Bool
- **Requirements**: Require `EnableQuickMarker` to be set to 1
- **Values**:
  - `0` = Players won't be able to see the distance under the quickmarker
  - `1` = The distance will be displayed under each quickmarkers

---

### **`ShowNameOnQuickMarkers`**
- **Type**: Bool
- **Requirements**: Require `EnableQuickMarker` to be set to 1
- **Values**:
  - `0` = Players won't be able to see the name of the owner of the quickmarker
  - `1` = The name of the owner of the quickmarker will be displayed underneath

---

### **`CanCreatePartyMarkers`**
- **Type**: Bool
- **Values**:
  - `0` = You can't create party markers
  - `1` = You can create party markers. This markers will be visible by everyone in your group (party)

---

### **`ShowPartyMemberHUD`**
- **Type**: Bool
- **Values**:
  - `0` = This feature will be disabled
  - `1` = Member of the same party can see the status of their teammates (health condition)
