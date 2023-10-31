# introduction

The goal of termgrasp is to teach working in a terminal including understanding of key unix concepts, usage of common utilities and shell scripting. Terminal is hard, so teaching process must resemble that of Duolingo - slow, "bite-sized" and with a lot of repetition. The idea is to smoothen the learning curve as much as possible, so that you could start with zero knowledge and very gradually come to pretty advanced knowledge and skills without resorting to other sources.

Text explanations should be kept to absolute minimum. This is what man pages and other resources are for. Also because kids may be perfectly capable of remembering commands and their parameters and thus solving terminal tasks, but have difficulties with reading texts or figuring out what they're asked for. Instead, like Duolingo, when introducing concepts, commands, etc simple intuitive tasks should be used: fill in the blanks, connect pairs, complete the command, etc. See task types.

At the same time, the point of termgrasp is to teach real practical working in the terminal instead of doing knowledge quizzes, so terminal session must be always available (except when it is unavailable on purpose) in order to work out the solution for a task experimentally. See usage of terminal.

The program should feel more or less familiar to Duolingo users.

# level structure

The unit of interaction with the program is a lesson comprised of tasks. Lesson may be short, but it must not be long. The attention span of children is not long. The lesson should be easily consumed in one go without making pauses. Also, making pauses may lead to Android killing a terminal app (where our program runs) to free memory, which results in lost progress. So a lesson of 15-25 min is fine.

A lesson consists of tasks belonging to one topic. One lesson is typically not enough to cover a topic. Also it's probably a good idea that a topic extends over a couple of days, so that a user returns to it after some rest instead of consuming in one go and jumping to the next (although for motivated users it's fine). There must not be many lessons in a topic - it must not feel endless. So 3-7 lessons, like in duolingo, is fine. Those 3-7 lessons form a level. If a topic needs more lessons than that, those lessons form new levels of that same topic. E.g. levels describing sed could be: sed, sed2, sed3, etc. Lessons are named around commands or concepts/activities whichever suits best.

Summing up, our content hierarchy is level-lesson-task. A number of tasks 15-25 min worth of work form a lesson. 3-7 lessons covering some topic form a level. If a topic is big enough, it has multiple levels as needed to cover it.

## how duolingo does it

Duolingo does typical lessons of 15 tasks. If 13 tasks are completed without error, 2 last tasks will have higher complexity, otherwise failed tasks are repeated after task 15 _endlessly_ until every task is answered correctly.

3-7 lessons form a level. Lessons don't have names, levels do. Last lesson of the level is for reviewing the mistakes and reinforcing the material with harder tasks. It is typically shorter.

A topic takes 3 levels of progressing complexity. The hardest task type of level 1 - make a sentence in target lang from blocks - is among normal tasks of level 2. The hardest task type of level 2 - write a sentence in target lang from scratch - is _not_ among normal tasks of level 3. Instead a simpler variant is normally used in level 3 - write a part of sentence from scratch. The hardest task type - write a sentence from scratch - is normally used only in the unit final (see below) test, that acts as a gateway into the next unit. Thus duolingo increases complexity slower than linearly and only requires absolute knowledge once - at the very end of the unit.

Level 1 is for introducing new words and phrases. There are no new words/phrases in levels 2-3 - they are for reinforcing material from level 1 only.

2 topics of 3 levels each are grouped into a unit along with extra levels (3 stories, 1 personalized practice and final review) giving typically 11 levels per unit. Topic levels are intertwined somewhat: t1-easy t1-medium t2-easy t1-hard t2-medium t2-hard. Units are just containers for levels and have no names, numbered sequentially.

## modular scheme proposal

Duolingo scheme of typical 5-6 lessons per level, where level 1 introduces words/concepts and levels 2-3 reinforce, seems not very flexible, b/c how to decide how many new concepts to put into those 5-6 lessons of level1? Natural language is more flexible - you can possibly get as many words/phrases as you wish. But how much would you get from, say, wc? Should it occupy its own level or be mixed with other util? If mixed, then which util and what if you later try to separate? If one later wants to refresh wc, why should he refresh the other util? It's harder to name such a level devoted to a couple of (even related) things.

Also finishing duolingo levels on some topic doesn't end up in proficiency. Even in level 3 you mostly assemble sentences from blocks.

So the proposed solution is to divide knowledge into small modules that deal with one concept only and do the necessary drilling end-to-end: from introducing the concept to gaining proficiency on the terminal writing full commands from scratch without any hint. E.g. "pacman -S" module makes sure you understand the underlying repository concept and can freely use the command to install packages. You don't mix "pacman -S" with other pacman ops in one module.

This has advantages:

- When adding a module, you have to think less, how it fits the overall course - it doesn't mix with other modules. Removing is also easier.

- Naming is easier, b/c module is devoted to one thing only. As a consequence, searching for revising the material is also easier.

- Modules may be really short if the content is short and it's fine. You don't have to bring other stuff just to provide enough lessons/levels. The only thing needed is to reach the goal of proficiency.

This is a bit akin to unix philosophy, where utils do one thing only.

Modules may probably have other modules as dependencies. E.g. you need to know grep/regex to fully use "pacman -Ss". Should "pacman -S" module depend on "basic sudo" module or introduce basic sudo usage itself?

# level content

## package manager

Teach distro-specific (ask for distro and/or detect current distro) ways to search, install, remove packages, update the system, view package contents, etc.

On desktop/laptop user's first needs will probably include installing new programs rather than e.g. working with the file system. Especially kids, which will want to play games, draw, etc and may long not use pc for any other purpose. So starting with levels on package management basics may be a good idea.

On the other hand, on mobile (android, ios), knowing how to use package manager may be of less importance. Still, user may be using termgrasp on mobile to learn how to work on desktop, so learning particular package manager may be important.

### pacman

First level(s) shall introduce only the absolutely crucial stuff needed by Arch beginner. Those are commands to search and install packages (-S, -Ss), remove packages (-Rs), query what's already installed (-Qs), update the whole system (-Suy). Also the notion of repository and superuser (sudo).

Later levels introduce commands that demand more advanced knowledge: view package info (-Si, -Qi), list package contents (-Ql), find owner package of the file path (-Qo), download package databases (-Sy), install package from tarball (-U).

## git

git may be needed not just for programming. E.g. you have a driver package (say, nvidia drivers) from AUR that must be rebuilt every time you update the system. You need git clone for initial install and then git pull for every update.

# level navigation

Termgrasp, like duolingo, is supposed to be game-like. When you start, all levels except level 1 are locked. So you start from level 1 and work your way through lessons sequentially to unlock level 2, then level 3, etc.

You can try jumping forward to locked levels, but for that to succeed you must pass the test that checks your knowledge of all the levels you're skipping including current. When the test is passed, all the skipped levels and lessons are marked as finished.

Note, a course update may possibly add new (locked) level in-between levels already finished (i.e. below current course position), so you could jump "backward" in course. Still, the scheme applies: to succeed in jumping first prove by passing the test that you've mastered all the intermediate levels (incl. current) that the program would lead you through if you were to do it the normal sequential way.

Similar to duolingo, finished levels may be done again. When choosing a finished level the last (hardest) lesson is started.

Also see "determining current level" in level updates.

# level updates

Level content is not fixed, it's supposed to be constantly improving. This inevitably leads to updating levels while the user is in the middle of the course, probably doing those same levels that are being updated.

Possible updates are: add level, remove level, edit level, move level (change position in course). Also it's important to what part of the course the update is happening: already finished levels (past levels), unfinished current level, not yet started levels (future levels).

## principles of update

Following principles should be obeyed whenever possible when updating level content:

- user's progress (levels/lessons passed, xp, achievements, etc) should be kept

- current level should be allowed to finish

## determining current level

Current level is searched as follows, whichever is found first:

- Unfinished level (i.e. with at least one finished lesson). There may be at most one such level. This way unfinished level is allowed to be finished first before moving on (see principles above).

- The lowest in course, that is not started (i.e. with no finished lessons). This behavior ensures that new content, even when added/moved to past part of the course, is always addressed by user.

## tracking progress

Since levels may be easily moved and removed, level progress is stored as a list of (un)finished levels and not some index number. A level is represented by its unique name. At most one level may have attached to it the number of lessons finished - this is unfinished current level. See determining current level.

This way for each level in the course:

- if there's a matching level in progress storage without lessons number attached - level is considered finished

- if there's a matching level in progress storage with attached lessons number - this is unfinished current level

- if there's no matching level in progress storage - level is considered not started, i.e. future level

## updates to future levels

Adding, removing or editing future levels may be freely done.

When moving some future level below current level in the course order, i.e. into past levels, this is akin to adding new level to past levels, which see below.

## updates to past levels

When a new level is added to course such that its position is below current level (i.e. among levels already finished), it will become the new current level, but only after current level is allowed to finish (see determining current level).

When finished level is removed, the xp, achievements and other progress (if applicable) from the level are kept, but the level itself disappears from the course.

When a level is finished, the content associated with it is considered grasped by the user. So when some past level is reworked, even cardinally and with adding more lessons, still it's considered finished, progress retained, must not be done again.

When past level is moved into future levels, it keeps its finished status and must be skipped over when reached.

## updates to unfinished current level

Current level can't be added.

When unfinished current level is removed, progress is kept (see principles). The new current level will be the lowest level not yet started (see determining current level).

When current level is edited, progress (incl. lessons already finished) is kept. When lessons are removed and new number of lessons is less than or equal to that already finished, the last lesson must be marked not finished. I.e. current level can't be finished by means of an update, that decreased number of lessons.

When current level is moved to future or past levels, its progress is kept and it's continued as usual.

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

