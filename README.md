# Knowledge Base Challenge
Starter project for building a simple Knowledge Base app with Django


### Get Dev Environment Running with Docker

* Make sure your computer has Docker installed. See these links for your OS: [Windows](https://docs.docker.com/docker-for-windows/install/), [Mac](https://docs.docker.com/docker-for-mac/install/), [Linux](https://docs.docker.com/v17.12/install/)
* From github [fork](https://help.github.com/articles/fork-a-repo/) this repo: https://github.com/lightningkite/knowledge-base-challenge.git
* From the terminal clone your fork:

```
git clone https://github.com/<your-github-user>/knowledge-base-challenge.git
cd knowledge-base-challenge
```

* Now inside the root of the project lets get the django project running:

```
docker-compose build
docker-compose up
```

* After running those commands if you open your browser to localhost:8000 you should see the django welcome screen. This only shows for a blank django project. Once you define url routes and views this page won't show.

* You can leave that running now and open another tab in your terminal and run:

```
docker-compose run web /bin/bash
python knowledge_base/manage.py migrate
```

* This sets up your database to work with django. At this point you are ready for the challenge


### The Project

* Simply put you will be building a knowledge base site that allows for users to post something useful with a title and set any number of tags for the post to help with searching. The main page of the site will show recent posts and allow you to search through all posts based off of post title, post body, and any of the post tags.


### Models

* The models that will be needed are: `User` (feel free to use the default django auth user), `Post`, and `Tag`
* The `User` model fields: `username` and `password` and whatever else is provided by the default django auth user
* The `Post` model fields: `author` (ForeignKey to your user), `title` (CharField), `body` (TextField), `tags` (ManyToMany relationship with `Tag` model) `created` (DatetimeField that is a timestamp of when the model was created)
* The `Tag` fields: `name` (unique CharField). We don't want tags getting duplicated since all posts should be using the same tags.


### Views

* Login view for existing users
* Signup view for new users
* Logout view for logged in users
* Post list view - Will be a list of posts. Will only show a post title and tags. Each item in the list will link to the corresponding post detail view. Should be the landing page of the site. Will also have a text input for searching the system. If there has been no search made the list will just show the 10 most recent posts in the system. Once there has been a search the list view will show all results of the search.
* Post detail view - Shows everything there is to know about a post. The title, description, when it was created, the tags, and the author. Should provide some sort of navigation to go back to the post list view. If a logged in post author is on this view there should be an edit link that takes the user to the form to edit the post.
* Post edit view - The form that lets only post authors edit an existing post.
* Post create view - Should be basically the same form as the Post edit view except the form will be empty. Any logged in user can edit this view.
* Navigation - Some way to from the list view to post detail views and to the signup/login/logout


### Summary

* There are a lot of different directions you can go with this project. Should give you some basic exposure to the Django framework. The [Django documentation](https://docs.djangoproject.com/en/2.1/) explains clearly how to use models, set up views, work with forms and do everything you will need for this project. If you find any third party libraries that you want to bring into the project feel free. Just add the requirement to the requirements.txt file and run `docker-compose build` again and re-run `docker-compose up`. Commit often and push your code to your fork on github and when you are done send us the link to your fork. Have fun!
