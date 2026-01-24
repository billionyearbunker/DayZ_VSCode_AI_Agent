# SocialMediaSettings

---

## Setting Parameters

### **`m_Version`**

- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

## News Feed Configuration

### **`NewsFeedTexts`**

- **Type**: Array
- **Description**: A list of short headlines in the pause menu with a title and short text for each of them

**Example:**

```json
{
    "m_Title": "My Awesome Title Feed !",
    "m_Text": "Because this is an example I can write anything. Please send help, they forgot to feed me again"
}
```

### **`NewsFeedTexts`** -> **`m_Title`**

- **Type**: String
- **Description**: The title of the feed

### **`NewsFeedTexts`** -> **`m_Text`**

- **Type**: String
- **Description**: A short description below the title of the feed

---

## Social Links Configuration

### **`NewsFeedLinks`**

- **Type**: Array
- **Description**: A list of all the social links like discord, steam, twitter, facebook and so on

**Example:**

```json
{
    "m_Label": "My Name Here",
    "m_Icon": "set:expansion_iconset image:icon_steam",
    "m_URL": "https://google.com"
}
```

### **`NewsFeedLinks`** -> **`m_Label`**

- **Type**: String
- **Description**: The name displayed next to the icon

### **`NewsFeedLinks`** -> **`m_Icon`**

- **Type**: String
- **Description**: The icon to display (edds or paa)

### **`NewsFeedLinks`** -> **`m_URL`**

- **Type**: String
- **Description**: The link to redirect the user