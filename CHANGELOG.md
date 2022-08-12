# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2022-08-12
### Changed
- Now you can specify a secret key on the save/load functions (or leave the default one, but it isn't recommended).
- Removed duplicated codes by using a getter on one of the load functions.
- The deserialized object is no a json string anymore, it's a object that needs to be casted, as you already had the need to know the deserialized type.
  
## [1.0.0] - 2022-08-11
### Added
- Initial commit of the project.
