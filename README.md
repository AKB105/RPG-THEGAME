# RPG-THEGAME 🐉
Your team started a game and then suddenly vanished into the dungeon!
The code is riddled with **12 bugs**. Your quest: find and fix every one of them in order to save your team!

## What the game is SUPPOSED to do

1. Ask for your hero's name: names with spaces (e.g. `Sir Lancelot`) must work.
2. Create the hero: Default values should be **30 HP, 7 attack, 2 defense, 3 potions**.
3. The hero fights **exactly three** randomly chosen monsters (Goblin, Skeleton, or Orc), one after another. The three monsters should be able to differ from each other.
4. Each round you choose **(1) Attack** or **(2) Potion**. If the monster survives your turn, it strikes back.
5. Damage dealt is `attacker's ATK + rand() % 3 - defender's DEF`, but every hit deals **at least 1 damage**.
6. A potion heals 10 HP, **never above max HP**, and only works if you have potions left.
7. A battle ends the moment **either** combatant's HP drops to 0 or below.
8. After the dungeon, the game reports how many monsters you defeated.

If the game you're running doesn't do the above; that's a bug. Go hunt it.

## Building

```
g++ -Wall -o rpg main.cpp character.cpp monster.cpp
```

Always compile with `-Wall`. The compiler is your first party member read every
error **and every warning** from top to bottom!

## The Rules of the Hunt

- There are **12 bugs**: some stop the game from building, some crash it or hang
  it, and some just make the game behave in ways that are ... playably weird.
  You may have to *play the game* to notice them.
- Fix the bugs! Do **not** rewrite the program from scratch. Each fix should be
  small and targeted.
- Keep a `BUGLOG.md` in your repo. For every bug, record:
  1. **Symptom** — what you observed (error message, weird gameplay, hang).
  2. **Cause** — the actual mistake in the code (file + line).
  3. **Fix** — what you changed and why it works.

## Hints (use sparingly)

- You cannot see the runtime bugs until the program builds. Fix compiler errors
  first, then linker errors, then play.
- If input ever starts "skipping" or looping strangely, think carefully about
  what `cin >> ` actually reads ... and what it leaves behind.

Good luck, adventurer. 🗡️

# Worth 20% Of The Grade!

