# BUGLOG

Name: Angelo Kelly

## Bug #1
Header guard typo causes compile failure
File: [include/character.h (line 1)]
Line 1 checks CHARACTER_H, but line 2 defines CHARACTER_H_. Because the names do not match, 
Character can be included twice and the compiler reports:
error: redefinition of 'class Character'

Fix: match the names.

## Bug #2
Potion function changes a copy, not the real hero
File: [src/main.cpp (line 12)]
drinkPotion(Character hero) passes the hero by value. HP and potion count change only 
inside the copied object, so drinking a potion does not actually heal the player or reduce 
potions.

Fix idea: pass by reference: Character& hero.

## Bug #3
Potion can heal above max HP
File: [src/main.cpp (line 17)]
hero.hp += 10; does not check hero.maxHp, but according to the design, potions should never heal above max HP.

Fix idea: cap HP at maxHp after healing.

## Bug #4 
Game runs 4 battles instead of exactly 3
File: [src/main.cpp (line 33)]
The loop is:
for (int i = 0; i <= 3; i++)
The loop will run 4 time, for it includes 3, which is 4 battles instead of the 
intended 3 battles..
Fix idea: use i < 3.

## Bug #5
Battle loop condition can hang / continue after someone dies
File: [src/main.cpp (line 38)]
The loop uses:
while (hero.isAlive() || monster.isAlive())
This keeps going as long as either one is alive, which goes against the intended design
of ending the battle whenever one of the combatants reaches 0 HP.
Fix idea: use && instead of ||.

## Bug #6
Monster HP and attack are swapped
File: [src/monster.cpp (line 12)]
Constructor order is name, hp, attack, defense, but the code passes:
Character(names[pick], atks[pick], hps[pick], defs[pick])
So monsters get tiny HP values like 5, 6, 7 and huge attack values like 15, 18, 22.

Fix idea: pass hps[pick] before atks[pick].
