# Extbaseinstantiable mixin for TYPO3
This package provides a mixin (read: trait) that lets you bestow the power of self-instantiation (using TYPO3
conventional mechanisms) to your classes. Add this mixin to any class to make it instantiable using the Extbase
`ObjectManager` with ease.

## Interface
Once you've mixed the trait into your class, you can call `MyClass::get()` to get an instance of the class.

## Detailed usage

```php
/**
 * Class MyClass
 */
class MyClass
{
    use \Castiron\ExtbaseInstantiable\Traits\ExtbaseInstantiable;

    /**
     * Some public interface
     */
    public function execute()
    {
        // yadda yadda whatever
    }
}

/**
 * Instantiate (with ObjectManager) and call a public method.
 */
MyClass::get()->execute();
```

## Why do I want this?
A couple of reasons why this is handy:
- It makes instantiating your class in TYPO3-world easy-peasy (vs `GeneralUtility::makeInstance` or `ObjectManager::get` called directly)
- It uses `ObjectManager::get` under the hood, so automatic dependency injection works if you use annotations like `@inject`

## FAQ

#### Will it also respect marker interfaces like `SingletonInterface`?
Yes! It's using normal TYPO3 object instantiation under the hood, so all that weirdo magic will work.

## Installation
```
composer require castiron/typo3-extbaseinstantiable
```
