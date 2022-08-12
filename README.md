# Generic Save System for Unity Engine
Tired of writing your own save system from scratch every time you start a project ? You're in the right place, this is a project i've made to be maintainted accross different projects, it's a performatic, secure and easy solution.
  
## How to install
### Package Manager (recommended)
* 1 - Open the package manager (Window > Package Manager).  
* 2 - Click on the plus icon and "Add package from git URL...".  
* 3 - Enter https://github.com/GabrielBigardi/Generic-Save-System.git and click "Add".  
* 4 - Wait until the package manager finishes installing the package and recompiling.  
   
### Lazy way
* 1 - Download this repository as ZIP or by cloning it.
* 2 - Drag it into your "Assets/Plugins" folder.
  
## Why to use
### No need to write it again over and over among different projects
* Usually, every time you start a new project and it has a save system, you need to make it unique for the project, but you can use this save system for any project.
### Performance
* When developing a save system, a lot of programmers uses expensive methods like GameObject.Find, FindObjectOfType, GetComponent... I don't.
### Ease-of-use and security
* You can literally use this on any serializable class without having to modify it.
* It has a save/load event, so you can stop using singletons/static classes over and over, causing code-spaghetti.
* Most save-systems let people easily edit your save-files, but this uses a secret key and AES encryption/decryption to secure your save files from being edited.
  
## Where can i find further documentation about (codes and other things)?
That's as easy as [clicking here](DOCUMENTATION.md)
  
## How do i contribute to this project?
[Click here](CONTRIBUTING.md)
  
## Contact
**Discord**: *Gabriel Bigardi#2292*  
**Twitter**: *@BigardiGabriel*  
**Email**: *gabrielbigardi@hotmail.com*  
  
## References
[Vicot](https://github.com/vicot) for the 1.1.0 suggestions and helping the project.
