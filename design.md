The goal of termgrasp is to teach working in a terminal including understanding of key unix concepts, usage of common utilities and shell scripting. Terminal is hard, so teaching process must resemble that of Duolingo - slow, "bite-sized" and with a lot of repetition. The idea is to smoothen the learning curve as much as possible, so that you could start with zero knowledge and very gradually come to pretty advanced knowledge and skills without resorting to other sources. Text explanations should be kept to absolute minimum (this is what man pages are for). Instead, like Duolingo, when introducing concepts, commands, etc simple intuitive tasks should be used: fill in the blanks, connect pairs, complete the command, etc. See task types. At the same time, the point of termgrasp is to teach real practical working in the terminal instead of doing knowledge quizzes, so terminal session must be always available in order to work out the solution for a task experimentally. See usage of terminal.

The program should feel familiar to Duolingo users.

# level structure

The unit of interaction with the program is one lesson. It may be short, but it must not be long. The attention span of children is not long. The lesson should be easily consumed in one go without making pauses. Also, making pauses may lead to Android killing a terminal app (where our program runs) to free memory, which results in lost progress. So a lesson of 15-25 min is fine.

A lesson consists of tasks belonging to one topic. One lesson is typically not enough to cover some topic.

Duolingo does typical lessons of 13-17 tasks.

# task types

The code is read and written. So there must be tasks that test the understanding of existing code (reading) and that create new code to solve a problem (writing). Reading code is harder, b/c apart from syntax/command knowledge there is a need to "decompile" a problem being solved by author, whereas when writing code that problem is known.

Instead of passively introducing new words by just stating their translations, duolingo makes it into a task: find a translation by picture, by means of exclusion of already known words or just look up the translation yourself by hovering onto the new word. This same approach should be used for new commands, concepts whenever possible. E.g. instead of just passively stating that "ls" command lists directory contents, a simple choice question may be asked that explains the mnemonics of "ls" name:

ls command lists information on files and directories
After which word "ls" is named?

1. list
2. last
3. lost

# usage of terminal

Though terminal usage is crucial, it is not mandatory (except deliberately terminal tasks). If a user knows the solution, they may enter it without resorting to terminal. Terminal is a means to experiment and to work out the solution.

During the solution of one task terminal session may be entered unlimited number of times. Every time it is entered, it is re-inited, so that any side effects made during previous attempts are reset.

In the solution dialog, shell command history from the last terminal session (if available), must serve as a source of possible solutions to choose from (if applicable) in addition to direct solution entry.
