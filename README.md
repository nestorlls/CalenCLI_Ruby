# Project: CalenCLI

### Start the program (happy)

Run `calencli.rb` and the program should show the welcome message, the weekly
agenda, the options footer, and prompt the user to input an action.

```bash
$ ruby calencli.rb
-----------------------------Welcome to CalenCLI------------------------------

Mon Nov 15                Ruby Basics 1 (1)
            12:00 - 13:30 English Course (2)

Tue Nov 16                Ruby Basics 2 (3)
            12:45 - 13:00 Soft Skill Session - Resilience (4)

Wed Nov 17                Ruby Methods (5)
            12:00 - 13:30 English Course (6)

Thu Nov 18                Extended Project (7)
            09:00 - 13:30 Summary Workshop (8)

Fri Nov 19                Extended Project (9)
            12:00 - 13:30 English for Engineers (10)

Sat Nov 20  10:00 - 11:00 Breakfast with my family (11)
            15:00 - 20:00 Hackaton (12)

Sun Nov 21                No events

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: 
```

### Create an event (happy)

```bash
-----------------------------Welcome to CalenCLI------------------------------

Mon Nov 15                Ruby Basics 1 (1)
            12:00 - 13:30 English Course (2)

Tue Nov 16                Ruby Basics 2 (3)
            12:45 - 13:00 Soft Skill Session - Resilience (4)

Wed Nov 17                Ruby Methods (5)
            12:00 - 13:30 English Course (6)

Thu Nov 18                Extended Project (7)
            09:00 - 13:30 Summary Workshop (8)

Fri Nov 19                Extended Project (9)
            12:00 - 13:30 English for Engineers (10)

Sat Nov 20  10:00 - 11:00 Breakfast with my family (11)
            15:00 - 20:00 Hackaton (12)

Sun Nov 21                No events

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: create
date: 2021-11-20
title: Push extended project!
calendar: tech
start_end: 23:00 23:30
notes: Don't forget to push our final work to the main branch
guests: Diego, Codeka
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action:
```

### Error messages

When the user doesn't input a date:

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: create
date: 
Type a valid date: YYYY-MM-DD
date: 2021-11-20
```

When the user doesn't input a title:

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: create
date: 2021-11-20
title: 
Cannot be blank
title: My new event
```

When the user inputs an invalid start_end:

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: create
date: 2021-11-20
title: My new event
calendar: optional-calendar
start_end: 11:00
Format: 'HH:MM HH:MM' or leave it empty
start_end: 11:00 09:00
Cannot end before start
start_end: 11:00 15:00
```

### List events

If the user inputs the word `list`

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: list
-----------------------------Welcome to CalenCLI------------------------------

Mon Nov 15                Ruby Basics 1 (1)
            12:00 - 13:30 English Course (2)

Tue Nov 16                Ruby Basics 2 (3)
            12:45 - 13:00 Soft Skill Session - Resilience (4)

Wed Nov 17                Ruby Methods (5)
            12:00 - 13:30 English Course (6)

Thu Nov 18                Extended Project (7)
            09:00 - 13:30 Summary Workshop (8)

Fri Nov 19                Extended Project (9)
            12:00 - 13:30 English for Engineers (10)

Sat Nov 20  10:00 - 11:00 Breakfast with my family (11)
            15:00 - 20:00 Hackaton (12)
            23:00 - 23:30 Push extended project! (15)

Sun Nov 21                No events

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: 
```

### Show an event

If the user type `show` the program should ask for an `Event ID`. If the user
inputs a valid ID, then the program will show all the details of that event (in
the same format as they were introduced). Which are the events IDs? Each event
has a number displayed between `(id)`. That's the ID. For example, the ID for
"English for Engineers" is 10.

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: list
-----------------------------Welcome to CalenCLI------------------------------

Mon Nov 15                Ruby Basics 1 (1)
            12:00 - 13:30 English Course (2)

Tue Nov 16                Ruby Basics 2 (3)
            12:45 - 13:00 Soft Skill Session - Resilience (4)

Wed Nov 17                Ruby Methods (5)
            12:00 - 13:30 English Course (6)

Thu Nov 18                Extended Project (7)
            09:00 - 13:30 Summary Workshop (8)

Fri Nov 19                Extended Project (9)
            12:00 - 13:30 English for Engineers (10)

Sat Nov 20  10:00 - 11:00 Breakfast with my family (11)
            15:00 - 20:00 Hackaton (12)
            23:00 - 23:30 Push extended project! (15)

Sun Nov 21                No events

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: show
Event ID: 15
date: 2021-11-20
title: Push extended project!
calendar: tech
start_end: 23:00 23:30
notes: Don't forget to push our final work to the main branch
guests: Diego, Codeka
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action:
```

### Update an event (and show again to verify)

Similar to `show`, when the user types `update` the program asks for the Event
ID. And then, similar to `create` the program prompt for each piece of the event
information. Yes, the user needs to respond again to every property. If
something is left blank, that's the value the event will take (for the optional
properties at least). The same validations described on `create` apply here.

After updating an event, it won't be a bad idea to show the event again to
verify if the changes were applied.

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: update
Event ID: 15
date: 2021-11-20
title: Push extended project updated!
calendar: tech
start_end: 23:00 23:30
notes: Dont forget to push our final work to the main branch
guests: Diego, Codeka, Teddy
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: show
Event ID: 15
date: 2021-11-20
title: Push extended project updated!
calendar: tech
start_end: 23:00-23:30
notes: Don't forget to push our final work to the main branch
guests: Diego, Codeka, Teddy
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: 
```

### Delete an event (and list again to verify)

Similar to `show` and `update`, when the user types `delete` the program asks
for the Event ID. And then, it performs the deletion. If everything goes well,
the actions footer is displayed (as always) and the program prompts the user for
the next action. You can list the events to verify if the deleted event shows up
(it shouldn't).

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: delete
Event ID: 15
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit
action: list
-----------------------------Welcome to CalenCLI------------------------------

Mon Nov 15                Ruby Basics 1 (1)
            12:00 - 13:30 English Course B1 (2)

Tue Nov 16                Ruby Basics 2 (3)
            12:45 - 13:00 Soft Skill Session - Resilience (4)

Wed Nov 17                Ruby Methods (5)
            12:00 - 13:30 English Course (6)

Thu Nov 18                Extended Project (7)
            09:00 - 13:30 Summary Workshop (8)

Fri Nov 19                Extended Project (9)
            12:00 - 13:30 English for Engineers (10)

Sat Nov 20  10:00 - 11:00 Breakfast with my family (11)
            15:00 - 20:00 Hackaton (12)

Sun Nov 21                No events

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action:
```

### Go to next week and the previous week

If the user types `next` the program should display the agenda for the next week. The same but in reverse when the user inputs `prev`.

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: next
-----------------------------------CalenCLI-----------------------------------

Mon Nov 22                No events

Tue Nov 23                No eventsg

Wed Nov 23                No events

Thu Nov 24                Extended Project (13)

Fri Nov 25                Extended Project (14)

Sat Nov 26                No events

Sun Nov 27                No events

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: prev
-----------------------------Welcome to CalenCLI------------------------------

Mon Nov 15                Ruby Basics 1 (1)
            12:00 - 13:30 English Course B1 (2)

Tue Nov 16                Ruby Basics 2 (3)
            12:45 - 13:00 Soft Skill Session - Resilience (4)

Wed Nov 17                Ruby Methods (5)
            12:00 - 13:30 English Course (6)

Thu Nov 18                Extended Project (7)
            09:00 - 13:30 Summary Workshop (8)

Fri Nov 19                Extended Project (9)
            12:00 - 13:30 English for Engineers (10)

Sat Nov 20  10:00 - 11:00 Breakfast with my family (11)
            15:00 - 20:00 Hackaton (12)

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action:
```

If the user keeps entering `next` he sooner or later will see an empty calendar:

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: next
-----------------------------------CalenCLI-----------------------------------

Mon Nov 29                No events

Tue Nov 30                No events

Wed Nov 01                No events

Thu Nov 02                No events

Fri Nov 03                No events

Sat Nov 04                No events

Sun Nov 05                No events

------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: 
```

## Exit the program

When the user type `exit`, the program should end.

```bash
------------------------------------------------------------------------------
list | create | show | update | delete | next | prev | exit

action: exit
Thanks for using calenCLI
$ 
```
