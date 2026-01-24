# Notification Scheduler Settings

---

## Setting Parameters

### **`m_Version`**

- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

### **`Enabled`**

- **Type**: Boolean
- **Description**: Enable/Disable notification scheduler system

### **`UTC`**

- **Type**: Boolean
- **Description**: Enable/Disable if the system should use UTC (Coordinated Universal Time). For further info on what UTC is and if you should enable or disable this option visit [TimeAndDate.com](https://www.timeanddate.com/time/aboututc.html)

### **`UseMissionTime`**

- **Type**: Boolean
- **Description**: Enable/Disable whether the system should use the mission uptime for each notification or server time. Disable this option if you want to use the server local time instead

---

## Notifications Configuration

### **`Notifications`**

- **Type**: Array
- **Description**: Each entry should contain a time (mission uptime or server local time), a title and text, and an icon path (or expansion icon name)

**Example:**

```json
"Notifications": [
    {
        "Hour": 22,
        "Minute": 0,
        "Second": 0,
        "Title": "Notification Schedule Test 1",
        "Text": "Lorem ipsum dolor sit amet",
        "Icon": "Info",
        "Color": ""
    },
    {
        "Hour": 22,
        "Minute": 1,
        "Second": 0,
        "Title": "Notification Schedule Test 2",
        "Text": "Lorem ipsum dolor sit amet",
        "Icon": "Info",
        "Color": ""
    }
]
```
    