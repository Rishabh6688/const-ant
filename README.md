🧩 Laravel-Corex-Modules


[![Latest Version on Packagist]]

[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)

[![Scrutinizer Coverage]]

[![Total Downloads]]


| **Laravel** | **laravel-modules** |
|-------------|---------------------|
| 11.0        | ^1.0                |




`composer require const-ant/laravel-corex` This Corex module is the foundation of the modular system in this application. It provides essential functionality for module management, including module autoloading, marketplace integration, and module lifecycle management.

This package is a re-published, re-organised and maintained version of [], which isn't maintained anymore.

With one big bonus that the original package didn't have: **tests**.

🔄 Upgrade Guide

To upgrade to version V11 follow [Upgrade Guide](https://laravelmodules.com/docs/v11/upgrade) on official document.



🔁 Autoloading System

The application uses a centralized module management system where:
- Only the Corex module is registered in the main `composer.json`
- All other modules are managed through their own individual `composer.json` files
- Module autoloading is handled automatically through the Corex module

🔧 How It Works

1. **Main composer.json**
   - Contains only the Corex module in its autoload configuration
   - Example:
   ```json
   {
       "autoload": {
           "psr-4": {
               "Package\\Corex\\": "const-ant/laravel-corex/src/"
           }
       }
   }
   ```

2. **package-specific composer.json**
   - Each module has its own composer.json
   - Manages its own dependencies and autoloading
   - Example:
   ```json
   {
       "name": "Module/your-module",
       "autoload": {
           "psr-4": {
               "package\\YourModule\\": "src/"
           }
       }
   }
   ```


🛠️ Installation

To install via Composer, run:

``` bash
composer require const-ant/laravel-corex

after installation command you have to run this command also for publish migration

php artisan vendor:publish --tag=corex-module-migrations

The package will automatically register a service provider and alias.

Optionally, publish the package's configuration file by running:

```



⚙️ Module Lifecycle Commands

1.  🚀 Installing a New Module**
   ```bash

   # Create new module
   php artisan module:make ModuleName
   
   # Install module
   php artisan module:marketplace install ModuleName
   
   # Enable module
   php artisan module:enable ModuleName
   
   ```

2.  🧹 Removing a Module**
   ```bash

   # Remove module
   php artisan module:marketplace remove ModuleName
   
   # Clean up autoload
   php artisan module:autoload
   ```


✅ Best Practices

1. **Adding Dependencies**
   - Add module-specific dependencies to the module's own composer.json
   - Run `composer update` from the project root

2. **Maintaining Clean Configuration**
   - Always use `module:autoload` after removing modules
   - Keep module-specific code and dependencies within the module
   - Use the Corex module's services for cross-module functionality



🧱 Module Structure

Each module lives in its own subfolder, and follows a clean, organized directory structure. Below is an example of a generated module (e.g., Blog) inside your package:

Blog Module/
└── src/
    ├── Http/
    │   └── Controllers/
    │       └── BlogController.php
    ├── Models/
    │   └── Blog.php
    ├── Providers/
    │   ├── BlogServiceProvider.php
    │   └── RouteServiceProvider.php
    ├── config/
    │   └── config.php
    ├── database/
    │   ├── factories/
    │   ├── migrations/
    │   └── seeders/
    │       └── BlogDatabaseSeeder.php
    ├── resources/
    │   ├── assets/
    │   │   ├── js/
    │   │   └── sass/
    │   └── views/
    │       ├── layouts/
    │       └── index.blade.php
    ├── routes/
    │   ├── web.php
    │   └── api.php
    ├── composer.json
    ├── module.json
    ├── package.json
    └── vite.config.js


🤝 Contributing

When contributing to the module system:
1. Ensure all new modules follow the established structure
2. Use the Corex module's services for module management
3. Document any changes to the module system
4. Test module installation and removal processes 


📚 Documentation

You'll find installation instructions and full documentation on [https://laravelmodules.com/](https://laravelmodules.com/docs).

🎬 Demo

You can see a demo using Laravel Breeze at (github).

This is a complete application using Auth, Base and Profile modules.

🌐 Community

We also have a Discord community. [https://discord.gg/hkF7BRvRZK](https://discord.gg/hkF7BRvRZK) For quick help, ask questions in the appropriate channel.

## Credits

- [All Contributors](../../contributors)

🛡️ License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.













