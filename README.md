# ps4-games-api
PS4 games collection API made using Python Flask,
what this API does is just demonstrate CRUD (Create,Read,Update,Delete) functionality, this API is actually just small part of a bigger application that i will develop later.

### List APIs

| URI                          | HTTP METHOD | Action                 |
|------------------------------|-------------|------------------------|
| ps4-games/api/v1/list        |     GET     | show list of data      |
| ps4-games/api/v1/detail/[id] |     GET     | show single data by id |
| ps4-games/api/v1/create      |     POST    | create/add new data    |
| ps4-games/api/v1/update/[id] |     PUT     | update data by id      |
| ps4-games/api/v1/delete/[id] |    DELETE   | delete data by id      |

sample JSON input (for create and update API):
```
{
  "title":"Drive Club",
  "genre":"Racing",
  "developer":"Evolution Studios",
  "publisher":"Sony Computer Entertainment",
  "release_date":"2014-10-07",
  "exclusive":"yes",
  "image_link":"https://upload.wikimedia.org/wikipedia/en/thumb/6/6f/Driveclub_box_art.jpg/250px-Driveclub_box_art.jpg"
}
```





### Database table
this API is using MySQL database with one table called ps4_games for storing game data
such as title, genre, game developer, publisher, etc.
```
CREATE TABLE `ps4_games` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `title` varchar(500) NOT NULL,
  `genre` varchar(255) DEFAULT NULL,
  `exclusive` char(3) DEFAULT NULL,
  `developer` varchar(255) DEFAULT NULL,
  `publisher` varchar(255) DEFAULT NULL,
  `image_link` varchar(255) DEFAULT NULL,
  `release_date` date DEFAULT NULL,
  `created_by` int(11) DEFAULT NULL,
  `updated_by` int(11) DEFAULT NULL,
  `created_at` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_title` (`id`,`title`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

### Requirements
```
pip install Flask
pip install flask-mysqldb
pip install flask flask-cors

for ubuntu:
sudo apt-get install python-dev
sudo apt-get install libmysqlclient-dev
```

### Configuration
Copy the `config.py.sample` into `config.py` and edit the content based on your configuration.

```
APP_CONFIG = {
    "app_debug_mode" : True,
    "mysql_host" : "localhost",
    "mysql_user" : "root",
    "mysql_password" : "",
    "mysql_db" : "ps4_game_collection",
    "mysql_cursorclass" : "DictCursor"
}
```


### How to run
```
python app.py
```
