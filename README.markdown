Game Shows support
==================

Support scripts and files that I use when creating content for my
[Game Shows][gs] YouTube channel.

[gs]: https://www.youtube.com/channel/UCI0KNfM-b2vXKPY4QwJ0_oQ


## Running commands

The [generate](generate) script is used to run scripts, and takes care
of providing the right environment variables, including setting up `$PATH`
to find the companion scripts kept in [bin/](bin).


## Preparing footage

The raw capture footage is in `mkv` format and the audio level is quite quiet,
so for easier editing in Davinci Resolve it is converted to `mp4` and the
volume boosted. A text file is also created for each new file to keep notes of
what footage is where, and a Things task to track if I've filled it out.

    # copy the files from the machine that does the video capturing
    ./generate raw

    # prep the footage used in editing from the raw video
    ./generate footage


## Generating audio from text

In order to make large swathes of text appearing on screen more accessible
and palatable, it is provided as audio narration too. This is generated
using Amazon Polly.

    # make mp3s from new or updated text files
    ./generate audio


## Editing/reviewing annotations

Annotations can be easily edited/reviewed later using the
[`annotations`](bin/annotations) script. It works from most-recent to
least-recent, and can match only empty files or ones matching a specific
pattern (typically the date).

    # edit only empty files
    ./generate annotations empty

    # edit only a specific day
    ./generate annotations 2020-11-20


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

    # add a task to Things
    ./generate add_to_things "I am an example task"

    # add all of the tasks required for Chapter 33 of the current "show"
    ./generate chapter_tasks 33

![Example chapter in Things](chapter.png)

[th]: http://culturedcode.com/things/
