The goal of termgrasp is to teach working in a terminal including understanding of key unix concepts, usage of common utilities and shell scripting. Terminal is hard, so teaching process must resemble that of Duolingo - slow, "bite-sized" and with a lot of repetition. The idea is to smoothen the learning curve as much as possible, so that you could start with zero knowledge and very gradually come to pretty advanced knowledge and skills without resorting to other sources. Text explanations should be kept to absolute minimum (this is what man pages are for). Instead, like Duolingo, when introducing concepts, commands, etc simple intuitive tasks should be used: fill in the blanks, connect pairs, complete the command, etc. See task types. At the same time, the point of termgrasp is to teach real practical working in the terminal instead of doing knowledge quizzes, so terminal session must be always available (except when it must be deliberately unavailable) in order to work out the solution for a task experimentally. See usage of terminal.

The program should feel familiar to Duolingo users.

# level structure

The unit of interaction with the program is one lesson. It may be short, but it must not be long. The attention span of children is not long. The lesson should be easily consumed in one go without making pauses. Also, making pauses may lead to Android killing a terminal app (where our program runs) to free memory, which results in lost progress. So a lesson of 15-25 min is fine.

A lesson consists of tasks belonging to one topic. One lesson is typically not enough to cover a topic. Also it's probably a good idea that a topic extends over a couple of days, so that a user returns to it after some rest instead of consuming in one go and jumping to the next (although for motivated users it's fine). There must not be many lessons in a topic - it must not feel endless. So 3-7 lessons, like in duolingo, is fine. Those 3-7 lessons form a level. If a topic needs more lessons than that, those lessons form new levels of that same topic. E.g. levels describing sed could be: sed, sed2, sed3, etc. Lessons are named around commands or concepts/activities whichever suits best.

Thus our content hierarchy is level-lesson-task. A number of tasks 15-25 min worth of work form a lesson. 3-7 lessons covering some topic form a level. If a topic is big enough, it has multiple levels as needed to cover it.

Like in duolingo, inside one lesson tasks progress from simpler to harder. Also levels of one topic progress from simpler to harder (if appropriate).

## duolingo

Duolingo does typical lessons of 13-15 tasks. If all tasks are completed without error, 2 extra tasks of higher complexity are done, otherwise failed tasks are repeated. 3-7 lessons form a level. Last lesson of the level is for reviewing the mistakes and/or reinforcing the material with harder tasks. It is shorter and may be skipped.

A topic takes 3 levels of progressing complexity. The hardest tasks of the 1st level are among normal tasks of the 2nd. Level 1 is for introducing new words with pictures.

2 topics of 3 levels each are grouped into a unit along with extra levels (3 stories, 1 personalized practice and final review) giving typically 11 levels per unit. Topic levels are intertwined somewhat: t1-easy t1-medium t2-easy t1-hard t2-medium t2-hard. Units are just containers for levels and have no names, numbered sequentially.

# task types

The code is read and written. So there must be tasks that test the understanding of existing code (reading) and that create new code to solve a problem (writing). Reading code is harder, b/c apart from syntax/command knowledge there is a need to "decompile" a problem being solved by author, whereas when writing code that problem is known.

Instead of passively introducing new words by just stating their translations, duolingo makes it into a task: find a translation by picture, by means of exclusion of already known words or just look up the translation yourself by hovering onto the new word. This same approach should be used for new commands, concepts whenever possible. E.g. instead of just passively stating that "ls" command lists directory contents, a simple choice question may be asked that explains the mnemonics of "ls" name:

ls command lists information on files and directories
After which word "ls" is named?

1. list
2. last
3. lost

Overall, task types can be:

- Guess words behind command name mnemonics (e.g. "change owner" for chown) - this is instead of passively stating the command name and purpose. Probably for lesson opening tasks.

- Choose param value from a list of variants. E.g. choose delimiter for "cut" to extract extension. Or choose between "-l", "-a", etc for ls to list details.

- Enter param value directly. The harder variant of previous type.

- Build a complete command from available pieces similar to how sentences in duolingo are created. This way user doesn't have to remember command params.

- Enter command directly from scratch. Can use terminal to work out the command though.

- Enter command directly from scratch without terminal. Probably appropriate to memorize often used params for single commands (not pipelines, those should be debugged in terminal).

- Choose the intent of the command or some part of it from a list of variants. This is code reading.

- Choose the output of the command from a list variants. No terminal.

- Enter the output of the command directly. No terminal.

- Fix the command.

# usage of terminal

Though terminal usage is crucial, it is not mandatory (except deliberately terminal tasks). If a user knows the solution, they may enter it without resorting to terminal. Terminal is a means to experiment and to work out the solution.

During the solution of one task terminal session may be entered unlimited number of times. Every time it is entered, it is re-inited, so that any side effects made during previous attempts are reset.

In the solution dialog, shell command history from the last terminal session (if available), must serve as a source of possible solutions to choose from (if applicable) in addition to direct solution entry.
