---
layout: env
title: IceHockey
grid:
   - Action Space: Discrete(18)
   - Observation Shape: (210, 160, 3)
   - Observation High: 255
   - Observation Low: 0
   - Import: <code>gym.make("ALE/IceHockey-v5")</code>
---

### Description
Your goal is to score as many points as possible in a standard game of Ice Hockey over a 3-minute time period. The ball is usually called "the puck".
There are 32 shot angles ranging from the extreme left to the extreme right. The angles can only aim towards the opponent's goal.
Just as in real hockey, you can pass the puck by shooting it off the sides of the rink. This can be really key when you're in position to score a goal.
 Detailed documentation can be found on [the AtariAge page](https://atariage.com/manual_html_page.php?SoftwareLabelID=241)

### Actions
By default, all actions that can be performed on an Atari 2600 are available in this environment.
Even if you use v0 or v4 or specify `full_action_space=False` during initialization, all actions 
will be available in the default flavor.


### Observations
By default, the environment returns the RGB image that is displayed to human players as an observation. However, it is
possible to observe
- The 128 Bytes of RAM of the console
- A grayscale image

instead. The respective observation spaces are
- `Box([0 ... 0], [255 ... 255], (128,), uint8)`
- `Box([[0 ... 0]
 ...
 [0  ... 0]], [[255 ... 255]
 ...
 [255  ... 255]], (250, 160), uint8)
`

respectively. [The general article on Atari environments](https://brosa.ca/blog/ale-release-v0.7) outlines different ways to instantiate corresponding environments
via `gym.make`.


### Rewards
You score points by shooting the puck into your opponent's goal. Your opponent scores in the same manner.
There are no limits to how many points you can get per game, other than the time limit of 3-minute games.
For a more detailed documentation, consult [the AtariAge page](https://atariage.com/manual_html_page.php?SoftwareLabelID=241).

### Arguments

```
env = gym.make("ALE/IceHockey-v5")
```

The various ways to configure the environment are described in detail in the article on Atari environments.
It is possible to specify various flavors of the environment via the keyword arguments `difficulty` and `mode`. 
A flavor is a combination of a game mode and a difficulty setting.

|      Environment | Valid Modes                                                                                                                                                                         | Valid Difficulties | Default Mode |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|--------------|
|        IceHockey | `[0, 2]`                                                                                                                                                                            |      `[0, ..., 3]` | `0`          |

You may use the suffix "-ram" to switch to the RAM observation space. In v0 and v4, the suffixes "Deterministic" and "NoFrameskip" 
are available. These are no longer supported in v5. In order to obtain equivalent behavior, pass keyword arguments to `gym.make` as outlined in 
the general article on Atari environments.
The versions v0 and v4 are not contained in the "ALE" namespace. I.e. they are instantiated via `gym.make("Icehockey-v0")`.

### Version History
A thorough discussion of the intricate differences between the versions and configurations can be found in the
general article on Atari environments. 

* v5: Stickiness was added back and stochastic frameskipping was removed. The entire action space is used by default. The environments are now in the "ALE" namespace.
* v4: Stickiness of actions was removed
* v0: Initial versions release (1.0.0)
