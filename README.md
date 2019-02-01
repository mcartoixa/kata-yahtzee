# Yahtzee Kata

## Introduction
Yahtzee is a [dice game](https://en.wikipedia.org/wiki/Yahtzee). We will implement the rules of the game step by step.

Inspirations:
* http://codingdojo.org/kata/Yahtzee/

## Step 1
The game is played with 5 dice. Each roll of the dice must be attributed to a category that allows to compute a score:

| Category   | Score                              | Example          |
|------------|------------------------------------|------------------|
| **Aces**   | The sum of dice with the number 1  | `11356` scores 2 |
| **Twos**   | The sum of dice with the number 2  | `13222` scores 6 |
| **Thirds** | The sum of dice with the number 3  | `53331` scores 9 |
| **Fours**  | The sum of dice with the number 4  | `41234` scores 8 |
| **Fives**  | The sum of dice with the number 5  | `55555` scores 25 |
| **Sixes**  | The sum of dice with the number 6  | `65432` scores 6 |

If no dice corresponds to the attributed category the resulting score is 0.

The goal of this step is to create a library that can compute the score of a given roll of the dice.

## Step 2
The goal of this step is to create a simple application (e.g. a console) that allows a single player to play a single game of Yahtzee:
* a random roll of the dice is displayed by the application.
* the user is asked to attribute a category to each roll. The selected category must not have been attributed before.
* a score is computed for this roll and added to the overall score of the game.
* start over until all categories have been used.

## Step 3
The previous categories (cf. Step 1) being called *Upper section* categories, the goal of this step is to implement *Lower section* categories:

| Category            | Constraint                                                                                | Score               | Example           |
|---------------------|-------------------------------------------------------------------------------------------|---------------------|-------------------|
| **Three Of A Kind** | At least 3 dice are the same                                                              | The sum of all dice | `44412` scores 15 |
| **Four Of A Kind**  | At least 4 dice are the same                                                              | The sum of all dice | `33133` scores 13 |
| **Full House**      | 3 dice are the same and the 2 remaining are also the same, but different from the 3 first | 25                  | `52552` scores 25 |
| **Small Straight**  | 4 sequential dice                                                                         | 30                  | `13456` scores 30 |
| **Large Straight**  | 5 sequential dice                                                                         | 40                  | `12345` scores 40 |
| **Yahtzee**         | The 5 dice are the same                                                                   | 50                  | `22222` scores 50 |
| **Chance**          | Any combination                                                                           | The sum of all dice | `16431` scores 15 |

If the roll does not fulfill the constraints of the attributed category the resulting score is 0.

## Step 4
Bonuses can be gained throughout the game:
* if the player scores 63 points or more in the Upper section categories, a bonus of 35 is added to the overall score.
* if the player throws a Yahtzee when the Yahtzee category has already been attributed with a score of 50, a bonus of 100 is added to the overall score. The player still has to attribute a category to the roll.
  * if the Upper section categories have all been filled, the *Full House*, *Small Straight* and *Full Straight* categories can be selected (provided they have not been attributed before) and get their full score even though the roll does not fulfill the constraints of this category (*Joker rule*).

The goal of this step is to implement the bonuses and the Joker rule.

## Step 5
The goal of this step is to give the ability to the player to throw the dice 3 times in each round:
* the first throw involves the 5 dice.
* the second and third throws are optional and can involve any of the five dice.

## Step 6
The goal of this step is to play against the computer.