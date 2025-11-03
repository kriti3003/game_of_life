This is a simple demonstration application used in the [Jenkins: The Definitive Guide](http://wakaleo.com/books/jenkins-the-definitive-guide) book.

## Building the project

The project is a simple multi-module Maven project. To build the whole project, just run `mvn install` from the root directory.

## Running the game

The application is a very simple online version of [Conway's 'game of life'](http://en.wikipedia.org/wiki/Conway's_Game_of_Life). To see what the game does, run `mvn install` as described above, then go to the gameoflife-web directory and run `mvn jetty:run`. The application will be running on http://localhost:9090.


