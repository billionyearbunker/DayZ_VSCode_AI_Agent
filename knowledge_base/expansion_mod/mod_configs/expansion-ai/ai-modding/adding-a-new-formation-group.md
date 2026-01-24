# Adding a New Formation Group

---

## Code Implementation

**File Location**: `YourMod/Scripts/4_World`

```cpp
class eAIFormationL: eAIFormation
{
	override vector GetPosition(int member_no)
	{
		int offset = Math.Floor((member_no + 1) / 2);
		float scaled_offset = 2 * offset * GetScale();
		if (member_no % 2 == 0) return Vector(scaled_offset, 0, 0); // Horizontal Line
		return Vector(0, 0, scaled_offset); // Vertical Line
	}
};
```

In this example we are drawing a L shape formation.
