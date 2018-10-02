# Script

Simple to write script in PHP.

## Installing

```bash
$ composer create-project jimchen/script script --prefer-dist
```

## Usage

#### Create a command file

```bash
$ php artisan make:command HelloCommand  // Create a file named `HelloCommand` in `app/Commands`
```

#### Write your command file

In `app/Commands/HelloCommand.php`
```php
<?php

namespace App\Commands;

use Illuminate\Console\Command;

class HelloCommand extends Command
{
    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'test';

    /**
     * The console command description.
     *
     * @var string
     */
    protected $description = 'A test command';

    /**
     * Create a new command instance.
     *
     * @return void
     */
    public function __construct()
    {
        parent::__construct();
    }

    /**
     * Execute the console command.
     *
     * @return mixed
     */
    public function handle()
    {
        //
        $this->info('Hello World!');
    }
}
```

#### Configuration

In `app/Kernel.php`
```php
<?php

namespace App;

use App\Foundation\Console\Kernel as ConsoleKernel;

class Kernel extends ConsoleKernel
{
    /**
     * The Artisan commands provided by your application.
     *
     * @var array
     */
    protected $commands = [
        \App\Commands\HelloCommand::class,
    ];
    
    ...
}
```

## License

MIT