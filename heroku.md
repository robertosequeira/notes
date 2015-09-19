# Heroku CLI

| Command       | Desciption |
| :----------:  | ---------- |
| `heroku login`                                        | Login
| `heroku create app-name`                              | Create a new app
| `heroku git:remote -a rails-sandbox-app`              | Link a local repo to a existing heroku app
| `heroku run rake --trace db:migrate` <br> `heroku run rake db:migrate`     | Migrate
| `heroku run rake db:seed`                             | Seed
| `heroku run console` <br> `heroku run rails c`        | Rails console at the app server
| `heroku maintenance:on` <br> `heroku maintenance:off` | Enable/disable maintenance mode
| `heroku logs --tail`                                  | Logs
| `heroku config:set SECRET=somesecret`                 | Set env variable
