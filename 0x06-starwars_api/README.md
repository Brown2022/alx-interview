<h1>Star Wars API</h1>
Your code should be semistandard compliant.

[Rules of Standard](https://standardjs.com/rules.html) + [semicolons on top](https://github.com/standard/semistandard)

[AirBnB style](https://github.com/airbnb/javascript)

<strong>Install Node 10</strong>

```
$ curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
$ sudo apt-get install -y nodejs
```
<strong>Install semi-standard</strong>

[Documentation](https://github.com/standard/semistandard)

```
$ sudo npm install semistandard --global
```
<strong>Install request module and use it</strong>

[Documentation](https://github.com/request/request)

```
$ sudo npm install request --global
$ export NODE_PATH=/usr/lib/node_modules
```
<strong>Tasks</strong>

<h3>0. Star Wars Characters</h3>

Write a script that prints all characters of a Star Wars movie:

- The first positional argument passed is the Movie ID - example: 3 = “Return of the Jedi”
- Display one character name per line in the same order as the “characters” list in the `/films/` endpoint
- You must use the [Star wars API](https://swapi-api.alx-tools.com/)
- You must use the `request` module
```
alexa@ubuntu:~/0x06$ ./0-starwars_characters.js 3
Luke Skywalker
C-3PO
R2-D2
Darth Vader
Leia Organa
Obi-Wan Kenobi
Chewbacca
Han Solo
Jabba Desilijic Tiure
Wedge Antilles
Yoda
Palpatine
Boba Fett
Lando Calrissian
Ackbar
Mon Mothma
Arvel Crynyd
Wicket Systri Warrick
Nien Nunb
Bib Fortuna
alexa@ubuntu:~/0x06$
```
