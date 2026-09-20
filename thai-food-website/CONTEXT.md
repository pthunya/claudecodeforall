# Thai Food Recommendation Site

A single-page site that lets a visitor browse Thai dishes, get a random suggestion, and keep a personal shortlist.

## Language

**Dish**:
A single Thai food item shown on the page — has a name, a Category, a short description, and an icon.
_Avoid_: "เมนู" used alone (ambiguous — Thai speakers use it for both a single item and the whole list), "อาหาร" alone (too generic).

**Category**:
The classification a Dish belongs to (e.g. ผัด, แกง, ต้ม, ยำ, ของหวาน). Used to group Dishes and to filter the grid.

**Random Pick**:
A single Dish chosen uniformly at random from the full set of Dishes, generated fresh every time the "สุ่มอาหารไทยวันนี้" button is pressed.
_Avoid_: "อาหารวันนี้" taken literally — despite the label, the pick is not locked to the calendar date and is not restricted by the active Category filter; it always draws from every Dish.

**Favorite**:
A Dish the visitor has marked to keep. Toggled from the heart control on any Dish card (grid or Random Pick result) and persisted in the browser's local storage, independent of Category filtering.
