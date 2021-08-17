# Absolute Theme

[Absolute theme](https://github.com/swissup/theme-frontend-absolute) - is simple and free 
Magento 2 theme with pagebuilder support.

## Installation

Installation requires Marketplace module. It’s our module that provides easy to
use installer.

```bash
composer require swissup/module-marketplace && bin/magento setup:upgrade
bin/magento marketplace:package:require swissup/absolute-metapackage
bin/magento marketplace:package:install swissup/absolute-metapackage
```

That's all. Navigate to you store to check your new theme:

![Homepage Screenshot](https://raw.githubusercontent.com/swissup/theme-frontend-absolute/master/media/preview.png)
