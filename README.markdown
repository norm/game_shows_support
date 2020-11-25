Game Shows support
==================

Support scripts and files that I use when creating content for my
[Game Shows][gs] YouTube channel.

[gs]: https://www.youtube.com/channel/UCI0KNfM-b2vXKPY4QwJ0_oQ


## Running commands

The [generate](generate) script is used to run scripts, and takes care
of providing the right environment variables, including setting up `$PATH`
to find the companion scripts kept in [bin/](bin).

    # add a task to Things
    ./generate add_to_things "I am an example task"

    # add all of the tasks required for Chapter 33 of the current "show"
    ./generate chapter_tasks 33


## Keeping track with [Things][th]

The scripts [`add_to_things`](bin/add_to_things), 
[`chapter_tasks`](bin/chapter_tasks),
and [`route_tasks`](bin/route_tasks)
help me keep track of where I am in any given video chapter in 
[Cultured Code's Things][th].

I use "Route: " tasks when planning out the route to take through the game,
then organise them roughly into chapters, and each chapter has a
[number of tasks](Horizon%20Zero%20Dawn/things.tasks)
such as "capture footage",
"add map", "retime captions", etc.

[th]: http://culturedcode.com/things/

![Example chapter in Things](chapter.png)
