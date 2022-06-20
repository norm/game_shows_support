Story resolution
================

To plan out the gameplay of a game with a non-linear story with plenty of
optional side-quests and no strict ordering of main quests, the `story`
script can take a collection of configuration files representing individual
story threads, order them, and present an approximate task list for
recording.


## Story thread config file

The config files looks like:

    title = 'Outlaws from the West'
    type = 'story'
    start = 'Colter'
    end = 'Colter'
    triggers = 'enter-pursued-by-a-memory'
    autobegin = true

    [[action]]
    text = "Rescue Sadie from the O'Driscolls"

    [[post_action]]
    text = "Offer Sadie the horse"
    location = 'Colter'
    after = ['enter-pursued-by-a-memory']

A new one can be minted from a useful template with the `add_story_thread`
command.

### Required elements

Each file must have:

* **title** — the title of the thread
* **type** — the type of thread (see below)
* **start**/**end** — the location where this thread begins and ends


The type of the thread can be anything, but the following have special
treatment:

* **border** — a large separation banner (eg used for marking "completed
  to here")
* **marker** — a smaller banner (eg used for marking "chapter n")
* **story** – the main storyline (only the mandatory threads)
* **location** — something that only happens *at* a location, but at any
  point in the storyline


### Describing the thread

To describe what needs to happen when playing the game, the thread can
have one or more actions, and optional post actions.

The first action should describe what the player needs to do to start the
thread. This is free text on the key `begin`, or `autobegin = true` if the
thread starts automatically without player input.

If there are more actions to take, enter each like so:

    [[action]]
    text = "Describe the action"

If there are optional actions that can be done after the thread is
complete (such as remembering to store found items, save the game, etc)
enter each like so:

    [[post_action]]
    text = "Change into Banuk Chieftain outfit"

Each action can have an optional `location` key to indicate it must be done in
a location different from `start`; similarly each post_action can indicate a
location different from `end`.

Each action and post_action can also chain the story, as described below.


### Chaining the story

Whilst some threads can be done in any order, sometimes one will lead to
another, or open up more threads to be done later.

If this thread automatically leads into the next, indicate this with:

    triggers = 'thread-name'

If completing this thread opens up other threads, indicate this with:

    unlocks = [
        'side-quest',
        'end-the-game',
    ]

If this thread must be completed before a certain point in the story (eg it
can be done at any time, but after a given thread it will disappear as an
option), indicate this with:

    finish_before = [
        'the-third-act',
    ]

And lastly, where multiple threads could be completed in any order, but you
want to exercise an editorial ordering:

    before = [
        'boss-fight',
    ]
    after = [
        'get-big-weapon',
    ]


### Required file

The file `story.toml` is required in your `story` directory. A default file
would be:

    title = 'START THE GAME'
    type = 'border'
    start = 'start'
    end = '...'
    triggers = 'story/...'
    autobegin = true

    reminders = []
    completed_threads = []
    completed_nodes = []
    abandoned_threads = []
    abandoned_nodes = []

You can edit the title, locations, triggers, actions, etc as you see fit, but
it should contain all of the required elements of a thread, **and** the five
keys `reminders`, `completed_threads`, `completed_nodes`, `abandoned_threads`,
and `abandoned_nodes`. As the game footage is recorded, it is useful to record
the threads that are completed/abandoned in here so the player can see where
they are up to.
