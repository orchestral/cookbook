## Downloading via Composer

Firstly, run the following command to download Orchestra Platform 3 using Composer:

    $ composer create-project orchestra/platform patio "3.1.x" --prefer-dist

This composer command would create a new project for you on `patio` folder using the latest development build, `--prefer-dist` is another option that you can use to indicate that you want to download a distributed version instead of cloning the repository, otherwise use `--prefer-source`.

Once composer finish installing the dependencies you can navigate the the project directory.

    $ cd patio

To test that everything is working, you may use the Serve command:

    $ php artisan serve
    Laravel development server started on http://localhost:8000/

Now open <http://localhost:8000> and you should see our splash screen.

![Orchestra Platform Splash Screen](splash-screen.png)
