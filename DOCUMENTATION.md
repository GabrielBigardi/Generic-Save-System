## How to use
* 1 - Add the namespace to your code: "using GBD.SaveSystem;"  
* 2 - Create your save data class/classes (it can be anything as long as it's serializable).  
* 3 - Save your game by using SaveSystem.SaveGame<T>("OutputFileName") and load it by using SaveSystem.LoadGame<T>("InputFileName") or SaveSystem.LoadGame("InputFileName", out T serializableObject).  
  
## Functions
```cs
// Save data by giving a Save-File name and a serializable class
public static bool SaveGame<T>(string saveName, T serializableObject)

// Load data by giving a Save-File name
public static bool LoadGame<T>(string loadName)

// Load data by giving a Save-FileName and a out variable with the type of your serializable class
public static bool LoadGame<T>(string loadName, out T serializableObject)
```  
  
## Events
```cs
// Event called when the data is successfully saved
public static event Action GameDataSaved;

// Event called when the data is successfully loaded
public static event Action<string> GameDataLoaded;
```  
  
### Example usage
```cs
// EXAMPLE - Save Data
public class Inventory
{
	int someItemID;
	
	public Inventory(int someItemID)
	{
		this.someItemID = someItemID;
	}
}

// EXAMPLE - Saving/Loading
public class PlayerInventoryHandler : MonoBehaviour
{
	private void Start()
	{
		SaveSystem.LoadGame<Inventory>("Inventory");
	}
	
	private void OnApplicationQuit()
	{
		SaveSystem.SaveGame("Inventory", new Inventory(1337));
	}
}

// EXAMPLE - Events Subscriptions
public class UIInventoryHandler : MonoBehaviour
{
	public void OnEnable => SaveSystem.GameDataLoaded += OnGameDataLoaded;
	public void OnDisable => SaveSystem.GameDataLoaded -= OnGameDataLoaded;
	
	public void OnGameDataLoaded(string loadedJson)
	{
		var loadedData = JsonUtility.FromJson<Inventory>(loadedJson);
		PlayerInventory = loadedData.PlayerInventory;
	}
}
```  
