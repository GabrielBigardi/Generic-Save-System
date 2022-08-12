## How to use
* 1 - Add the namespace to your code: "using GBD.SaveSystem;"  
* 2 - Create your save data class/classes (it can be anything as long as it's serializable).  
* 3 - Save your game by using SaveSystem.SaveGame<T>("OutputFileName") and load it by using SaveSystem.LoadGame<T>("InputFileName") or SaveSystem.LoadGame("InputFileName", out T serializableObject).  
* 4 - For security purposes you need to change the secret key in the save system, it supports any 128-bit hex key, you can generate one at https://www.allkeysgenerator.com/Random/Security-Encryption-Key-Generator.aspx  
  
## Functions
```cs
// Save data by giving a Save-File name and a serializable class
public static bool SaveGame<T>(string saveName, T serializableObject);

// Load data by giving a Save-File name
public static bool LoadGame<T>(string loadName);

// Load data by giving a Save-FileName and a out variable with the type of your serializable class
public static bool LoadGame<T>(string loadName, out T serializableObject);
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
// EXAMPLE - Custom Secrets Static Class
public static class GameSecrets
{
	public const string SAVE_SECRET_KEY = "b14ca5898a4e4133bbce2ea2315a1916";
}

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
		SaveSystem.LoadGame<Inventory>("Inventory", GameSecrets.SAVE_SECRET_KEY);
	}
	
	private void OnApplicationQuit()
	{
		SaveSystem.SaveGame("Inventory", new Inventory(1337), GameSecrets.SAVE_SECRET_KEY);
	}
}

// EXAMPLE - Events Subscriptions
public class UIInventoryHandler : MonoBehaviour
{
	public void OnEnable => SaveSystem.GameDataLoaded += OnGameDataLoaded;
	public void OnDisable => SaveSystem.GameDataLoaded -= OnGameDataLoaded;
	
	public void OnGameDataLoaded(object loadedObject)
	{
		var loadedData = loadedObject as Inventory;
		PlayerInventory = loadedData.PlayerInventory;
	}
}
```  
