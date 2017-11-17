# ICalendar Bundle

## Installation

### Manual Installation
Add this to your composer.json
```json
"require": {
    "six-paths/icalendar-bundle": "dev-master"
}
```

### Automated Installation
composer require six-paths/icalendar-bundle@dev-master

Activate the bundle in `app/AppKernel.php`

```php
$bundles = array(
    // ...
    new Sixpaths\ICalendarBundle\SixpathsICalendarBundle(),
);
```

## Usage

It is advised to inject this service in to listeners or other services that may need to consume it rather than using $this->get('...'); instead of a controller; however, that option is still available

As part of a controller
```php
class SomeController extends Controller
{
    public function someAction(/* ...$arguments */)
    {
        $icalendar = $this->get('sixpaths.icalendar');
    }
}
```

As part of a console command
```php
class SomeCommand extends ContainerAwareCommand
{
    protected function configure()
    {
        $this->setName('some:command')
            ->setDescription('A command');
    }

    protected function execute(InterInterface $input, OutputInterface $output)
    {
        $container = $this->getContainer();
        $icalendar = $container->get('sixpaths.icalendar');
    }
}
```
